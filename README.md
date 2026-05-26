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
<img width="855" height="330" alt="Screenshot 2026-05-26 162133" src="https://github.com/user-attachments/assets/2c8ecf24-cc4e-413a-b928-dd05f4ae7358" />
<img width="791" height="252" alt="Screenshot 2026-05-26 162140" src="https://github.com/user-attachments/assets/22273da4-fb08-4ad6-8c43-eaaa15dd8910" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
