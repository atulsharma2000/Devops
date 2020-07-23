
𝗔𝗜𝗠 :

1. Create container image that’s has Jenkins installed using dockerfile 

2. When we launch this image, it should automatically starts Jenkins service in the container.

3. Create a job chain of job1, job2, job3 and job4 using build pipeline plugin in Jenkins

4. Job1 : Pull the Github repo automatically when some developers push repo to Github.

5. Job2 : By looking at the code or program file, Jenkins should automatically start the respective language interpreter install image container to deploy code ( eg. If code is of PHP, then Jenkins should start the container that has PHP already installed ).

6. Job3 : Test your app if it is working or not.

7. Job4 : if app is not working , then send email to developer with error messages.

8. Create One extra job job5 for monitor : If container where app is running. fails due to any reson then this job should automatically start the container again.


𝐏𝐫𝐞𝐫𝐞𝐪𝐮𝐢𝐬𝐢𝐭𝐞 :

- VMware for virtualization
- RedHat Enterprise linux 8 image installed on VMware
- Docker for OS-level virtualization(to create images and containers on RHEL8)
- Jenkins(a great DevOps tool for automation)
- Github account

𝐓𝐡𝐞𝐨𝐫𝐲 :

- What is DevOps?
    DevOps is a set of practices that combines software development and IT operations. It aims to shorten the systems development life cycle and provide continuous delivery with     high software quality.

- What is jenkins?
    Jenkins is a free and open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous     integration and continuous delivery.

- What is docker os level virtualization?
    Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers.
    Container technology is a method of packaging an application so it can be run with isolated dependencies, and they have fundamentally altered the development of software         today due to their compartmentalization of a computer system.
    OS-level virtualization refers to an operating system paradigm in which the kernel allows the existence of multiple isolated user-space instances.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐚𝐧𝐝 𝐈𝐦𝐩𝐥𝐞𝐦𝐞𝐧𝐭𝐚𝐭𝐢𝐨𝐧:

(1) Install VMware on your host operating system. In VMware install the RHEL8 operating system. In RHEL8 install Docker(first you have to install all the requirements of Linux and configure yum and then install docker on RHEL8).

(2) Create a directory in linux, and in that directory create a file named as "Dockerfile" with all of this content as shown:
      ![1st](https://user-images.githubusercontent.com/41663027/88304968-8ca07a00-cd26-11ea-92eb-e9ee82b669a0.PNG)
      - here we installing latest version of centos
      - in centos we installing wget, sudo, git
      - then installing best suitable version of java (java beacuse jenkins works on java)
      - now installing jenkins in centos 
      - giving permissions and running jenkins
      - exposing it to port 8080
      
(3) Now building an image from the Dockerfile and running it: 
![2](https://user-images.githubusercontent.com/41663027/88308579-d723f580-cd2a-11ea-8a6f-ddf1a1a1df60.PNG)
![3](https://user-images.githubusercontent.com/41663027/88308741-0470a380-cd2b-11ea-8162-bf13e8b615a1.PNG)
      - docker build -t centkins:v1 task2/
      - docker run -it --name task centkins:v1
      
(4) Now we switch to Jenkins dashboard, creating our first job.
    job-1 is basically dealing with our production, it will automatically pull the latest updated github repository as soon as devloper push to github repository.
    ![j11](https://user-images.githubusercontent.com/41663027/88310718-a09baa00-cd2d-11ea-82f5-20c2c75973e7.PNG)
    ![j12](https://user-images.githubusercontent.com/41663027/88310785-b1e4b680-cd2d-11ea-88cb-cfa1b204e02b.PNG)
    ![j13](https://user-images.githubusercontent.com/41663027/88310803-b9a45b00-cd2d-11ea-9b7c-6bda92ccd144.PNG)
      - here we providing github repository details to jenkins 
      - scheduling POLL SCM, so that as soon as jenkins see any update pushed by the devloper then it will pull it
      - after pulling it, jenkins will run shell command to paste the updated repository in our directory














