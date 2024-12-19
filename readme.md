run all the yaml file using kubectl

run a frontend docker image<br>
    docker run -d --rm -p 8001:80 demo-frontend1


Problem faced:
    If you got CORS related problem then, add this piece of code in tasks-api.js
---
    app.use((req, res, next) => {
        res.setHeader('Access-Control-Allow-Origin', '*');
        res.setHeader('Access-Control-Allow-Methods', 'POST,GET,OPTIONS');
        res.setHeader('Access-Control-Allow-Headers', 'Content-Type,Authorization');
        next();
    })
---


Always edit the tasks-service ip address in frontend application<br>
// tasks-service ip is added in App.js(frontend/src/App.js) (minikube service tasks-service)


Now we will host the frontend in the cluster instead of using as docker container<br>
exposing our frontend application on port 8001:80

now create docker image and push to repo(docker-k8s:demo-frontend1)<br>
then apply deployment and service.<br>
then ~ minikube service frontend-service<br>
and take the ip and paste in browser.<br>

and make sure and the k8s-yaml file are up and running with latest tag

i.e - piyush168713/docker-k8s:demo-auth1<br>
      piyush168713/docker-k8s:demo-task4<br>
      piyush168713/docker-k8s:demo-user3<br>
      piyush168713/docker-k8s:demo-frontend1<br>
