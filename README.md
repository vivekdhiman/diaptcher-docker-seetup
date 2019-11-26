Documentation to setup AEM Dispatcher with help of Docker with bare
minimum configuration. In addition, set up Docker Plugin in IntelliJIdea
to optimize the working with dispatcher.

**Step 1**

Checkout the below repository using below command

`git clone https://github.com/vivekdhiman/disptcher-docker-setup.git`

**Step 2**
Change Renderer in dispatcher.any will be change according to
environment. you can use below command to find the IP 

`ipconfig getifaddr en0 `

Open the termination and navigate to **docker** directory.
i.e. /disptcher-docker-setup/local/docker

**Step 3**

Build the httpd+dispatcher image of name **dispatcher-apache** by using below command.

`docker build -t dispatcher-apache .`

This command execute the Dockerfile present in current directory. In
terminal, you can view the step by step instructions gets execute for
the image.

**Step 4**

Now you need to run the docker container and specify the name. The command in a whole will be similar like below.

- HOSTIP <--> IP Address for container , can be replace with HOSTIP=$(ipconfig getifaddr en0)
- dispatcher-app <--> Container Name
- dispatcher-apache <--> Image File

`docker run -dit -e HOSTIP=$(ipconfig getifaddr en0) --rm --name dispatcher-app -p 8080:80 dispatcher-apache`

**Step 5**

Test Dispatcher by hitting URL [http://aem.dispatcher-dev:8080/] , you
must be getting response 404. In that case setup has been completed.

**Step 6**

To update and reflect and change in configuration file.

- We must first stop the container as with below command.

     `docker stop dispatcher-app`
- Rebuild Image (Step 2)
- Start the Container (Step 3)   

**Please read the following blog to manager docker based apache and
dispatcher using intelliJ IDEA plugins.**

[http://aemcorner.blogspot.com/2019/11/dispatcher-apache-management-using.html 
]

**Platform where this tested so
far**

OS Version - Mac

Installed Docker Version - 2.1.0.4

Apache - httpd:2.4

Dispatcher - 4.2.3