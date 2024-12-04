---
Owner: Sharafat Karim
Last edited time: 2022-12-11T10:03
---
Create a volume by using the `docker volume create` command.

`docker volume create` _`todo-db`_

Start the todo container, but add the `-v` flag to specify a volume mount. We will use the named volume and mount it to `/etc/todos`, which will capture all files created at the path.

```Plain
docker run -dp 3000:3000 -v todo-db:/etc/todos docker-101
```

---

to learn the file’s position in disk, run,

`docker volume inspect` _`todo-db`_