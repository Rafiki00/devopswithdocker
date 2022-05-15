# Part 1
Completed exercises for part 1 of the DevOps with Docker course.

## Exercise 1.1: Getting started

```bash
> docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS                          PORTS     NAMES
8b60c7c41524   nginx     "/docker-entrypoint.…"   About a minute ago   Up About a minute               80/tcp    peaceful_merkle
9a49b5447781   nginx     "/docker-entrypoint.…"   About a minute ago   Exited (0) 3 seconds ago                  priceless_stonebraker
32faa912d009   nginx     "/docker-entrypoint.…"   13 minutes ago       Exited (0) About a minute ago             recursing_lovelace
```

## Exercise 1.2: Cleanup

```bash
> docker ps -as
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES     SIZE
```
```bash
> docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```

## Exercise 1.3: Secret message

```bash
> docker run -d -it devopsdockeruh/simple-web-service:ubuntu
```
```bash
> docker exec -it admiring_mayer bash
```
```bash
> tail -f text.log
```
```bash
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2022-05-03 10:36:37 +0000 UTC
2022-05-03 10:36:39 +0000 UTC
2022-05-03 10:36:41 +0000 UTC
2022-05-03 10:36:43 +0000 UTC
2022-05-03 10:36:45 +0000 UTC
```

## Exercise 1.4: Missing dependencies

```bash
> docker run --rm -it --name web_getter ubuntu sh -c 'echo \"Input website:\"; read website; echo \"Searching..\"; sleep 1; curl $website;'
```
I needed to escape the double quotes with backslash in order to pass the correct statement to execute.
This command outputs 'Input website:' and waits for an input. While it does this, I opened another terminal and did the following:
```bash
> docker exec -it web_getter bash
```
```bash
> apt update
```
```bash
> apt install curl
```
Then back in the first terminal I input the website and get the following response:
```bash
> docker run --rm -it --name web_getter ubuntu sh -c 'echo \"Input website:\"; read website; echo \"Searching..\"; sleep 1; curl $website;'
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://www.helsinki.fi/">here</a>.</p>
</body></html>
```

## Exercise 1.5: Sizes of images

```bash
> docker images
REPOSITORY                          TAG       IMAGE ID       CREATED         SIZE
devopsdockeruh/simple-web-service   ubuntu    4e3362e907d5   13 months ago   83MB
devopsdockeruh/simple-web-service   alpine    fd312adc88e0   13 months ago   15.7MB
```
```bash
> docker exec -it jolly_davinci sh
/usr/src/app # tail -f text.log
2022-05-03 14:46:58 +0000 UTC
2022-05-03 14:47:00 +0000 UTC
2022-05-03 14:47:02 +0000 UTC
2022-05-03 14:47:04 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
```

## Exercise 1.6: Hello Docker Hub

```bash
> docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete
5e2195587d10: Pull complete
6f595b2fc66d: Pull complete
165f32bf4e94: Pull complete
67c4f504c224: Pull complete
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```


## Exercise 1.7: Two line Dockerfile

[Dockerfile](./1.7/Dockerfile)
```bash
> docker run web-server
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /*path                    --> server.Start.func1 (3 handlers)
[GIN-debug] Listening and serving HTTP on :8080
```

## Exercise 1.8: Image for script

[Dockerfile](./1.8/Dockerfile)


## Exercise 1.9: Volumes

```bash
docker run -d -it -v "C:\Users\Rafa9\OneDrive\Escritorio\devops\text.log:/usr/src/app/text.log" devopsdockeruh/simple-web-service:alpine
```

## Exercise 1.10: Ports open

```bash
docker run -d -it -p 8080:8080 devopsdockeruh/simple-web-service:alpine server
```
