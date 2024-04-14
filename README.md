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
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode()) 
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
## client:
![Screenshot 2024-04-14 213211](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/151658061/559096d8-fc13-4cae-bb4b-3dba6d2ec233)

## server:
![Screenshot 2024-04-14 213224](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/151658061/21e7066e-17f8-4b24-a06b-9569341c61eb)

## PROGRAM - RARP
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
## client:
![Screenshot 2024-04-14 213237](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/151658061/5cd2257a-f2ba-44b6-b771-308b1d393fa0)

## server:
![Screenshot 2024-04-14 213249](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/151658061/0d97508d-4c65-4c76-b0c6-1a807cd33dcd)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
