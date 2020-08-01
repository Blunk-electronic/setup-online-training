# Guide on how to setup your PC for Online Training

In the course of the training you will be working on a remote training server. In order to connect your
workstation/PC with this server please read this guide carefully.

NOTE for network administrators: No incoming ports on your firewall have to be opened. The attendees 
will be establishing outgoing connections via SSH to the remote training server.

## Prerequisites
Before the training commences the teacher will provide you with:
- a user name and a password. The user name is usually something like "training2", "training3" etc.
- the IP of the remote training server like 45.154.144.35.

### Windows
Install the SSH client <span style="background-color: #FFFF00">Putty</span> from https://www.putty.org/

### Linux
Install a VNC viewer like Tiger VNC or the remote desktop client Remmina.
Both should come with mayor Linux distros.


## Set up a tunnel
Working on a remote server in graphical mode is based on the VNC, noVNC or RDP protocol. They use
the port numbers 5901, 5801 or 3389 respectively. Whatever protocol you will be using, it must be
tunneled from your location to the location of the training server. In our case we will setup
a tunnel for each protocol.
The protocol for the tunnel is SSH (port 22).

### Windows
Start Putty and do the setup as depicted in the follwing screenshots.
Enter in the red circled field the IP of the remote training server.

![startup](img/putty-destination.png)

Go to section Connection/SSH/Tunnels and enter the three tunnels:

![tunnels](img/putty-tunnels-list.png)

Click "open".
A console window opens. Enter your username and password.

![login](img/putty-login.png)

Now you have three tunnels ready: One for RDP, one for VNC and a third for noVNC.
Leave the console window open. 

### Linux
Open a terminal as a regular non-root user and type these commands which specify:
- the user name (e.g. training2),
- the IP of the remote training server

```sh
$ ssh -L 5901:localhost:5901 training2@45.154.144.35
```

```sh
$ ssh -L 5801:localhost:5801 training2@45.154.144.35
```




## Starting the remote session

### Operating system independed via webbrowser
- Start a webbrowser like Firefox or Chromium

### Windows
#### Via RDP client
- Start the remote desktop client. 
- Enter the computer address 127.0.0.2:3389 :

![addres](img/rdp-start-session.png)

- Login with your username and password:

![login](img/rdp-login.png)

- The session at the remote server opens.
![session running](img/rdp-session.png)

You are now ready for work !

#### Via VNC viewer
- Start the VNC viewer.

![address](img/tiger-vnc-1.png)
![disable TLS](img/tiger-vnc-security.png)
![login](img/tiger-vnc-login.png)
![session running](img/tiger-vnc-session.png)

### Linux
#### Via VNC viewer
Same as with Windows. See above.






