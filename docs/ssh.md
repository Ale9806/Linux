# Secure Shell

Secure Shell (SSH) is a cryptographic network protocol for operating network services securely over an unsecured network. Typical applications include remote command-line, login, and remote command execution, but any network service can be secured with SSH.

SSH provides a secure channel over an unsecured network by using a client–server architecture, connecting an SSH client application with an SSH server. The protocol specification distinguishes between two major versions, referred to as SSH-1 and SSH-2. The standard TCP port for SSH is 22. SSH is generally used to access Unix-like operating systems, but it can also be used on Microsoft Windows. Windows 10 uses OpenSSH as its default SSH client and SSH server.

## Conect using ssh
First you gotta make sure that the deivce you want to connect has ssh enabeled, in this example we will connect to a raspberry pi 4

```bash
user@desktop:~$ ssh [user]@[ip address]
[user]@[ip address]'s password: ************
pi@user:~ $  
```
Once we have established the conection we have gained remote acces to our raspberry pi.

## Sending files via SSH
scp (secure copy) command in Linux system is used to copy file(s) between servers in a secure way. The SCP command or secure copy allows secure transferring of files in between the local host and the remote host or between two remote hosts.

**Sending files from local computer to remote computer**

```
scp path/on/my/computer [username]@[IP address]:path/to/file/on/server 
```
**Sending files from remote computer to local computer**

* Login using SSH
```
scp [username]@[IP address]:path/to/file/on/server path/on/my/computer
```


## Close SSH connection
In orer to close the secure conextion we established we can type `~.` that is it.