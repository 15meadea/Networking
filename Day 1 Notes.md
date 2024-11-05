SSH First Connect
student@internet-host:~$ ssh student@172.16.82.106
The authenticity of host '172.16.82.106 (172.16.82.106)' can't be established.
ECDSA key fingerprint is SHA256:749QJCG1sf9zJWUm1LWdMWO8UACUU7UVgGJIoTT8ig0.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '172.16.82.106' (ECDSA) to the list of known hosts.
student@172.16.82.106's password:
student@blue-host-1:~$
You will need to approve the Server Host (Public) Key

#### Key is saved to /home/student/.ssh/known_hosts

SSH Re-Connect
ssh student@172.16.82.106
student@172.16.82.106's password:
student@blue-host-1:~$
Further SSH connections to server will not prompt to save key as long as key does not change

SSH Host key Changed
ssh student@172.16.82.106
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:RO05vd7h1qmMmBum2IPgR8laxrkKmgPxuXPzMpfviNQ.
Please contact your system administrator.
Add correct host key in /home/student/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/student/.ssh/known_hosts:1
remove with:
ssh-keygen -f "/home/student/.ssh/known_hosts" -R "172.16.82.106"
ECDSA host key for 172.16.82.106 has changed and you have requested strict checking.
Host key verification failed.

SSH Key Change Fix
ssh-keygen -f "/home/student/.ssh/known_hosts" -R "172.16.82.106"
Copy/Paste the ssh-keygen message to remove the Host key from the known_hosts file

When you re-connect it will prompt you to save the new Host key

SSH FILES
Known-Hosts Database

~/.ssh/known_hosts
Configuration Files

/etc/ssh/ssh_config
/etc/ssh/sshd_config
VIEW/CHANGE SSH PORT
To view the current configured SSH port

cat /etc/ssh/sshd_config | grep Port
Edit file to change the SSH Port

sudo nano /etc/ssh/sshd_config
Restart the SSH Service

systemctl restart ssh
SSH-KEYGEN
ssh-keygen -t rsa -b 4096 -C "Student"
Create your own SSH Public/Private keys

-t Encryption (rsa|dsa|ecdsa|ed25519)

-b Bit length (1024|2048|4096)

-C Adds a comment

~/.ssh/id_rsa and ~/.ssh/id_rsa.pub

SSH-COPY-ID
ssh-copy-id student@172.16.82.106
Copies your SSH Public key to the remote server

Saves key to ~/.ssh/authorized_keys on remote server

Allows you to authenticate with server using your key instead of password

Must secure your private key
