# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
DEVELOPED BY:JWALAMUKHI S 
REGISTER:212223040079

CLIENT
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_fil', 'wb') as f:
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

SERVER
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
    filename='hello.txt'
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

## OUTPUT
CLIENT
![client](https://github.com/user-attachments/assets/a336d54d-4434-4614-b585-3aa40b9f0d2a)


SERVER
![server](https://github.com/user-attachments/assets/d7b59732-6cbc-44e7-86a9-4688b02c4527)


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
