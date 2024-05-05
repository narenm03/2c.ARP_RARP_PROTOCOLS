# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name:NARENDARAN.M
## REG NO:212223230134
## AIM:
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
6. 
## PROGRAM - ARP:
### CLIENT:
import socket   
s=socket.socket()    
s.bind(('localhost',8000))    
s.listen(5)    
c,addr=s.accept()    
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:    
ip=c.recv(1024).decode()    
try:    
c.send(address[ip].encode())   
except KeyError:   
c.send("Not Found".encode()) 

### SERVER:
import socket    
s = socket.socket()    
s.connect(('localhost',8000))    
while True:   
ip = input("Enter logical address: ")   
s.send(ip.encode())    
print("MAC Address",s.recv(1024).decode()) 
## OUTPUT - ARP:
### CLIENT:
![Screenshot 2024-04-09 171431](https://github.com/23004513/2c.ARP_RARP_PROTOCOLS/assets/138973069/f29e2182-0d63-40e0-b953-0e7ec5749fca)

### SERVER:
![Screenshot 2024-04-09 172010](https://github.com/23004513/2c.ARP_RARP_PROTOCOLS/assets/138973069/57768d61-b90b-4fa1-8709-ae97ecdc6e3b)

## PROGRAM - RARP:
### CLIENT:
import socket   
s = socket.socket()    
s.bind(('localhost',8000))   
s.listen(5)    
c,addr = s.accept()    
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}   
while True:   
ip = c.recv(1024).decode()   
try:    
c.send(address[ip].encode())   
except KeyError:    
c.send("Not Found".encode())

### SERVER:
import socket   
s = socket.socket()    
s.connect(('localhost',8000))   
while True:    
ip = input("Enter MAC address: ")    
s.send(ip.encode())   
print("Logical Address",s.recv(1024).decode())

## OUTPUT -RARP:

### CLIENT:
![Screenshot 2024-04-09 172725](https://github.com/23004513/2c.ARP_RARP_PROTOCOLS/assets/138973069/84b84a2b-9049-4d38-b8c4-4b518287dee3)
### SERVER:
![Screenshot 2024-04-09 173244](https://github.com/23004513/2c.ARP_RARP_PROTOCOLS/assets/138973069/1fb76e5a-b398-4253-8147-990588ced9c4)

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
