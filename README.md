# Detectron2 Dockerfile and Tutorial

This repository contains a Dockerfile for building a Detectron2 image capable of using the host's Nvidia CUDA enabled GPU
to do training and inference via the Detectron2 library.  The included Tutorial.ipynb can be accessed after running the 
created Docker image as a container.  

The command line for building the Dockerfile into an image is as follows:

```
docker build .
```
 
 After building, the Docker image can be tagged.  I have done so and uploaded the resulting image to my DockerHub with the 
 tag jdillenburg/Detectron2:latest.
 
 ```
 docker tag 6d96a79d576a68246a0803ea9e1e1e57d39d4134571e19a062f5ad08028a34f6 jdillenburg/detectron2:latest
 ```
 
 Note that the long hexadecimal number is the container ID as output by the build command.
 
 The built image can be run using the following command:
 
```
 docker run --gpus all -d -it -p 8888:8888 -v /d/python/detectron2:/home/appuser/src jdillenburg/detectron2:latest
 
```

After runnig the container, the container ID will bbe printed to the console.  You can then use that container ID to obtain the 
jupyterlab token needed to authenticate to the website:

```
(base) PS D:\python\detectron2> docker exec -it bca3cf87bf0822cfeadcdcd7eb89fd1b1acb921512adab7eb7661e5c6fbaa22f jupyter server list
[JupyterServerListApp] Currently running servers:
[JupyterServerListApp] http://bca3cf87bf08:8888/?token=ae07fecdbe1a3a63e8b6a30aebe22d3cacddfdaccfdf97c5 :: /home/appuser/src
```

Point your web browser at http://localhost/?token=ae07fecdbe1a3a63e8b6a30aebe22d3cacddfdaccfdf97c5

You should see Jupyterlab which you can use to open up and run the Tutorial.ipynb file.

John Dillenburg
[dillenbu@uic.edu](mailto:dillenbu@uic.edu)