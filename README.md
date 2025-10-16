# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM:

To write a python program for creating File Transfer using TCP Sockets Links.

## ALGORITHM:

1. Import the necessary python modules.
3. Create a socket connection using socket module.
4. Send the message to write into the file to the client file.
5. Open the file and then send it to the client in byte format.
6. In the client side receive the file from server and then write the content into it.
## PROGRAM:

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

## mytext.txt:

```
 HI ASHIKA TR
 I know ur a good girl
 Be happy and stay stromg

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

## CLIENT:

<img width="1268" height="328" alt="image" src="https://github.com/user-attachments/assets/cfd9611d-ce29-49ee-b8cc-2d3ad35632fb" />

## SERVER:

<img width="1276" height="214" alt="image" src="https://github.com/user-attachments/assets/18034683-f235-4fc4-bc36-b2a10cfabf35" />

## RESULT:

Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
