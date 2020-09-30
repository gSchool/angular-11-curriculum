## Virtualization


Virtualization is central to the software development lifecycles of most major Enterprise operations. The core push toward virtualization was born out of the need to optimize server resources as companies scale and contract according to the needs of the market, fluctuations in demand for specific products, user trends, etc. 

In the early days of virtualization, the primary player in this space were Virtual Machines of "VMs" . Virtual machines would divide up machine resources and carve them into a section within the oprerating system that would function like an indepnedent computer in its own right.  This segmented environment , a "Virtual Machine", would have its own virtual hard drive, virtual RAM, virtual CPU, virtual networks, etc. Each VM has its own operating system, and would have to be configured and updated just like any physical machine, with software updates, patches, etc. 

In more recent years, another form of virutualization has emerged: containerization. You may already be familiar with Docker; Docker was the first major player in the move to make virtualzation faster and more efficient.  Containers are not virtual machines. Where a virtual machine requires an entire operating system to be installed and configured, containers *only* require a base image that has the necessary software installations required for the app or apps running in the container, and the actual software code that will be running based on that image. This makes spinning up a container exponentially faster than booting up an entire Virtual Machine, and it requries far less maintenance.  For example, you may have a Java app that requires a base disc image with a Java installation, and then your Java application's code that runs on top of that image.  While containerization has certain complexities that were not present when running a similar project on Virtual Machines, it is often argued that the speed and efficiency of containers make it worth it to move towards using containers for deploying virtual environments. 

We will be covering containerization, Docker, Kubernets, MKE, and other related topics in a future project. 


### !challenge

* type: multiple-choice
* id: 64D2A472-2757-4BBF-9902-028C74086794
* title: Virtualization
<!-- * points: [1] (optional, the number of points for scoring as a checkpoint) -->
* topics: virtualization

##### !question

Containers differ from virtual machines in that

##### !end-question

##### !options

* containers typically use more resources
* virtual machines usually live within containers
* containers typically use less resources
* containers take more time to boot up

##### !end-options

##### !answer
* containers typically use less resources

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, users can see after a failed attempt) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

Virtual machines emulate an entire machine, where containers are smaller spaces that only contain code and the supporting resources needed to run that code. This makes containers typically much smaller and faster to boot up. 

##### !end-explanation

### !end-challenge