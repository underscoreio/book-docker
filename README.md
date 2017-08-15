# Docker Setup for Underscore Book Builds

**NOTE: THIS HAS BEEN REPLACED BY THE DOCKER TEMPLATE IN https://github.com/underscoreio/underscore-ebook-template**

This Dockerfile defines a container with all dependencies required to build Underscore's books, such as [Creative Scala](https://github.com/underscoreio/creative-scala/)

## Usage

To use this template you should:


- install Docker Compose (`brew install docker-compose` on OS X; or download from [docker.com](http://docker.com/)); 
- copy `docker-compose.yml` to the directory where the book source is checked out;
- run `docker-compose run book bash`.


This will setup a shared filesystem so the material on your local filesystem can be seen by the Docker container and turned into a book, and give a `bash` prompt to interact with the Docker container.

Within the `bash` prompt you most likely want to run `sbt` to build the book. For example, running

```bash
sbt pdf
```

to generate a PDF version of the book you're working on.


## Building

To create a new version of this container

```bash
docker build -t underscore/book .
```

Once it is built, login and push it to Docker Hub

```bash
docker login 
docker push underscore/book:latest
```

