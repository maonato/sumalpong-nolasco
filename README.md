OS155 project:
SSH key Rotation, optional auto aupdating public key and/or deleting old public key from the server

HOW TO USE:

open linux terminal

#you may begin at home directory
#Step One—Create the RSA Key Pair
ssh-keygen -t rsa
#Step Two—Store the Keys in mykey file
Enter file in which to save the key (/demo/.ssh/id_rsa):mykey

#The entire key generation process looks like this:

ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/demo/.ssh/id_rsa):mykey
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /demo/.ssh/id_rsa.
Your public key has been saved in /demo/.ssh/id_rsa.pub.
The key fingerprint is:
4a:dd:0a:c6:35:4e:3f:ed:27:38:8c:74:44:4d:93:67 demo@a
The key's randomart image is:
+--[ RSA 2048]----+
|          .oo.   |
|         .  o.E  |
|        + .  o   |
|     . = = .     |
|      = S = .    |
|     o + = +     |
|      . o + o .  |
|           . o   |
|                 |
+-----------------+

#copy the public key inside mykey.pub and paste in .ssh/authorized_keys in the server
#this are the steps:
#type
cat .ssh/id_rsa.pub | ssh user@address "cat >> ~/.ssh/authorized_keys"
#input the password of your server
#this should appear in your screen


The authenticity of host '12.34.56.78 (12.34.56.78)' can't be established.
RSA key fingerprint is b1:2d:33:67:ce:35:4d:5f:f3:a8:cd:c0:c4:48:86:12.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '12.34.56.78' (RSA) to the list of known hosts.
user@12.34.56.78's password: 
Now try logging into the machine, with "ssh 'user@12.34.56.78'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

#do that steps to all server that you want to acces using ssh command.

#lets start with the auto update script.
#NOTE: make sure that you already have performed the above steps..

#Step One—Create the RSA Key Pair
ssh-keygen -t rsa
#Step Two—Store the Keys in mykey file
Enter file in which to save the key (/demo/.ssh/id_rsa):mykey2

#The entire key generation process looks like this:

ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/demo/.ssh/id_rsa):mykey2
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /demo/.ssh/id_rsa.
Your public key has been saved in /demo/.ssh/id_rsa.pub.
The key fingerprint is:
4a:dd:0a:c6:35:4e:3f:ed:27:38:8c:74:44:4d:93:67 demo@a
The key's randomart image is:
+--[ RSA 2048]----+
|          .oo.   |
|         .  o.E  |
|        + .  o   |
|     . = = .     |
|      = S = .    |
|     o + = +     |
|      . o + o .  |
|           . o   |
|                 |
+-----------------+

#Step Three-create a file containing the list of addresses of your server that you want to update key and save as filename server...
#Step Four-run the Rotation.sh
