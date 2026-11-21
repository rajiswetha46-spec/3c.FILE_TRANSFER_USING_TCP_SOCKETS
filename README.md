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
# SERVER.PY
```

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

s.bind(('localhost', 5055))
s.listen(1)

print("Waiting for client...")

c, addr = s.accept()
print("Client connected:", addr)

try:
    with open("sample.txt", "rb") as f:
        while True:
            data = f.read(1024)

            if not data:
                break

            c.sendall(data)

    print("File sent successfully")

finally:
    c.close()
    s.close()

```

# CLIENT.PY
```

import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect(('localhost', 5055))

try:
    with open("received.txt", "wb") as f:
        while True:
            data = s.recv(1024)

            if not data:
                break

            f.write(data)

    print("File received successfully")

finally:
    s.close()
```

## OUPUT
<img width="1493" height="957" alt="Screenshot 2026-11-21 210814" src="https://github.com/user-attachments/assets/faea76bb-0089-42fd-9ee2-4cbdff62de23" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
