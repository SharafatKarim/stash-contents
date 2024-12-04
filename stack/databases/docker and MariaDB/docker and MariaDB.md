---
Owner: Sharafat Karim
Last edited time: 2022-12-12T14:59
---
Official guide is actually good,

> [!info] Get Started with MariaDB using Docker in 3 Steps | MariaDB  
> There's no question that MariaDB has become one of the most popular databases of choice for developers over the past decade.  
> [https://mariadb.com/resources/blog/get-started-with-mariadb-using-docker-in-3-steps/](https://mariadb.com/resources/blog/get-started-with-mariadb-using-docker-in-3-steps/)  

---

Still let me explain a bit,

First let’s create,

```Bash
docker run -p 127.0.0.1:3306:3306  --name mdb -e MARIADB_ROOT_PASSWORD=Password123! -d mariadb:latest
```

> p for port forwarding, d for detached, e for environment variable, —name for custom name, I guess

---

now to connect,

```Bash
docker exec -it mdb mariadb --user root -pPassword123!
```

from TLDR;

![[/Untitled 2.png|Untitled 2.png]]

> [!important]  
> there’s no space between -p and password