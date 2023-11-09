# WintonC2
Yet another Command & Control (C2) server using Golang...

This would be my third time making the exact same barebones C2 but with slight improvements, this time I decided to learn Go while doing it because I was bored.

Very heavily a WIP, C agent coming soon.

![sample](https://i.imgur.com/5owJ9Cg.png)

## Compilation
The `teamserver` compiles to a single golang binary:
```bash
go build .
chmod +x teamserver
./teamserver <ip> <port> <password>
```

The `agent` has a MSVC solution file, compile the solution in `Release` mode (Windows):
```bash
gcc -Wall -std=c99 -o Wanton.exe Commands.c Main.c Utils.c -lcurl
```
_A Makefile is not provided because I am lazy_

## Change Log

#### 10/11/2023 - Winton now has an agent for Windows!
- The agent is written in C and is extremely unstable! :D, and barely functional.
- Currently only has support for `pwd`, but more commands will be added eventually.
    ![10/11/2023](https://i.imgur.com/D2nVffY.png)
#### 9/11/2023 - Beacons can now go offline!
- If the callback from the last beacon is over `Agent.Sleep + 5` seconds, the beacon will be marked as down (_but should still listening for callbacks_).
   - In its current state, the agent gets completely removed from the `AgentList[]` and `AgentCallbacks[]` if it goes offline, this will be changed in the future to allow for offline agents to still be in the list.
    ![9/11/2023](https://i.imgur.com/CZm1eGe.png)
- The change of beacon state is also reflected in the `AgentList[]` and `AgentCallbacks[]` tables
    ![9/11/2023](https://i.imgur.com/p87EHej.png)