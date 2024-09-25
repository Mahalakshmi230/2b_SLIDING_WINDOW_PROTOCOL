# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To write a python program to perform implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8050))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
       while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
        i+=s
```
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8050))
while True:
   print(s.recv(1024).decode())
   s.send("acknowledgement recived from the server".encode())
```
## OUPUT
CLIENT:

![Screenshot 2024-08-30 114227](https://github.com/user-attachments/assets/feac64df-74ab-47d6-97d3-fa8fd3832069)

SERVER:

![Screenshot 2024-08-30 114200](https://github.com/user-attachments/assets/459cd839-83bd-41ed-98f6-18c60c1662ce)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
