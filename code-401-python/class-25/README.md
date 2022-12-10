# Class-25
## Django REST Framework & Docker
#### A Beginner's Guide to Docker
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT6fUpMbzSMaFi9s2xZlKmBcocG4rSNaYlpy-KavyDlEzy2gxbu3N4TyuNJeuwt0LlbIsc&usqp=CAU)
- Docker is a platform designed to help developers build, share, and run modern applications. We handle the tedious setup, so you can focus on the code.
-Docker can be shared among team members so everyone is working on the same setup.
- **Linux Containers**
    - Docker is really just Linux containers which are a type of virtualization.
    - **Virtualization** has its roots at the beginning of computer science when large, expensive mainframe computers were the norm.
- Containers vs Virtual Environments
    - Virtualization aims to run multiple OS instances on a single server, whereas containerization runs a single OS instance, with multiple user spaces to isolate processes from one another. This means containerization makes sense for one AWS cloud user that plans to run multiple processes simultaneously.
- Images and Containers
    - Images and containers are the two fundamental concepts to grasp when you start with Docker. An **image** is a snapshot in time of what a project contains. A **container** is a running instance of the image.
    - ```Dockerfile``` is a list of instructions for creating an image
    - Images are made up of one or more layers
    - Containers are a running instance of an image
    - ```docker-compose.yml``` controls how to run the container
    - Containers are stateless and ephemeral in nature. We can link the local filesystem via ```volumes``` but things become more complex with databases (which we didn’t cover here).
![](https://miro.medium.com/max/1400/1*p8k1b2DZTQEW_yf0hYniXw.png)

#### Django for APIs - Library Website
- We cannot build a web API with only Django Rest Framework. It always must be added to a project after Django itself has been installed and configured.
- **Traditional Django**
    - A traditional Django website consists of a single project with multiple apps representing discrete functionality
- **Django REST Framework**
    - Web API will expose a single endpoint that lists out all books in JSON. To do this, it will need a new URL route, a new view, and a new serializer file.
    - Django REST Framework views are similar except the end result is serialized data in JSON format, not the content for a web page! Django REST Framework views rely on a model, a URL, and a new file called a serializer
    - **Serializers** 
        - A serializer translates complex data like querysets and model instances into a format that is easy to consume over the internet, typically JSON.
        - It is also possible to “deserialize” data, literally the same process in reverse, whereby JSON data is first validated and then transformed into a dictionary. 
    - **Browsable API**
        - Django REST Framework ships with a built-in browsable API that **displays both the content and HTTP verbs associated with a given endpoint**.