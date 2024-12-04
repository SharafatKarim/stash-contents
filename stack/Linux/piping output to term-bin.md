---
Owner: Sharafat Karim
Last edited time: 2022-12-11T08:12
---
pipe the output like,

`pacman -Q | grep wallet | nc termbin.com 9999`

---

first command and pipe it using `nc` (Netcat)

> ==**nc**==
> 
> **Netcat** is a versatile utility for working with **TCP** or **UDP** data.
> 
> More information: _https://nmap.org/ncat._
> 
> - Listen on a specified port and print any data received:
> 
> `nc -l port`
> 
> - Connect to a certain port:
> 
> nc ip_address port
> 
> `- Set a timeout:`
> 
> nc -w timeout_in_seconds ipaddress port
> 
> - Keep the server up after the client detaches:
> 
> `nc -k -l port`
> 
> - Keep the client up even after EOF:
> 
> `nc -q timeout ip_address`
> 
> - Scan the open ports of a specified host:
> 
> `nc -v -z ip_address port`
> 
> - Act as proxy and forward data from a local TCP port to the given remote host:
> 
> `nc -l local_port | nc hostname remote_port`  
>   
> 
> ==source TLDR (too long didn’t read)==