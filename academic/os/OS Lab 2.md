# Process Management
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

