# Topics  ![Learn](https://img.shields.io/badge/Interview-Preparation-blueviolet?style=for-the-badge)

- [Topics !To Cover](#topics-cover)
  - [DevOps Interview Questions](#devops-interview-questions)
  - [Programming:](#programming)
  - [OS-Linux:](#os-linux)
  - [Networking:](#networking)
  - [Security:](#security)
  - [Docker](#docker)
  - [kubernetes](#kubernetes)
  - [Architecture:](#architecture)
  - [Infrastructure as Code:](#infrastructure-as-code)
  - [Setup](#setup)
  - [Cloud Computing](#Cloud Computing)
  
********
## DevOps Interview Questions


- Q1) Can you tell us the fundamental differences between DevOps & Agile?

  - Ans: Although DevOps shares some similarities with the Agile methodology, which is one of the most popular SDLC methodologies, both are fundamentally different approaches to software development. Following are the various fundamental differences between the two:

    - Agile Approach – The agile approach is only meant for development in Agile while the Devops approach is meant for both development and operations in DevOps.

    - Practices and Processes – While agile involves practices such as Agile Scrum and Agile Kanban, DevOps involves processes such as CD (Continuous Delivery), CI (Continuous Integration), and CT (Continuous Testing).

    - Priority – Agile prioritizes timeliness whereas, DevOps gives equal priority to timeliness and quality.

    - Release Cycles – DevOps offers smaller release cycles with immediate feedback while Agile offers only smaller release cycles without immediate feedback.

    - Feedback Source – Agile relies on feedback from customers while feedback from self (monitoring tools) is involved in DevOps.

    - Scope of Work – For Agile, the scope of work is agility only but for DevOps, it is agility and the need for automation.

- Q2) Why do we need DevOps?

  - Ans: Organizations these days are trying to transport small features to customers via a series of release trains instead of releasing big feature sets. There are several benefits of doing so, including better software quality and quick customer feedback.

  - All such benefits lead to a higher level of customer satisfaction, which is the most important goal for any product development project. To do so, companies need to:

      - Increase deployment frequency
      - Lessen lead time between fixes
      - Lower failure rate of new releases
      - In case of new release crashing, have a faster mean time to recovery

  - DevOps helps in fulfilling all these requirements and thus, achieving seamless software delivery. Full-fledged organizations like Amazon, Etsy, and Google have adopted DevOps methodology resulting in achieving performance levels that were previously uncharted.

  - With the adoption of DevOps methodology, organizations are able to accomplish tens to thousands of deployments in a single day. Moreover, doing so while offering first-rate reliability, security, and stability.

- Q3) What are the important business and technical benefits of using DevOps?

  - Ans: DevOps brings a lot of business and technical benefits to the table. Some of the most important ones are listed down as follows:

    - Business benefits:

      - Enhanced operating environment stability
      - Faster delivery of features
      - More time for adding value to the product

    - Technical benefits:

      - Continuous software delivery
      - Faster problem resolution
      - Lesser complex problems

- Q4) Can you name some of the most-used DevOps tools?

  - Ans: Following is a list of some of the most widely used DevOps tools:

      - Ansible/Chef/Puppet – A configuration management and application deployment tools
      - Docker/Podman/Rocket/CRI-O – A containerization tool
      - Kubernetes - Container Orchestration Tool.
      - Git – A version control system (VCS) tool.
      - Gitlab/Github - Source code hosting platform.
      - Jenkins – A continuous integration (CI) tool
      - Jira – An agile team collaboration tool
      - Nagios – A continuous monitoring tool
      - Selenium – A continuous testing (CT) tool

- Q5) What is Selenium used for?

  - Ans: Selenium is used for continuous testing in DevOps. The tool specializes in functional and regression forms of testing.

- Q6) What do you understand by Ansible in DevOps?
  
  - Ans: It is a configuration management tool that is used for automating administration tasks. Ansible makes use of the Controller-Targets architecture in which the two entities communicate via an secured/encrypted channel.

  - System admins need to perform a lot of repetitive tasks, notably installing and configuring servers. Writing scripts for automating such tasks is an option but it becomes hectic when the infrastructure is large. Configuration management is a great workaround for this.

  - Ansible helps in configuring, deploying, and managing servers. Not only does it make such redundant tasks easier but also cuts a significant portion of the total work time. The mature configuration management tool:

      - Continuously checks whether the needed configuration for a host is in place or not. If altered, the configuration is automatically reverted back
      - Defines distinct configurations for every host
      - Does dynamic scaling (up and down) of machines
      - Provides control over all the configured machines so that a centralized change can automatically get propagated to all of them

- Q7) What do you understand by anti-patterns of DevOps?
  
  - Ans: When a DevOps pattern commonly adopted by other organizations doesn’t work in a specific context and still the organization continues using it, it leads to the adoption of an anti-pattern. In other words, anti-patterns are myths about DevOps. 
  
  Some of the notable anti-patterns are:

      - An organization needs to have a separate DevOps group
      - Agile equals DevOps
      - DevOps is a process
      - DevOps is development-driven release management
      - DevOps is not possible because the organization is unique
      - DevOps is not possible because the people available are unsuitable
      - DevOps means Developers Managing Production
      - DevOps will solve all problems
      - Failing to include all aspects of the organization in an ongoing DevOps transition
      - Not defining KPIs at the start of a DevOps transition
      - Reduce the silo-based isolation of development and operations with a new DevOps team that silos itself from other parts of the organization

- Q8) DevOps has something called CI. What is it and what is its purpose?
  - Ans: CI in DevOps stands for Continuous Integration. CI is a development practice in which developers integrate code into a shared repository multiple times in a single day.

    - Continuous Integration of development and testing enhances the quality of the software as well as reducing the total time required for delivery.

    - The developer has broken the build if a team member checking in code runs into a compilation failure. As such, other developers are not able to sync with the shared source code repository without introducing compilation errors into their own workspaces.

    - This disrupts the collaborative and shared development process. Hence, as soon as a CI build breaks, it’s important to identify and correct the problem immediately.

    - Typically, a CI process includes a suite of unit, integration, and regression tests that run each time the compilation succeeds. In case any of the aforesaid tests fail, the CI build is considered unstable (which is common during an Agile sprint when development is ongoing) and not broken.

- Q9) More often than not we hear shift left in DevOps. What is it?
  - Ans: The traditional software development lifecycle when graphed on a paper has two sides, left and right. While the left side of the graph includes design and development, the right side includes production staging, stress testing, and user acceptance.

  - To shift left in DevOps simply means the necessity of taking as many tasks on the right i.e. that typically happens toward the end of the application development process and incorporate them into earlier stages of a DevOps methodology.

    - There are several ways of accomplishing a shit left in DevOps, most notably:
    - Create production-ready artifacts at the end of every Agile sprint 
    - Incorporating static code analysis routines in every build

  - The level of doing the DevOps the right way is directly dependent on the degree of shifting left as much as possible.

- Q10) What does CAMS in DevOps stand for?
  - Ans: The acronym CAMS is usually used for describing the core creeds of DevOps methodology. It stands for:

   - Culture
   - Automation
   - Measurement
   - Sharing

- Q11) What are the several KPIs used to gauge DevOps success?
  - Ans: KPIs is a contracted form of Key Performance Indicators. In order to measure the success of a DevOps process, several KPIs can be used. Some of the most popular ones are:

   - Application performance
   - Application usage and traffic
   - The automated test pass percentage
   - Availability
   - Change volume
   - Customer tickets
   - Defect escape rate
   - Deployment frequency
   - Deployment time
   - Error rates
   - Failed deployments
   - Lead time
   - Meantime to detection (MTTD)
   - Mean time to recovery (MTTR)

- Q12) In your opinion, what are the major benefits of implementing DevOps automation?
  - Ans: Following are the major benefits of implementing DevOps automation:

    - Removal of the possibility of human error from the CD equation (Core benefit)

    - As tasks become more predictable and repeatable, it is easy to identify and correct when something goes wrong. Hence, it results in producing more reliable and robust systems

    - Removes bottlenecks from the CI pipeline. It results in increased deployment frequency and decreased number of failed deployments. Both of them are important DevOps KPIs

- Q13) What do you understand by containers?

 - Ans: 
  - Containers are a form of lightweight Software virtualization that help in providing isolation among processes using Namespaces,CGroups,Selinux,Copy-On-Write.
  - Containers are heavier than a chroot but lighter than a hypervisor based VMs.

- Q14) Microservices are a core part of DevOps. Can you name any two popular Java development frameworks for creating microservices?
  
 - Ans: 
  - There are several Java frameworks that allow creating microservices. However, Eclipse MicroProfile and Spring Boot stand out from the herd as the two leading Java development frameworks used in DevOps for creating microservices.

- Q15) What do you understand by a Version Control System (VCS)? Define its uses.
  
 - Ans: 
  - A Version Control System or VCS is a system that is capable of recording changes made to a file or a group of files over time. 
  - Git and Mercurial are two of the most popular version control systems. Important uses of a VCS are:

   - Check what was the last modification that caused a problem
   - Compare the changes made over time
   - Identifying who introduced a new issue and at what time
   - Revert a file or files to some earlier state
   - Revert the complete project to a previous state

- Q16) Git is a popular DevOps tool. Tell us how you will revert a commit that has already been pushed and made public.
  - Ans: There are two ways of doing so:

    - By creating a new commit to undo all changes made by the commit that has already been pushed and made public. Following command is used for doing so:
    - git revert

    - By fixing or removing the bad file in a new commit and then pushing it to the remote repository. After making necessary changes to the file, commit it to the remote repository using the command:
    - git commit -m “commit message”

- Q17) What are post mortem meetings?

- Ans: 
    - Many times there is a need to discuss what went wrong during a DevOps release process. For this, post mortem meetings are arranged. These meetings yield steps that should be taken to avoid the same failure or set of failures in the future for which the meeting was arranged in the first place.

- Q18) Draw a comparison between Asset Management and Configuration Management.

- Ans:

  - The process of monitoring as well as maintaining things of value to an entity or group is called an Asset Management.

 - Configuration Management refers to the process of controlling, identifying, planning for, and verifying the configuration items within service in support of Change Management.

- Q19) Can you state and explain various key elements of continuous testing?
  - Ans: Various key elements of continuous testing are:

      - Advanced analysis – Used for forecasting and predicting unknown future events
      - Policy analysis – Meant for improving the testing process
      - Requirement traceability – Refers to the ability to describe as well as follow the life of a requirement, from its origin to deployment
      - Risk assessment – The method or process of identifying hazards and risk factors that can cause potential damage
      - Service virtualization – Allows using virtual services instead of production services. Emulates software components for simple testing
      - Test optimization – Improve the overall testing process

- Q20) Please explain the core operations of DevOps in terms of development and infrastructure.
- Ans: Core operations of DevOps in terms of development and infrastructure are:

    - Application development – Developing a product that is able to meet all customer requirements and offers a remarkable level of quality
    - Code coverage – Measurement of the total number of blocks or lines or arcs of the code executed while the automated tests are running
    - Code developing – Prepare the code base required for the product development
    - Configuration – Allowing the product to be used in an optimum way
    - Deployment – Installing the software to be used by the end-user
    - Orchestration – Arrangement of several automated tasks
    - Packaging – Activities involved when the release is ready for deployment
    - Provisioning – Ensuring that the infrastructure changes arrive just-in-time with the code that requires it
    - Unit testing – Meant for testing individual units or component.


- Q21) How Would You Explain the Concept of “Infrastructure as Code”(IaC)?

  - It is a good idea to talk about IaC as a programmable infrastructure, where infrastructure is perceived in the same way as any other code. 
  - Describe how the traditional approach to managing infrastructure is taking a back seat and how manual configurations, obsolete tools, and custom scripts are becoming less reliable. 
  - Next, accentuate the benefits of IaC and how changes to IT infrastructure can be implemented in a faster, safer and easier manner using IaC. 
  - Include the other benefits of IaC like applying regular unit testing and integration testing to infrastructure configurations, and maintaining up-to-date infrastructure documentation.

  - If the candidate have completed a certification on Amazon Web Services (AWS), and are interviewing for niche roles such as AWS-certified DevOps engineer, here are some AWS DevOps interview questions that you must be prepared for:

- Q22) What Is the Role of AWS in DevOps?

  - When asked this question in an interview, get straight to the point by explaining that AWS is a cloud-based service provided by Amazon that ensures scalability through unlimited computing power and storage. AWS empowers IT enterprises to develop and deliver sophisticated products and deploy applications on the cloud. Some of its key services include Amazon CloudFront, Amazon SimpleDB, - - - Amazon Relational Database Service, and Amazon Elastic Computer Cloud. Discuss the various cloud platforms and emphasize any big data projects that you have handled in the past using cloud infrastructure.


- Q23) How Is IaC Implemented Using AWS?

  - Start by talking about the age-old mechanisms of writing commands onto script files and testing them in a separate environment before deployment and how this approach is being replaced by IaC. Similar to the codes written for other services, with the help of AWS, IaC allows developers to write, test, and maintain infrastructure entities in a descriptive manner, using formats such as JSON or YAML. This enables easier development and faster deployment of infrastructure changes.



- Q24) What are the success factors for Continuous Integration?

  - Examples of answers:
      - Maintain a code repository
      - Automate the build
      - Make the build self-testing
      - Everyone commits to the baseline every day
      - Every commit (to baseline) should be built
      - Keep the build fast
      - Test in a clone of the production environment
      - Make it easy to get the latest deliverables
      - Everyone can see the results of the latest build
      - Automate deployment

.....................................

- Q25) How would you implement CI (continuous delivery) - end to end, including source control, branches, tools, etc. ?

- Q26) What is Continious Delivery? Continious Deployment?
  
- Q27) What is the difference between Continuous Integration, Continious Delivery and Continious Deployment?

- Q28) What’s the difference between git and gitlab/github/bitbucket ? What about git and SVN ?

- Q29) What is git rebase?

- Q30) In Git how do you revert a commit that has already been pushed and made public?

- Q31)  What is puppet/chef/ansible used for? What are the advantages over shell scripts ?

- Q32) What do you understand by “Infrastructure as code”? How does it fit into the DevOps methodology? What purpose does it achieve?

- Q33) How do you give your developers access to the production logs ?

- Q34) Tell me about the worst-run/best-run outage you’ve been a part of. What made it bad/well-run?

- Q35) How do you monitor your application ? How do you make sure it is working ? How do you get alerts when it stops working ?

- Q36) What would be the availability and performance metrics for a key value store ? What about for MySQL replication ?

- Q37) How would you deploy software to 5000 systems?

- Q38) What is caching ? Where should a large scale application cache, and what data should be cached ?


************
## Programming:

- Q1) What is your favorite scripting/programming language(s)? Why ?

- Q2) General CS, algorithms Q&A: 5 minutes

- Q3) Data structures - discuss possible implementations and applications:
    - Binary tree
    - Hash map
    - Heap

- Q4) Complexity classes - discuss and give examples:
  - Linear
  - Polynomial
  - NP Complete / NP Hard

- Q5) Sorting algorithms - discuss:
  - What is the fastest sorting algorithm?
  - What is the complexity of quick sort?

- Q6) Distributed systems:
    - What’s Paxos?
    - What's Raft?
    - What’s consistent hashing?

- Q7) Hands-on coding:
    - Inverse a string in place

- Q8) Deep Concept of DP and Graphs:

- Q9) Development Coding Questions.

- Q10) Describe a dev/test/production workflow using GIT
  - Feature branching vs trunk based development
  - Advantages of requiring pull requests and approvals
  
- Q11) More on Front-end Developer Job Interview Questions


***********

## OS-LINUX:

- Q1) How can you view running processes?
  - ps aux
  - top(htop)

- Q2) How do you check server uptime?
  - uptime
  - top

- Q3) How do you start/stop services?
  - (deprecated) service start/stop service_name
  - systemctl start/stop service_name

- Q4) How do you display the shell’s environment variables?
  - env
  - printenv

- Q5) What does #!/bin/bash at the top of a script do?
  - It say to shell, what interpreter to use when run this script

- Q6) What does "&" after a command do?
  - It run command in background

- Q7) What does piping commands mean?
  - piping with '|' transfer stdout of one command to another, for example,
  `ps aux | grep httpd` - first command show all running processes, then, transfer stdout to stdin of second command, whose find only strings where 'httpd'.

- Q8) What distributions have you used on servers?Why?
  - Ubuntu - very fresh kernels and packages
  - CentOS/RHEL - Enterprise and stability

- Q9) What is your favorite editor?

- Q10) What is RAID? What is RAID0, RAID1, RAID5, RAID10?

- Q11) Describe the general file system hierarchy of a Linux system.

- Q12) Describe what each of the following command line utilities do:
  - tee
  - awk
  - tr
  - cut
  - curl
  - tail
  - sed


- Q13) Command line demo:
  - Search for "my konfu is the best" in all *.py files
  - Replace the occurrence of "my konfu is the best" with "I'm a linux jedi master" in all *.txt files
  - Find all files which have been accessed within the last 30 days
  
- Q14) What is the difference between virtual memory and swap ?

- Q15) What is the difference between hardlinks and symlinks?

- Q16) What is an inode and what fields are stored in an inode?

- Q17) What are zombie processes ?

- Q18) Can you have several HTTPS virtual hosts sharing the same IP?
  - Yes, I can. I can setup several virtual hosts on one IP and split up yhem with different ports.

- Q19) What is the difference between processes and threads?

- Q20) What is the difference between exec and fork?

- Q21) How nginx can handle a lot of connections? What does it use inside?
  - Example of answer: Eventloop.

- Q22) What is "nohup" used for?

- Q23) What is an atomic operation?

- Q24) I've added my public ssh key into authorized_keys but I'm still getting a password prompt, what can be wrong?

- Q25) How do you catch a SIGHUP ? What about SIGSEGV ? What about SIGKILL ?

- Q26) What is the Linux Kernel OOM and how does it work ?

- Q27) What's a chroot jail?

- Q28) Describe the Linux boot process with as much detail as possible, starting from when the system is powered on and ending when you get a prompt.

- Q29) What's LD_PRELOAD and when is it used?

- Q30) You ran a binary and nothing happened. How would you debug this?
  - I run binary with strace, for example: strace binary_name

- Q31) When can a socket receive E_AGAIN ?

- Q32) What is a dynamically/statically linked file?

- Q33) A careless sysadmin executes the following command: chmod 444 /bin/chmod - what do you do to fix this?

- Q34) I've lost my root password, what can I do?

- Q35) You have accidentally deleted a running script, how could you restore it ?

- Q36) What load balancers have you used ?

- Q37) AWS:
    - What is the difference between an AMI and an instance ?
    - What’s EBS ? What’s an EBS snapshot ? What is the real cost of having an EBS snapshot ?
    - What’s a VPC ?
    - What’s the difference between a region and an availability zone ?
    - What’s an ELB ?
    - What’s S3 ? What are the features supported on S3 ?


******************

## Networking:

- Q1) What is IPv6 ? Why should we care?

- Q2) How does ping work ? What about traceroute ?

- Q3) I type http://www.yahoo.com in my browser’s URL bar and I press enter. What happens ? (discuss at every OSI layer - Physical, data link, network, transport, session, presentation, application)
    - DNS & anycast, IP, UDP, routing, BGP, TCP, HTTP, transparent proxy
    - What is BGP?
    - What’s a PTR in DNS? Why should we care?

- Q4) What if I change from http://www.yahoo.com to https://www.yahoo.com  ?
    - Public/private certificates, CAs, proxying, MiTM, etc.

- Q5) What happens when I press the send button in my email client ?

- Q6) How do we prevent bots crawling ? How would you deal with a syn flood ?

- Q7) How many hosts in a /24  network? What about a /22 ?

- Q8) What is the difference between DNAT and SNAT ? When do you use either ?

- Q9) What is a virtual IP address? What is a cluster?


*******************

## Security:


- Q1) What is the importance of SSL?

- Q2) What is a SQL injection?

- Q3) What is cross-site scripting (XSS)?

- Q4) Why shouldn’t you roll your own crypto?

- Q5) How are passwords stored on databases?

- Q6) What is a Man-in-the-middle attack?

- Q7) How do you safely manage environment variables in a cloud environment?

- Q8) How do you manage security updates?

- Q9) How do you keep encryption keys and credentials secure but make them available to machines that need them?


**********************


## Docker

- Q1) What is docker for?

- Q2) How to ask docker cli to show all containers&

- Q3) How to delete image with container, who use this image?

- Q4) What command help you to delete all old unused images?

- Q5) What is docker-compose? What is docker-compose.yml?

- Q6) How to expose ports in docker-compose file?

- Q7) How to reduce docker images?

- Q8) Where you  can store docker images?

- Q9) What is alpine and why we need it?

*********************


##  kubernetes



**********************


## Architecture:


******************


## Infrastructure as Code:



*******************

## Setup


**************


## Cloud Computing
