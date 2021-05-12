# Chat-application
A Chat application made using Tkinter

## INTRODUCTION

Chat app will have one server that hosts the chat and multiple clients that connect to it and communicate with each other. The client-server architecture is a basic computing model where the client requests services from the server, while the server processes these requests and provides services to the clients,with a Graphical User Interface.
a server can serve multiple clients! In our application, we want many clients to be talking in real-time. The client software will send a message to the chatroom server, and the chatroom server will broadcast our message to all other connected clients.

### How chat application will work ? 
1. A client sends a message to the server from the command line or GUI.
2. The server receives and processes the message.
3. The server sends the message to all other connected clients.
4. The clients will display the message in the command line or GUI.
  
### Implementing the server
* For this we imported two libraries, namely ***socket and threading. The first one will be used for the network connection and the second one is necessary for performing various tasks at the same time.***
* The next task is to define our connection data and to initialize our socket. We needed an IP-address for the host and a free port number for our server. Here, we used localhost address (127.0.0.1) and the port 49806. The port is actually irrelevant but the port used should be free and not reserved. If trying to run this script on an actual server, specify the IP-address of the server as the host.
* When we define our socket, we need to pass two parameters. These define the type of socket we want to use. The first one ***(AF_INET)*** indicates that we are using an internet socket rather than an unix socket. The second parameter stands for the protocol we want to use. ***SOCK_STREAM*** indicates that we are using TCP and not UDP.
* After defining the socket, we bind it to our host and the specified port by passing a tuple that contains both values. We then put our server into listening mode, so that it waits for clients to connect. At the end we create two empty lists, which we will use to store the connected clients and their nicknames later on.
* Then we define a little function that is going to help us broadcasting messages and makes the code more readable. What it does is just sending a message to each client that is connected and therefore in the clients list. We will use this method in the other methods.
* What it then does is receiving the message from the client (if he sends any) and broadcasting it to all connected clients. So when one client sends a message, everyone else can see this message. Now if for some reason there is an error with the connection to this client, we remove it and its nickname, close the connection and broadcast that this client has left the chat. After that we break the loop and this thread comes to an end.
* When we are ready to run our server, we will execute this receive function. It also starts an endless while-loop which constantly accepts new connections from clients. Once a client is connected it sends the string ‘Shubham’ to it, which will tell the client that its nickname is requested. After that it waits for a response (which hopefully contains the nickname) and appends the client with the respective nickname to the lists. After that, we print and broadcast this information. Finally, we start a new thread that runs the previously implemented handling function for this particular client. Now we can just run this function and our server is done.

### Implementing the client
* A server is pretty useless without clients that connect to it. So client side needs to be implemented. For this, we will again need to import the same libraries. This is now a second separate script.
* The first steps of the client are to choose a nickname and to connect to our server. We will need to know the exact address and the port at which our server is running.
* Instead of binding the data and listening, we connect to an existing server.
* Now, a client needs to have two threads that are running at the same time. The first one will constantly receive data from the server and the second one will send our own messages to the server. So we will need two functions.
* The writing function is quite a short one. It also runs in an endless loop which is always waiting for an input from the user. Once it gets some, it combines it with the nickname and sends it to the server. The last thing we need to do is to start two threads that run these two functions.
* Apart from using simple socket and threading modules ,***Tkinter module is also used ,which is an inbuilt GUI library of python 3*** ,which basically helps in give our TCP chat app a graphical User interface ,which makes it quite easy for the user to use the Chat app.

## Running the chat

* Server Log:


 ![Screenshot 2021-04-28 192130](https://user-images.githubusercontent.com/47259965/117974468-37803400-b34b-11eb-9ba7-b4a32fc74478.png)
 
 
 * The Client log:


  ![Screenshot 2021-04-28 192029](https://user-images.githubusercontent.com/47259965/117974407-26cfbe00-b34b-11eb-9a88-17b3e03513a3.png)
  
  
 
  ![Screenshot 2021-04-28 192101](https://user-images.githubusercontent.com/47259965/117974454-33ecad00-b34b-11eb-8266-cec56f4e7d2b.png)
 

