# SSH from operations point of view: Giving Access

When we talk about public key infrastructure. We have two keys: public key and the private key, You can provide your public key to anyone and then using that key that person can encrypt the message he wants to send and by using your private key you can decrypt the message and read it. On top level this is what happens in ssh encryption decrytion also. We will look deep into it in later chapter.

Lets see how you can give anyone access to any machine. 

For this you have to generate a keypair. To generate a keypair you can run the below command

```
ssh-keygen
```

When you will run this command you will see somefields to fill and after you fill them you will get your keys. 
You can find the keys at ~/.ssh directory. There will be two files of your interest

```
id_rsa                : Private key
id_rsa.pub            : Public Key 
```

Rememeber you never share your private key with anyone as this is your identity. 

Now that we have our public key which we have to put into server we will follow the below steps to put the key in the correct position.

### Scenario 1: Give access to already present user like root

Step 1. In the machine, go to the users home directory in this case, users home directory is `/root ` In all the other cases the home directory will be in `/home/username`
```
cd root   # or /home/username
```
Step 2. Open .ssh/authorized_keys file, if it is not present you can create it. 
```
vi authorized_keys 
```
Step 3. Paste your key in the file and close the file. Now your the person whose key you have added will have access to the user in whose home_directory/.ssh/authorized_keys file you have added the key. The user can ssh using below command.
```
ssh root@ip_of_the_server
```

### Scenario 2: Create a new user and give access to the user. 

This you should generally do and not add the keys to the existing user or root.

Step 1. Create user using below command
```
sudo adduser username
```

Step 2. Add the public key of the user in `/home/username/.ssh/authorized_keys.
You can follow scenario 1 for this. 

These were the cases where you have added your keys to the server to get the access. This can be other way around where you can take a key from server and use it to ssh to the server. 