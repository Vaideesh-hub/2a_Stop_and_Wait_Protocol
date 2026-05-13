# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
import socket
import threading
import time 

def server():
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind(("127.0.0.1", 5000))
    s.listen(1)
    print("Server is waiting for a connection...")

    conn, addr = s.accept()
    print("Connected by:", addr)

    data = conn.recv(1024)
    print("Client says:", data.decode())

    # Changed response message
    conn.send("Hi! Nice to meet you. How can I help you?".encode())

    conn.close()
    s.close()

def client():
    time.sleep(1)

    c = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    c.connect(("127.0.0.1", 5000))

    # Changed client message
    c.send("Hello Server! I need some information.".encode())

    response = c.recv(1024)
    print("Server says:", response.decode())

    c.close()

server_thread = threading.Thread(target=server)
client_thread = threading.Thread(target=client)

server_thread.start()
client_thread.start()

server_thread.join()
client_thread.join()
```
## OUTPUT
<img width="624" height="150" alt="image" src="https://github.com/user-attachments/assets/dc1da947-c204-4256-9319-4fbb874cfdaf" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
