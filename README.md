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
##Server (ARP Server)

import socket

arp_table = { "192.168.1.1": "AA:BB:CC:DD:EE:01", "192.168.1.2": "AA:BB:CC:DD:EE:02", "192.168.1.3": "AA:BB:CC:DD:EE:03" }

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM) server.bind(("localhost", 5000)) server.listen(5)

print("ARP Server is running...")

while True: client, addr = server.accept() print("Connected with", addr)

ip = client.recv(1024).decode()
print("Requested IP:", ip)

mac = arp_table.get(ip, "MAC Address not found")
client.send(mac.encode())

client.close()
<img width="1854" height="255" alt="image" src="https://github.com/user-attachments/assets/5e7bdb33-930f-479a-9ab6-393c344f8a0b" />

##Client (ARP Client)

import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("localhost", 5000))

ip = input("Enter IP Address: ")

client.send(ip.encode())

mac = client.recv(1024).decode()

print("MAC Address:", mac)

client.close()
<img width="1054" height="270" alt="image" src="https://github.com/user-attachments/assets/9d0609c6-5e50-4999-8338-b46825c0c71b" />

## PROGRAM - RARP
##Server (RARP Server)

import socket

rarp_table = { "AA:BB:CC:DD:EE:01": "192.168.1.1", "AA:BB:CC:DD:EE:02": "192.168.1.2", "AA:BB:CC:DD:EE:03": "192.168.1.3" }

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM) server.bind(("localhost", 6000)) server.listen(5)

print("RARP Server is running...")

while True: client, addr = server.accept() print("Connected with", addr)

mac = client.recv(1024).decode()
print("Requested MAC:", mac)

ip = rarp_table.get(mac, "IP Address not found")
client.send(ip.encode())

client.close()
<img width="1610" height="321" alt="image" src="https://github.com/user-attachments/assets/66c03b23-406f-4a79-b11d-f50501c20d81" />
##Client (RARP Client)

import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("localhost", 6000))

mac = input("Enter MAC Address: ")

client.send(mac.encode())

ip = client.recv(1024).decode()

print("IP Address:", ip)

client.close()
<img width="1657" height="283" alt="image" src="https://github.com/user-attachments/assets/d45776d7-2cfe-4b5b-ad20-48ce895ad924" />
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
