#  Network using Dockerfile and docker commands

##   Step 1: Create Docker network

```bash
docker network create app-network
```

##   Step 2: Run MongoDB container

```bash
docker run -d --name mongo --network app-network mongo
```
##   Step 3: Build & run backend

```bash
cd backend
docker build -t my-backend .
docker run -d --name backend --network app-network -p 5000:5000 my-backend
```

##  Step 4: Build & run frontend

```
cd ../frontend
docker build -t my-frontend .
docker run -d --name frontend --network app-network -p 3000:3000 my-frontend
```

✅ What You’ve Achieved So Far
MongoDB and Node.js talk using `mongo` as hostname.

React talks to backend via backend hostname (if needed) but if you are using browser outside the container you have to used localhost.

You can now open localhost:3000 and the backend API made as http://localhost:5000/.


##  Why not backend:5000, why localhost:5000?