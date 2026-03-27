# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
SERVER:
```
import socket 
s = socket.socket() 
s.bind(('localhost', 880)) 
s.listen(1) 
c, _ = s.accept() 
address = {"192.168.144.56": "AC:50:DE:1B:DE:65"} 
while True: 
ip = c.recv(1024).decode() 
c.send(address.get(ip, "Not Found").encode()) 
```
## OUTPUT - ARP
<img width="1009" height="207" alt="image" src="https://github.com/user-attachments/assets/02deb546-7dfe-4a0a-9a52-66dbd63a4579" />

## PROGRAM - RARP
```
import socket 
s=socket.socket();s.bind(('localhost',880));s.listen(1);c,_=s.accept() 
a={"192.168.144.56":"AC:50:DE:1B:DE:65"} 
while True: c.send(a.get(c.recv(1024).decode(),"Not Found").encode())
```
## OUPUT -RARP
<img width="1027" height="308" alt="image" src="https://github.com/user-attachments/assets/1428014c-5ebc-4117-80db-4bf643f1cb1a" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
