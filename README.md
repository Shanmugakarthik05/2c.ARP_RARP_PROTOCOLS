# 2c.SIMULATING ARP /RARP PROTOCOLS

 ## NAME:SHANMUGAKARTHIK G <br>
 ## REG.NO:212223220105
 
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
## CLIENT.PY:
~~~
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
~~~
## SERVER.PY:
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
~~~
## OUPUT - ARP
## CLIENT.PY:
![image](https://github.com/user-attachments/assets/406ed527-8a36-4e35-a550-6bb8dbab1343)

## SERVER.PY:
![image](https://github.com/user-attachments/assets/b23ee3b6-a5ae-4f59-9615-e8982b8c767e)

## PROGRAM - RARP
## CLIENT.PY:
~~~
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
~~~
## SERVER.PY:
~~~
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
~~~
## OUPUT -RARP
## CLIENT.PY:
![image](https://github.com/user-attachments/assets/8fe4b26a-5bf2-47dd-8de7-06d6746e2481)

## SERVER.PY:
![image](https://github.com/user-attachments/assets/51201c85-d35e-4e96-98c2-01e16dacc0ce)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
