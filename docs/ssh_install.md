# SSH installation and status

SSH is generally installed by default on most of the machines you will encounter. Especially on cloud it is installed by default. If it is not installed we can install it using the below commands for Ubuntu. 

```
sudo apt-get install openssh-server
```

Once this is installed you have to check if it is running, you can do it using the default systemd command like below. 

```
sudo service sshd status
```

If the service is active your ssh daemon is installed and is working.

To verify if it is working fine you can try and telnet to port 22 of that machine. 

```
telnet localhost 22
```

If you see something like this the service is running 

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_8.0p1 Ubuntu-6ubuntu0.1
```

There is a sshd daemon running which takes care of all the operrations. 

Now to ssh to the machine you can use the below command but before that we have to take a look into how public key and private key combination works. 

I will first take you to the simple approch to understand it and then we will go deep in understanding the math in this encryption technology.