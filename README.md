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
client:
~~~
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
~~~
Server:
~~~
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
~~~
## OUPUT:

client:

<img width="936" height="338" alt="image" src="https://github.com/user-attachments/assets/057479d8-ae70-41b6-be0f-ebbf9b036346" />

server:

<img width="936" height="338" alt="image" src="https://github.com/user-attachments/assets/67614321-355e-4ec7-8de0-19cf807fc290" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
