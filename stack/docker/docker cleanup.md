---
Owner: Sharafat Karim
Last edited time: 2022-12-12T11:58
---
First let’s check both running and stopped containers,

`docker ps --all`

You can remove one by using,

`docker rm` `_container-ID_`

> [!important]  
> docker rm and docker stop aren’t same! You can use docker start to start a stopped container!  

---

And finally,

`docker system prune`

> [!important]  
> WARNING! This will remove:- all stopped containers- all networks not used by at least one container- all dangling images- all dangling build cache