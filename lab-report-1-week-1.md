
# Lab 1

### Hello, we will be working with ssh today!

## 1. Installing VS CODE

This is the easiest step. Download from this *[site](https://code.visualstudio.com/download)*.

![vscode](VSCODE1.png)

Then, when you've installed it. Launch VS CODE          

![vscode1](VSCODE.png)


## 2. Remotely connecting

Now, you want to get your course specific account/User ID to log in to UCSD's server at:     
https://sdacs.ucsd.edu/~icc/index.php             
Reset the password and then type in **ssh cs15lfa22zz@&#65279;ieng6.ucsd.edu** where zz
is your unique id. It will ask you to type in your password you just reset.     

![remote](remote_access.png)

If it was your first time connecting, you might get a message asking if you want to       
continue connecting. Type in **yes**.


## 3. Trying some commands
Try these commands out.
- cd ~
- cd
- ls -lat
- ls -a
- ls <directory> where <directory> is /home/linux/ieng6/cs15lfa22/cs15lfa22abc,     
  where the abc is one of the other group members’ username
- cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lfa22/public/hello.txt
  
The results will be like this.
  
![tryingout](trying_commands.png)

These commands are the ones we learned during the first day of lecture. Revisit topics if necessary.
  
## 4. Moving files using scp
  
In this task, we will have to make a file at your local machine (WhereAmI.java) and import it
to UCSD's server or the remote machine.

![whereami](where_am_i.png)

We can test out the functionality of this file using the commands below.     

![whereami1](where_am_i_1.png)

Then, we will use this command at your **local machine** to move it to the **remote server**.        
**scp WhereAmI.java cs15lfa22zz@&#65279;ieng6.ucsd.edu:~/**

If successful, the results will be like this,    
  
![scp](scp.png)
 
We can check if the file transfer is succesful by logging into the server and look up the content.
  
![scp_success](scp_success.png)

## 5. Setting a SSH Key

Now, entering your password every now and then is quite tedious. We can set up an SSH key at your local     
machine and then import it to the remote machine. The process can be done by the commands below.

Initiallizing the key at local machine.
  
![keygen1](keygen_1.png)
  
You can see that there is a **mkdir .ssh** command after logging into the remote server.      
This command makes a directory at the remote server where we will save our ssh keygen. 
  
Now that we have generated a SSH key, we should import it to the remote server and save it.

![keygen2](keygen_2.png)
  
We can check in the remote server if the key is there.

![keygen_success](key_gen_success.png)
  
## 6. Optimizing remote running
  
Now, we can do new stuff because we have initiallized an ssh key in the remote server.    
For example, we can run multiple commands on a single line at the remote machine from the local machine    
without the tedious process of logging in first.    
Here are some examples:
  
![end](End.png)

For the first code, we can see that " " marks are used to directly use the command before        
logging in. For the second code, we can see that ; are used to run multiple commands.
