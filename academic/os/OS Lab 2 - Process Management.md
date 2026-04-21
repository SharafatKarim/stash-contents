# Process Management - Module 2
## Process Controlling
### fork()
```cpp
#include<bits/stdc++.h>
using namespace std;

int main() {
    int pid = fork();
    if (pid == 0)
        cout << "Child process  -> " << pid << endl;
    else
        cout << "Parent process -> " << pid << endl;
}
```
### exec()
```cpp
#include <bits/stdc++.h>
int main() {
    execlp("ls", "", "-la", NULL);
    return 0;
}
```
### wait()
```cpp
#include<bits/stdc++.h>
#include<sys/wait.h>

using namespace std;

int main() {
    int pid = fork();
    if (pid == 0) {
        sleep(5);
        cout << "Child process  -> " << pid << endl;
    } else {
        cout << "Parent process -> " << pid << endl;
        wait(NULL);
    }
}
```

## Signal Controlling

### Sigint
```cpp
#include<bits/stdc++.h>
using namespace std;

void sig_int(int sig_num) {
    cout << "Received signal, " << sig_num << endl;
    exit(sig_num);
}

int main() {
    signal(SIGINT, sig_int);
    while (true);
}
```


### Sigkill
```cpp
#include<bits/stdc++.h>
using namespace std;

int main() {
    int target_pid = 1234;
    if (kill(target_pid, SIGKILL) == 0)
        cout << "Killed " << target_pid << endl;
    else
        cout << "Not found!" << endl;
}
```

## Mini Shell

```cpp
#include<bits/stdc++.h>
#include<sys/wait.h>

using namespace std;

void sig_handle(int sig_num) {
    cout << "\nCtrl + c pressed! Exiting..." << endl;
    exit(sig_num);
}

int main() {
    signal(SIGINT, sig_handle);

    string s;
    while (true) {
        cout << "mini-shell:";
        cin >> s;
        if (s == "exit") break;

        if (fork() == 0) {
            execlp(s.c_str(), "", NULL);
            exit(1);
        } else {
            wait(NULL);
        }
    }
}
```

# Threading

## C++
```cpp

```