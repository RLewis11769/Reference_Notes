# Docker Basics

## Docker Command Line

### Build image based on Dockerfile
- With -t to tag image with name
- With -f to specify Dockerfile
- With --target to specify stage to stop at (for multi-stage build)
- Combined
```
docker build .
docker build -t image_tagname .
docker build -f Dockerfile.dev .
docker build --target last_stage_to_build .
docker build -f Dockerfile.dev -t image_tagname .
```

### Run container
- With -d to run in background not attached to terminal
- With --name to name the container
- With -p to forward local port to container port
- With -v to mount a volume meaning connect local directory to container directory (production only)
	- Local directory must be full/absolute path - Either copy it directly or $(pwd) for Linux
	- If on Windows, use -f CHOKIDAR_USEPOLLING=true %cd%\
	- With :ro to make read-only (meaning one way from local to container, not vice versa)
	- This is called bind mounting - mount specified directory from host machine onto container (aka replicate directory tree at different location)
- With --env-file to load environment variables from a file
- With -f to specify Dockerfile
- Example development
- Example production
```
docker run image_tagname
docker run -d image_tagname
docker run --name container_name image_tagname
docker run -p 3000:3000 image_tagname
docker run -v local_directory:container_directory image_tagname
docker run --env-file ./.env image_tagname
docker run -f Dockerfile.dev image_tagname
docker run -d -p 3000:3000 -v $(pwd)/src:/app/src:ro --env-file ./.env -f Dockerfile.dev --name container_name image_tagname
docker run -d -p 8080:80 --env-file ./.env -f Dockerfile.prod --name container_name image_tagname
```

### List all images on computer
```
docker image ls
```

### Delete image
```
docker image rm image_tagname
docker rmi image_tagname
```

### List all containers on computer
aka list process status of all containers on computer
```
docker container ls
docker ps
```

### Stop container
Sends kill signal to stop container from running
If using, don't need to use -f when deleting
```
docker stop container_name
```

### Delete container
- With -f to force delete running container
```
docker rm container_name
docker rm container_name -f
```

### View container's command line
- Meaning execute command inside container
	- With -i to enter interactive mode/keep STDIN open
	- With -t to allocate pseudo-TTY/emulate terminal/provide endpoint
	- Execute bash command specifically
```
docker exec -it container_name bash
```

## Docker Compose
- Tool to manage docker containers
- Uses docker-compose.yml file
- Names image and containers according to own naming convention

### Start container
- Does not rebuild image each time it is run by default
	- Because looking for image with tag name in cache and can't specify tag name
	- Can run docker build separately
	- Or use --build option to build image before starting container
- With -f flag to specify docker-compose.yml file (order matters)
	- Base/shared file first, then specific file (overrides base)
```
docker-compose up
docker-compose up -d
docker-compose up --build
docker-compose -f docker-compose.yml -f docker-compose-dev.yml up
```

### Remove container
- With -f file if used to build
```
docker-compose down
docker-compose -f docker-compose.yml -f docker-compose-dev.yml down
```
