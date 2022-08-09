# Class 24

Live link: [Django REST Framework & Docker](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2024/)

## Django REST Framework & Docker

---

### A Beginner's Guide to Docker

With Docker we now longer have to mess around with virtual environments.
We can faithfully reproduce a production environment locally. And Docker can be shared
among team members so everyone is working on the same setup. Wins all around.

> What’s the downside? Complexity. Docker is a complex beast under the hood.
> However a little knowledge can take you a long way and that’s the goal of this guide!

### Linux Containers

Docker is really just Linux containers which are a type of virtualization.

> What’s the downside to a virtual machine? Size and speed.

In recent years Linux containers, also known as “containerization,” has become
increasingly popular. For most applications, a virtual machine provides far more
resources than are needed and a container is more than sufficient.

> This, fundamentally, is what Docker is. A way to implement Linux containers!

### Containers vs Virtual Environments

- virtual environments can only isolate Python packages.
- They still rely on a global, system-level installation of Python albeit they can refer
  to the proper version.
- So when we use Python 2.7 in a project, we’re pointing to an installation of Python 2.7
  on the computer itself, not actually within the virtual environment.
- We can’t run a production database or other services within virtual environments so
  compared to Docker containers they are far more limited.

### Install Docker

- download the desktop app on our computer & create a free account
- we can confirm the correct version is running. It should be at least version 19.
  - $ docker --version
- Now run the command below to confirm you have a working version of it, too. The version should be at least 1.24.x.
  - docker-compose --version
- To confirm Docker installed correctly we can run our first command
  - docker run hello-world

### Images and Containers

Images and containers are the two fundamental concepts to grasp when you start with Docker.
> An image is a snapshot in time of what a project contains
>
> A container is a running instance of the image.

A baking analogy we can use here is as follows:

- A Dockerfile is the recipe for a cake
- An image is a snapshot of the recipe at a given time
- A docker-compose.yml says how to make the cake
- And the container is the actual, baked cake

## Conclusion

That last example with Django probably felt a bit too fast to fully understand.
And that’s ok. I wanted to show a working example without getting too bogged down in the
complexity of images and containers.

The important takeaways from this tutorial are this:

- Docker is a way to run Linux containers
- Containers are a lightweight alternative to Virtual Machines
- Dockerfile is a list of instructions for creating an image
- Images are made up of one or more layers
- Containers are a running instance of an image
- docker-compose.yml controls how to run the container
- Containers are stateless and ephemeral in nature. We can link the local filesystem via volumes but things become more
  complex with databases (which we didn’t cover here).

## Notes

- Dockerfile :Similar to a Pipenv or a requirements.txt file; it is a list of all the requirements needed to build our
  image. It is simpler to have them all in one place rather than install each manually line-by-line.

---
Resources:

## [Docker](https://wsvincent.com/beginners-guide-to-docker/)

---

### Django REST Framework

### What is it

works alongside the Django web framework to create web APIs. We cannot build a web API
with only Django Rest Framework. It always must be added to a project after Django itself
has been installed and configured.

### 2 Types

- A traditional Django website consists of a single project with multiple apps
  representing discrete functionality.
- Instead, it is just pure data ( often in the JSON format) and accompanying HTTP
  verbs that specify what user actions are allowed. In this instance, an API user can only
  read the content, they are not able to update it in any way though we will learn how to do that in future chapters.

---
Resources:

## [Django REST Framework](https://djangoforapis.com/library-website-and-api/)

## [API](https://djangoforapis.com/library-api/)

---
