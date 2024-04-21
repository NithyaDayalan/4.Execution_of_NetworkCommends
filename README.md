# 4  EXECUTION OF NETWORK COMMANDS

## AIM : 
Use of Network commands in Real Time environment.

## SOFTWARE :
Command Prompt And Network Protocol Analyzer.

## PROCEDURE : 
To do this EXPERIMENT- follows these steps:
1. In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer.
2. All commands related to Network configuration which includes how to switch to privilege mode and normal mode and how to configure router interface and how to save this configuration to flash memory or permanent memory.
<BR> 
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.

## PROGRAM :
### CLIENT :
```
import socket 
from pythonping import ping
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
while True:
    c, addr = s.accept()
    print("Connection from", addr)
    try:
        hostname = c.recv(1024).decode().strip()
        if hostname:
            try:
                response = str(ping(hostname, verbose=False))
                c.send(response.encode())
            except Exception as e:
                c.send("Ping failed: {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error:", e)
    finally:
        c.close()
```
### SERVER :
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
try:
    while True:
        ip = input("Enter the website you want to ping: ")
        s.send(ip.encode())
        response = s.recv(1024).decode()
        if response:
            print("Ping Result:", response)
        else:
            print("No response from server.")
except Exception as e:
    print("Error:", e)
finally:
    s.close()
```
### TRACECODE COMMAND :
```
from scapy.all import *
target = ["www.google.com"]
result, unans = traceroute(target,maxttl=32)
print(result,unans)
```
## OUTPUT :
### CLIENT & SERVER :
![image](https://github.com/NithyaDayalan/4.Execution_of_NetworkCommends/assets/166380061/59fafdf8-09b4-4bcf-bc9c-01699721d558)

### TRACEROUTE COMMAND :
![image](https://github.com/NithyaDayalan/4.Execution_of_NetworkCommends/assets/166380061/88de2c74-8728-486f-b3d1-b8183418f202)

## RESULT :
Thus Execution of Network commands Performed.
