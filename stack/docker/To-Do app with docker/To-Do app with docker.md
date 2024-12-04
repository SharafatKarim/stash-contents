---
Owner: Sharafat Karim
Last edited time: 2022-12-11T09:27
---
Let’s continue with our tutorial!

---

We used a docker local app,

![[app.zip]]

---

then a `Dockerfile`

```Bash
FROM node:10-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

and consequently running, (build)

`docker build -t docker-101 .`

then, we ran using,

`docker run -dp 3000:3000 docker-101`

---

It’s live here,

> [!info]  
>  
> [http://localhost:3000/](http://localhost:3000/)  

---

Let’s update a bit of our code, `~/app/src/static/js/app.js`

```Bash
-                <p className="text-center">No items yet! Add one above!</p>
+                <p className="text-center">You have no todo items yet! Add one above!</p>
```

and, build again and try to run. An error? Can you tell the reason?

First, list ID of the containers using,

`docker ps`

then stop it like,

`docker stop` _`id`_

> To force it to stop, use,  
>   
> `docker rm -f <the-container-id>`