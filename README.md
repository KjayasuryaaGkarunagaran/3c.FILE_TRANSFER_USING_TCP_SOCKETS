# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
DEVELOPED BY: Jayasuryaa k
REGISTER NUMBER: 212222040060

## CLIENT:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
   print('receiving data...')
   data = s.recv(1024)
   print('data=%s', (data))
   if not data:
    break
   f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```

## SERVER:
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
 conn, addr = s.accept()
 data = conn.recv(1024)
 print('Server received', repr(data))
 filename='mytext.txt'
 f = open(filename,'rb')
 l = f.read(1024)
 while (l):
   conn.send(l)
   print('Sent ',repr(l))
   l = f.read(1024)
 f.close()
 print('Done sending')
 conn.send('Thank you for connecting'.encode())
 conn.close()
```
## OUPUT:

![image](https://github.com/Priya-dharshini-Raja/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/148514803/9df5e16c-4444-4f78-8f63-f5a8e9aa90ca)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
