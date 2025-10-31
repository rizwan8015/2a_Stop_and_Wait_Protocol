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

### CLIENT:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))   # Bind the socket to host and port
s.listen(5)
print("Waiting for connection...")

c, addr = s.accept()
print(f"Connected with {addr}")

while True:
    i = input("Enter data: ")
    c.send(i.encode())

    ack = c.recv(1024).decode()
    if ack:
        print(ack)
        continue
    else:
        c.close()
        break
```

### SERVER:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement Received".encode())
```
## OUTPUT
### CLIENT:
<img width="767" height="217" alt="image" src="https://github.com/user-attachments/assets/b4b951d2-d2cf-4108-9044-498356d7f2b1" />

### SERVER:
<img width="836" height="122" alt="image" src="https://github.com/user-attachments/assets/0e819e95-1232-4a2a-90e2-49c3d1daa769" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
