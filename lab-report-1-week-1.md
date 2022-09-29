
# Lab 1

### Hello, we will be working with ssh today!

## 1. Installing VS CODE

This is the easiest step. Download from the site below.      

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
- ls <directory> where <directory> is /home/linux/ieng6/cs15lfa22/cs15lfa22abc, where the abc is one of the other group members’ username
- cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
- cat /home/linux/ieng6/cs15lfa22/public/hello.txt

## 4. Moving files using scp


## 5. Setting a SSH Key


## 6. Optimizing remote running
