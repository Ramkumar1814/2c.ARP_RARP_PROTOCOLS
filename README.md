# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name: RAMKUMAR S
## Regno: 212223220085
## AIM
To write a python program for simulating ARP protocols using TCP.
To write a python program for simulating RARP protocols using UDP

## ALGORITHM (ARP):
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
## ALGOROTHM(RARP):

## Client
1. Start the program
2. Using datagram sockets UDP function is established.
3. Get the MAC address to be converted into IP address.
4. Send this MAC address to server.
5. Server returns the IP address to client.
## Server
1. Start the program.
2. Server maintains the table in which IP and corresponding MAC addresses are stored.
3. Read the MAC address which is send by the client.
4. Map the IP address with its MAC address and return the IP address to client.
## PROGRAM - ARP
## client ARP:
```
import socket
s=socket.socket()
s.bind(('localhost',8880))
s.listen(5)
c,addr=s.accept()
address={"192.168.144.56":" AC:50:DE:1B:DE:65"};
while True:
  ip=c.recv(1024).decode()
  try:
  c.send(address[ip].encode())
  except KeyError:
  c.send("Not Found".encode())
```
## server ARP:
```
import socket
s=socket.socket()
s.connect(('localhost',8880))
while True:
  ip=input("Enter Logical Address:")
  s.send(ip.encode())
  print("MAC address",s.recv(1024).decode())
```
## OUPUT - ARP
client:
![Screenshot 2024-09-25 155007](https://github.com/user-attachments/assets/2f156b95-99d9-4390-899a-7575f27057d8)
Server:
![Screenshot 2024-09-25 155024](https://github.com/user-attachments/assets/f887e7b4-c3aa-4207-a9e9-ed2581ace64d)

## PROGRAM - RARP
## client RARP:
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
## server RARP:
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
Client:
![Screenshot 2024-10-01 092544](https://github.com/user-attachments/assets/63ea56b4-05ba-43f4-a747-03ae4e50b5cd)
Server:
![Screenshot 2024-10-01 092552](https://github.com/user-attachments/assets/0cee0d14-53b5-4147-9128-04e8f635b0d5)


## RESULT
Thus, the python program for simulating ARP protocols using TCP and python program for simulating RARP protocols using UDP were successfully executed.
