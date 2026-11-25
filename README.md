# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
## sserver
```
import socket
import threading

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('localhost', 8001))
s.listen(1)

print("Server waiting for connection...")
conn, addr = s.accept()
print("Client connected")

def receive():
    while True:
        try:
            msg = conn.recv(1024).decode()
            if not msg or msg.lower() == "exit":
                print("Client disconnected")
                break
            print("\nClient:", msg)
        except:
            break

threading.Thread(target=receive, daemon=True).start()

while True:
    msg = input("Server: ")
    conn.send(msg.encode())
    if msg.lower() == "exit":
        break

conn.close()
s.close()
```
## client
```

import socket
import threading

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('localhost', 8001))

print("Connected to server")

def receive():
    while True:
        try:
            msg = s.recv(1024).decode()
            if not msg or msg.lower() == "exit":
                print("\nServer disconnected")
                break
            print("\nServer:", msg)
        except:
            break

threading.Thread(target=receive, daemon=True).start()

while True:
    msg = input("Client: ")
    s.send(msg.encode())
    if msg.lower() == "exit":
        break

s.close()
```
## OUPUT
## server
<img width="497" height="123" alt="image" src="https://github.com/user-attachments/assets/1234653f-73bd-43d8-af8d-89492052ab25" />
## client
<img width="602" height="128" alt="image-1 (1)" src="https://github.com/user-attachments/assets/1afc5327-36bb-4dcb-80c6-3f002f35b2b3" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
