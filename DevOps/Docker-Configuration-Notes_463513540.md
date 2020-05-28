Information Technology : Docker Configuration Notes  

###### [Home](https://github.com/RyKaj/Documentation/blob/master/README.md) | [DevOps](https://github.com/RyKaj/Documentation/tree/master/DevOps/README.md) |
------------
3.  [Kubernetes](Kubernetes_451820631.html)

Information Technology : Docker Configuration Notes
===================================================

Created by Ryan Kajiura, last modified on Feb 04, 2020



![](attachments/463513540/463513544.png)

  

> Docker 101, is a new series that I am beginning, to give you guys a closer look at the most buzzing word of the DevSecOps world. This new technology have been revolutionising the way deployment takes place while easing the headache of the DevOps people.

  

A Docker container is made up of layers of _images_, binaries packed together into a single package. The base image contains the operating system of the container, which can be different from the OS of the host.

The OS of the container is in the form an image. This is not the full operating system as on the host, and the difference is that the image is just the file system and binaries for the OS while the full OS includes the file system, binaries, and the kernel.

First, to give you a understanding of what Docker is I need you to remember everything you know about virtualisation or virtual machines. So, let’s recap for a moment a see what virtual machines do. Virtual machines allow you to setup a guest operating system over your current operating system i.e. you can run Ubuntu or Kali Linux machines on your Windows computer without a problem. All you have to do is download the .iso files for the guest OS and then install it in your virtualisation software like VMware, VirtualBox, etc. A pictorial representation of it would look something like this.

![](https://miro.medium.com/max/2526/1*U0HvIqjTr1xvfIusdjM_TA.png)

Now that you have a clear idea of what virtualisation is let’s proceed ahead and see what a Docker is and why do people keep comparing it with virtual machines. First, let me give you a pictorial representation of Docker so that you can understand easily.

![](https://miro.medium.com/max/2522/1*QwUgVGQNsNejKbSfkCTFgg.png)

Now, scroll back and forth and try to spot the differences between Docker and Virtual machines by yourself before I begin with my explanation.

Docker is nothing but a process that runs on the Host OS, which in turn helps us spawn containers inside of it. These containers allow developers to create a package for an application which contains the precise set of libraries, dependencies and toolset required to run the application. This is even more beneficial as the docker image of these containers, similar to .iso file for virtual machines can be shipped in one package wherever the application needs to be deployed. It can be any Linux machine irrespective of its flavour or the applications installed on the system and everything will work the way it should right out of the box.

Docker and Virtual Machine setup are similar only till the Host OS, but after that they differ a lot and it is these differences that makes all the difference let me point out how.

If the Docker requires only specific set of libraries, toolset and dependencies it will consume way less storage than a standard virtual machine. One more thing as there are less dependencies and libraries required for Docker hence the startup time for a virtual machine is extremely slow when compared to the startup time of Docker. All these benefits and we haven’t even talked about its greatest positive point and that is that Docker enables us to package an entire application and ship it to any Linux machine all over the globe without ever having to worry about integration and not having to spend hours and hours troubleshooting why your software ain’t working the way it should on a certain client’s system across the globe in a completely different timezone.

![](https://miro.medium.com/max/898/1*Y-bVQ7z1Ts2gFP7tpQyybg.png)

Now that we have clearly shown why Docker is better than Virtualisation solutions in a lot of way let’s actually see how to work with dockers and understand how this amazing tech works.

Docker has some other really really cool features, such as copy on write, volumes (shared file systems between containers), the docker daemon (manages containers on a machine), version controlled repositories (like Github for containers), and more. To learn more about them and see some practical examples of how to use Docker, this Medium [article](https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b) is extremely useful.

![](https://miro.medium.com/max/602/1*BO8iqCKHjeB6Fw9irS4oBw.png)

  

  

  

Training

  

References

*   [Medium - docker 101 introduction](https://medium.com/dev-sec-ops/docker-101-introduction-4c7785b70ccc)
*   [Medium freecodecamp - demystifying containers 101 a deep dive into container technology for beginners](https://medium.com/free-code-camp/demystifying-containers-101-a-deep-dive-into-container-technology-for-beginners-d7b60d8511c1)

Attachments:
------------

![](images/icons/bullet_blue.gif) [image.png](attachments/463513540/463513544.png) (image/png)  



