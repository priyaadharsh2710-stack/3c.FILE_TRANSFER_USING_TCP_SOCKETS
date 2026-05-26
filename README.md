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
Client
```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file.txt', 'wb') as f:

    while True:
        print('Receiving data...')

        data = s.recv(1024)

        if not data:
            break

        print('Data =', data)

        f.write(data)

print('Successfully received the file')

s.close()

print('Connection closed')
```
Server:
```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.bind((host, port))

s.listen(5)

print("Server listening...")

while True:

    conn, addr = s.accept()

    print('Connected by', addr)

    data = conn.recv(1024)

    print('Server received:', repr(data))

    filename = 'mytext.txt'

    f = open(filename, 'rb')

    l = f.read(1024)

    while l:
        conn.send(l)

        print('Sent', repr(l))

        l = f.read(1024)

    f.close()

    print('Done sending')

    conn.close()

    break

s.close()
```
## OUPUT
<img width="867" height="225" alt="Screenshot 2026-05-26 163602" src="https://github.com/user-attachments/assets/84094346-2ea5-4bf2-b67c-30a7491927db" />

<img width="895" height="245" alt="image" src="https://github.com/user-attachments/assets/c7b0118c-eee8-44cf-8e51-36a640fd5b8c" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6a78532f-8815-4c46-ad3f-310614d5d9d4" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
