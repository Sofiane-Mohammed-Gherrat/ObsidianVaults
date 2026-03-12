
## Creating A User 

```Shell
sudo useradd -m -d /home/[username] -s /usr/bin/[bash or zsh] [username]
```
	-m : creates the home dir
	-d : the place where it's created
	-s : default shell
	-u : UID

#### Setting a password:

```Shell
sudo passwd [username]
```

#### Switch User:

```Shell
sudo su -i       # to root
su [username]    # to a user
su - [username]  # recommended: loads the env viriables -feels like fresh login
```

## Deleting a user

```Shell
sudo userdel [username]
```
#### Deleting the usr and home

```Shell
sudo userdel -r [username]
```

#### killing all the processes of the usr at once 

 ```Shell 
 sudo killall -u [username]
 ```


## Where the change happens:

> 3 files main files: 
- /etc/passwd : ( * no password ) ( **! can't login** )
- /etc/shadow
- /etc/group : `ls /etc/group | grep [username]` to list **all the groups** that usr belongs to.
##### Note:
>/etc/skel : defines the home dir skeleton 

#### Locking and Unlocking the usr:

> enabling the login through the password 

```Shell
sudo usermod -U [username] # Unlocked
sudo usermod -L [username] # Locked 
```

