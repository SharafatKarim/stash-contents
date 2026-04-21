# Synchronization Problem

## Problem Set

1. A university system generates student IDs using a shared variable next_id.
When multiple admission requests are processed simultaneously, some students receive duplicate IDs. No synchronization mechanism is currently used. Implement a C++ program demonstrating this issue

2. Two processes update a shared database record.
The system designer wants a software-only solution (no hardware support) that ensures:
    • Mutual exclusion 
    • Fair turn-taking 
Implement the solution in C++

3. A file system allows multiple threads to write logs.
To prevent corruption:
    • Only one thread should write at a time 
    • Others should wait efficiently (no busy spinning) 
Implement using C++

4. A bank has implemented an ATM system where multiple users can access their accounts simultaneously. Each transaction updates a shared variable called balance.
Recently, the bank noticed that sometimes the balance becomes incorrect when multiple users withdraw or deposit money at the same time.
The system designer decides to use a low-level hardware-supported locking mechanism where:
    • A lock variable is checked and set in one atomic step 
    • Threads repeatedly check the lock until it becomes free 
Tasks
    1. Identify the synchronization technique used 
    2. Write a C++ program to solve this problem

5. A multi-core system maintains a global counter that is updated by multiple threads. The system must ensure:
    • The counter is updated only if its current value has not been changed by another thread 
    • The update must be atomic 
The system uses a hardware instruction that:
    • Compares a variable with an expected value 
    • Updates it only if they match 
Tasks
    1. Identify the synchronization method 
    2. Implement the solution in C++

6. A computer lab has a single printer shared among many students.
Rules:
    • Only one student can use the printer at a time 
    • If the printer is busy, others must wait 
    • Waiting students should not waste CPU (no busy waiting) 
The system designer creates a high-level structure where:
    • Shared variables are hidden 
    • Only predefined functions can access the resource 
    • Waiting is handled automatically 
Tasks
    1. Identify the synchronization method 
    2. Write a C++ solution

7. A factory has:
    • Producers adding items 
    • Consumers removing items 
Rules:
    • Buffer size is limited 
    • Producers must wait if full 
    • Consumers must wait if empty 
Tasks
    1. Identify synchronization tool 
    2. Implement in C++

# Sample Solutions

### Race condition

```cpp
#include <bits/stdc++.h>
using namespace std;

int shared_id = 0;

void func() {
    int id = shared_id;
    id++;
    cout << id << endl;
    shared_id = id;
}

int main() {
    thread t1(func);
    thread t2(func);

    t1.join();  
    t2.join();  
    cout << "Main thread finished. ID -> " << shared_id << endl;
    return 0;
}
```

### Software based solution
```cpp
#include <bits/stdc++.h>
using namespace std;

int shared_id = 0;

int turn = 0;
bool flag[2] = {false, false};

void func(int i) {
    flag[i] = true;
    turn = 1-i;
    while (flag[1-i] && turn == (1-i));

    int id = shared_id;
    id++;
    cout << id << endl;
    shared_id = id;

    flag[i] = false;
}

int main() {
    thread t1(func, 0);
    thread t2(func, 1);

    t1.join();  
    t2.join();  
    cout << "Main thread finished. ID -> " << shared_id << endl;
    return 0;
}
```

### Writing Logs
```cpp
#include <bits/stdc++.h>
using namespace std;

void func(int i) {
    cout << i << endl;
}

int main() {
    thread t1(func, 1);
    t1.join();  
    
    thread t2(func, 2);
    t2.join();  
    return 0;
}
```

### Mutex Lock

```cpp
#include <bits/stdc++.h>
using namespace std;

int balance = 0;
bool locker = false;

void acquire_locker() {
    while(locker);
    locker = true;
}

void release_locker() {
    locker = false;
}

void func() {
    acquire_locker();

    int local_bal = balance;
    local_bal++;
    cout << local_bal << endl;
    balance = local_bal;

    release_locker();
}

int main() {
    thread t1(func);
    thread t2(func);

    t1.join();  
    t2.join();  
    cout << "Final bal. -> " << balance << endl;

    return 0;
}
```

### Test & Set

```cpp
#include <bits/stdc++.h>
using namespace std;

int balance = 0;
// bool locker = false;
atomic<bool> locker{false};

bool test_and_set() {
    // bool temp = locker;
    // locker = true;
    // return temp;
    return locker.exchange(true);
}

void acquire_locker() {
    while(test_and_set());
}

void release_locker() {
    locker = false;
}

void func() {
    acquire_locker();

    int local_bal = balance;
    local_bal++;
    cout << local_bal << endl;
    balance = local_bal;

    release_locker();
}

int main() {
    thread t1(func);
    thread t2(func);
    
    t1.join();  
    t2.join();  
    cout << "Final bal. -> " << balance << endl;

    return 0;
}
```

### Compare & Swap
```cpp
#include <bits/stdc++.h>
using namespace std;

int balance = 0;
// bool locker = false;
atomic<bool> locker{false};

bool test_and_set() {
    // bool temp = locker;
    // locker = true;
    // return temp;
    // return locker.exchange(true);
    return locker.compare_exchange_weak(false, true);
}

void acquire_locker() {
    while(test_and_set());
}

void release_locker() {
    locker = false;
}

void func() {
    acquire_locker();

    int local_bal = balance;
    local_bal++;
    cout << local_bal << endl;
    balance = local_bal;

    release_locker();
}

int main() {
    thread t1(func);
    thread t2(func);
    
    t1.join();  
    t2.join();  
    cout << "Final bal. -> " << balance << endl;

    return 0;
}
```

### Producer Consumer
```cpp
#include<bits/stdc++.h>
using namespace std;

int BUFFER_SIZE = 5;
int buffer[5];
int counter = 0;
int in = 0, out = 0;

void producer() {
    for (int i = 0; i < 10; i++) {
        while (counter == BUFFER_SIZE); // wait until buffer is not full

        buffer[in] = i;
        in = (in + 1) % BUFFER_SIZE;
        counter++;

        cout << "Produced: " << i << endl;
    }
}

void consumer() {
    for (int i = 0; i < 10; i++) {
        while (counter == 0); // wait until buffer is not empty

        int item = buffer[out];
        out = (out + 1) % BUFFER_SIZE;
        counter--;

        cout << "Consumed: " << item << endl;
    }
}

int main() {
    thread prod(producer);
    thread cons(consumer);

    prod.join();
    cons.join();

    return 0;
}
```

### Semaphore
```cpp
#include <bits/stdc++.h>
using namespace std;

int balance = 0;
int locker = 1;

void acquire_locker() {
    while (locker <= 0);
    locker--;
}

void release_locker() {
    locker++;
}

void func() {
    acquire_locker();

    int local_bal = balance;
    local_bal++;
    cout << local_bal << endl;
    balance = local_bal;

    release_locker();
}

int main() {
    thread t1(func);
    thread t2(func);
    
    t1.join();  
    t2.join();  
    cout << "Final bal. -> " << balance << endl;

    return 0;
}
```

### Monitor
```cpp
#include <bits/stdc++.h>
using namespace std;

class DiningMonitor {
private:
    enum State { THINKING, HUNGRY, EATING };
    vector<State> state;
    vector<condition_variable> self;
    mutex m;
    int n;

public:
    DiningMonitor(int philosophers) : n(philosophers) {
        state.resize(n, THINKING);
        self.resize(n);
    }

    void pickup(int i) {
        unique_lock<mutex> lock(m);
        state[i] = HUNGRY;
        cout << "Philosopher " << i << " is HUNGRY" << endl;
        test(i);
        
        while (state[i] != EATING) {
            self[i].wait(lock);
        }
        cout << "Philosopher " << i << " is EATING" << endl;
    }

    void putdown(int i) {
        unique_lock<mutex> lock(m);
        state[i] = THINKING;
        cout << "Philosopher " << i << " is THINKING" << endl;
        
        test((i + n - 1) % n);
        test((i + 1) % n);
    }

private:
    void test(int i) {
        if (state[i] == HUNGRY &&
            state[(i + n - 1) % n] != EATING &&
            state[(i + 1) % n] != EATING) {
            state[i] = EATING;
            self[i].notify_one();
        }
    }
};

void philosopher(int id, DiningMonitor& monitor) {
    for (int i = 0; i < 3; i++) {
        monitor.pickup(id);
        this_thread::sleep_for(chrono::milliseconds(100));
        monitor.putdown(id);
        this_thread::sleep_for(chrono::milliseconds(50));
    }
}

int main() {
    DiningMonitor monitor(5);
    vector<thread> threads;

    for (int i = 0; i < 5; i++) {
        threads.emplace_back(philosopher, i, ref(monitor));
    }

    for (auto& t : threads) {
        t.join();
    }

    cout << "All philosophers finished eating" << endl;
    return 0;
}
```