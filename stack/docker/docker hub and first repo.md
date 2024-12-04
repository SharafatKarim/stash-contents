---
Owner: Sharafat Karim
Last edited time: 2022-12-11T09:53
---
let’s login first,

`docker login`

---

now, list our container by,

`docker images`

and also,

`docker images ls`

---

to upload try in this way,

first tag it,

`docker tag docker-101 sharafatkarim/101-todo-app`

and then push it,

`docker push sharafatkarim/101-todo-app`

---

once it’s in the repo, you can pull it like,

`docker run -dp 3000:3000 sharafatkarim/101-todo-app`