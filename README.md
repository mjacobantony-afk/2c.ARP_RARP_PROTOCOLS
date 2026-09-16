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
### SERVER
```py
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
### CLIENT
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP

<img width="1837" height="102" alt="image" src="https://github.com/user-attachments/assets/3ed63ef6-be99-4cee-ab2e-df8220e580eb" />

<img width="1838" height="168" alt="image" src="https://github.com/user-attachments/assets/6714458c-8169-45e1-99e5-58792a6a4b04" />

## PROGRAM - RARP
### SERVER
```py
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

### CLIENT
```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP

<img width="1837" height="84" alt="image" src="https://github.com/user-attachments/assets/ff395e0e-0ced-4e15-b0b3-c06e70cfa1fe" />

<img width="1839" height="168" alt="image" src="https://github.com/user-attachments/assets/ca85e3bf-b539-45bf-8550-c7f46da86743" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
