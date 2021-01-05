# Writeup Of My Forensics Challenges in Hac-Sec 21

It was a series of 3 challenges all based on analysis of log files of linux.

Challenge File is added in the repository if you want you can try it.

## Challenge - 1

```
what was the suspicious link attacker trying to download in the machine?

format: HAC-SEC{full_link}
```

## Solution - 1 

It was very easy task for solving this task we have to analyze `/var/log/apache2/access.log` and after looking closely we can see there's a github link of `linprivchecker.py`

## Flag - 1

`HAC-SEC{https://raw.githubusercontent.com/reider-roque/linpostexp/master/linprivchecker.py}`

## Challenge - 2 

```
what penetration tool was into the machine? provide path of log file inside the linux .

format: HAC-SEC{toolname_fullpathoflogfile}
```

## Solution - 2

For this challenge we have to analyze `/var/log/apt/history.log` because we can see all the tools installed in the system using `apt` 
as we can see `nmap` was installed in the system. 

## Flag - 2

`HAC-SEC{nmap_/var/log/apt/history.log}`

## Challenge - 3

```
According to Mr.Wolf the attacker was trying to send some secret file through the website can you find it?

Note: Flag is in standard format
```

## Solution - 3

we have to analyze `/var/log/apache2/access.log`
There's a lot of junk in some of the last links you can see there's a base64 encoded string
`(192.168.30.1 - - [24/Dec/2020:09:55:21 +0000] "GET /upload=aHR0cHM6Ly9oYXN0ZWJpbi5jb20venVoZWJlcWFwdS5yYg== HTTP/1.1" 404 492 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:83.0) Gecko/20100101 Firefox/83.0")`

just decode it and you will find hastebin link
`https://hastebin.com/zuhebeqapu.rb` 
after that we will see base64 and after decoding it we can see its a jpeg file convert it. 

and after analyzing the same log file there's a `justpasteit` link 

`https%3A%2F%2Fjustpaste.me%2FwUzx`

url decode it and visit it you will find password. 

`notaeasypasswordtoguessandbruteforce`

and it is very common when you have `.jpg` file just use steghide on it with the password given and you will get the flag.

## Flag - 3

`HAC-SEC{W0lfs_4r3_4m4z1nggg}`

Hope you enjoyed the challenges and learned something from them and feel free to contact me on discord.
Thanks for reading and good luck for future CTFs :)