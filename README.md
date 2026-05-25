# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
# client side :
```
import socket

s = socket.socket()
s.connect(("localhost", 8000))

while True:
    ip = input("Enter the website you want to ping: ")
    s.send(ip.encode())
    print(s.recv(1024).decode())
```
# server side :
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(("localhost", 8000))
s.listen(5)

print("Server started...")

c, addr = s.accept()
print("Connected to", addr)

while True:
    hostname = c.recv(1024).decode()

    if not hostname:
        break

    try:
        result = ping(hostname, verbose=False)
        c.send(str(result).encode())
    except Exception:
        c.send("Not Found".encode())
```

## OUTPUT
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/7ef05eed-bc20-4f6a-99a2-c86cab72132a" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
