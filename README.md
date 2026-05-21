# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
~~~
client:
import socket
s=socket.socket()
s.bind(('localhost',8000))
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

server:
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())

## OUPUT:

client:
<img width="1180" height="235" alt="Screenshot 2026-05-21 143157" src="https://github.com/user-attachments/assets/3700fc36-6d26-4c4b-acfa-a03f65801d72" />

server:
<img width="1144" height="196" alt="Screenshot 2026-05-21 143209" src="https://github.com/user-attachments/assets/fa71a6a9-8aa0-4ebc-be2d-09bb474999a0" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
