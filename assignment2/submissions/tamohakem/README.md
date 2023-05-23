## My name is tamohakem Outcomer and please file below my submission

## Kubernetes, Docker, Containerisation and Virtualisation

1. Containers and Virtual machines are two approaches to deploying applications. Name the advantages and disadvantages of each.

containers have the following advantages and disadvantages:

Portability

As a part of a distributed system, containers are highly portable.

Because containers pack microservices and their dependencies in a small-sized package, it’s easy to move containers around, even across different cloud environments.

    Effective resource usage

Code packaged within containers share most of the dependencies needed to run the containers, including an operating system, libraries, and frameworks.

Unlike in virtual machines, there’s only one copy of necessary files in each hardware, leading to more effective resource usage. 

    Easier to maintain

As containers use a microservices-based architecture, your code is broken down into manageable pieces that can be handled individually. Hence, you can update and maintain a container without worrying it will affect other parts of your application.

    Highly Scalable

Container orchestration platforms are created to help you manage your containers. Container orchestrators, like Kubernetes or Docker Swarm, automate most of your container management process, including scaling, networking, and deployment.

Containerized applications are highly scalable, and they can scale up and down quickly by spinning up new nodes and/or pods when the needs call for it.

    Disadvantagies:

    Lacking Security measures

Containers provide lightweight isolation from the host OS and containers within the same system. This leads to a weaker security boundary compared to virtual machines.

    Runs only one OS

This can be a benefit if you only use one OS, but if you need to be able to use it across different OS’s this is a negative. You can run an earlier version of the same OS using lightweight virtual machines.

Virtual Machines have the following advantages and disadvantages:
    Advantages:

    Hard security boundaries

VMs provide more isolation between neighboring systems, as you’re using a separate operating system from other machines in the same physical server. Whereas in containers, you’re operating within one OS, and flaws can affect the entire system.

The complete isolation in VMs results in better security, and vulnerabilities that are harder to exploit.

    Can emulate multiple OS

As you can run any operating system you want within a virtual machine, you don’t need to buy another hardware every time you need a different OS.

    More resources

The resources allocated for a virtual machine are far more than what’s allocated for containers. That’s why VMs are more suitable for resource-intensive tasks. Tasks with larger sizes and a long lifecycle are more suitable to use with VMs rather than containers.

Disadvantages:

    Not as portable

Virtual machines are gigabytes-sized chunks of software.

Naturally, it’s harder to move a virtual machine when compared to a container, because the applications run on a virtual machine that is highly dependent on the OS and the emulated hardware it runs on.

    Ineffective resource usage

Often, the resources provided by virtual machines are too much for running a single application.

However, once a VM is assigned to a resource, it takes up the whole space, even when it needs less. This creates idle power that you can use elsewhere if your planning is inaccurate.

    Harder to maintain the OS

As there are multiple operating systems in one VM, you need to update and maintain each OS separately. This is a time consuming and exhausting task, especially if you have multiple VMs.

2. What is a Docker image and how are they created?

A Docker image is a lightweight, standalone, and executable package that contains everything needed to run a piece of software, including the code, runtime, system tools, system libraries, and dependencies. It provides a consistent and reproducible environment for running applications, regardless of the underlying infrastructure.

Docker images are created using a declarative file called a Dockerfile. The process of creating a Docker image involves the following steps:

    Choose a base image: A base image is the starting point for the Docker image. It provides the foundation of the operating system and includes essential tools and libraries. You can choose a base image that matches the requirements of your application.

	Write a Dockerfile: Create a Dockerfile in your project directory or repository. The Dockerfile defines the steps needed to build the image. It includes instructions such as copying files into the image, installing dependencies, configuring the environment, and specifying the commands to run.

	Define the build context: The build context is the set of files and directories that are sent to the Docker daemon to build the image. When you build the image, Docker looks for the Dockerfile in the build context directory and uses it to create the image.

	Build the image: Use the docker build command to build the image. This command reads the Dockerfile, follows the instructions, and generates a new Docker image. During the build process, Docker executes each instruction in the Dockerfile and creates a new layer for each instruction. Layers are cached, which allows subsequent builds to be faster if the instructions haven't changed.
	Finally,Tag and push the image (optional): Once the image is built, you can tag it with a name and version using the docker tag command. 

3. What is a Docker container and how might you run them?

A Docker container is an instance of a Docker image that is running as a process on a host machine.
To run a Docker container, you typically follow the following steps:
    a. Obtain the Docker image: First, you need to have the Docker image that you want to run. You can either build the image yourself using a Dockerfile (as explained in the previous question) or pull it from a container registry using the docker pull command. Docker Hub is a popular public registry that hosts a vast collection of pre-built Docker images.

    b. Start a container: Once you have the Docker image, you can use the docker run command to start a container based on that image. This command creates a new container instance and starts it.

    c. Configure container options: The docker run command allows you to specify various options and configurations. 

    d. Interact with the running container: Once the container is running, you can interact with it in various ways like, view the container logs using the docker logs command, access the container's shell using docker exec -it, stop the container using docker stop, and start or restart it using docker start or docker restart, respectively.

## Linux administration and shell scripting

1. Write a shell script that takes a single input arguments and echoes it back when it is run.

#!/bin/bash
# Check if an argument is provided
if [ $# -eq 0 ]; then
    echo "No input argument provided."
    exit 1
fi
# Echo the input argument
    echo "Input argument: $1"

2. Write a shell script that creates a directory call "sports" and inside the "sports" directory create two other subdirectories called "football" and "handball". You should be able to run the script multiple times without it failing.

#!/bin/bash
# Set the main directory name
main_dir="sports"
# Check if the main directory already exists
if [ ! -d "$main_dir" ]; then
    # Create the main directory
    mkdir "$main_dir"
    echo "Created directory: $main_dir"
fi
# Create the subdirectories
subdirs=("football" "handball")
for subdir in "${subdirs[@]}"; do
    # Check if the subdirectory already exists
    if [ ! -d "$main_dir/$subdir" ]; then
    # Create the subdirectory inside the main directory
    mkdir "$main_dir/$subdir"
    echo "Created directory: $main_dir/$subdir"
  else
    echo "Directory already exists: $main_dir/$subdir"
  fi
done
exit

3. Copy the code below into a file called hello.sh and run it. Explain the behaviour.
```
#!/bin/bash
echo "You are using $(basename $0)"
for n in $*
do
    echo "Hello $n"
done
exit 0
```
4. Copy the script below into a file called addme.sh and analyse it line by line. Run it and describe in details the behavior.

```
#!/bin/bash
# (@)/ph
# A very simple telephone list
# Type "ph new name number" to add to the list, or
# just type "ph name" to get a phone number
PHONELIST=~/.phonelist.txt
# If no command line parameters ($#), there
# is a problem, so ask what they're talking about.
if [ $# -lt 1 ] ; then
    echo "Whose phone number did you want? "
    exit 1
fi
# Did you want to add a new phone number?
if [ $1 = "new" ] ; then
shift
    echo $* >> $PHONELIST
    echo $* added to database
exit 0
fi
# Nope. But does the file have anything in it yet?
# This might be our first time using it, after all.
if [ ! -s $PHONELIST ] ; then
    echo "No names in the phone list yet! "
    exit 1
else
    grep -i -q "$*" $PHONELIST # Quietly search the file
    if [ $? -ne 0 ] ; then # Did we find anything?
        echo "Sorry, that name was not found in the phone list"
        exit 1
    else
        grep -i "$*" $PHONELIST
    fi
fi
exit 0
```
5. Create a script that reads in three positional parameters from the command line,
assigns those parameters to variables names ONE, TWO, and THREE, respectively,
and then outputs that information in the following format:
There are X parameters that include Y. The first is A, the second is B, the third is C.
Replace X with the number of parameters and Y with all parameters entered.
Then replace A with the contents of variable ONE, B with variable TWO, and C
with variable THREE.

## CICD, Infrastructure as as Code (IaC), Terraform, Packer and Ansible

1. Read Chapter 1, page 1 - page 37 of the Terraform Up and Running book and with respect to your learning answer the following questions:

* What do you understand by the term Idempotence?

    Idempotence refers to the property of a system or operation where applying the same action multiple times produces the same result as applying it once. In other words, performing an idempotent operation multiple times has no additional effect beyond the initial operation.

* What are the benefits of adopting a DevOps way of working for an organisation?

When an organisation adopts the DevOps way of working, she experiences the following benefits:
    Increased number of features delivered for a given period, reduce defects, reduce lead times (the time from coming up with an idea to running code in production), reduce number of production incidents, reduced amount of time developers spent on developing new features, reduced  development cost and automation of the software delivery process as possible.

* What are the benefits of provisioning infrastructure using tools like Terraform and Ansible?

When Terraform and Ansible are used together, Terraform deploys all the underlying infrastructure and Ansible deploys apps on the servers offering benefits like: 
    -Infrastructure changes become repeatable and can be applied consistently across different environments.

    -Automation of infrastructure provisioning and configuration tasks, reducing manual effort and minimizing human error, improving efficiency, saving time, and enabling faster infrastructure deployments.

    -Provision and manage infrastructure across various cloud providers and on-premises environments.

    -Easily scale your infrastructure up or down by modifying the code or configuration. 

    -Fefine and enforce standard configurations, security policies, and compliance requirements, reducing configuration drift and maintaining a high level of reliability.

    -Facilitate collaboration among teams by allowing them to work together on the same infrastructure codebase promoting best practices and speeding up development cycles.

* Some provisioning and configuration management tools require the installation of agents on managed servers. Can you list the advantages and disadvantages of tools based on agents?

    Advantages of agent-based tools:
    I.	Richer control and monitoring: Agents provide a more comprehensive level of control and monitoring over the managed servers. 

    II.	Enhanced security: Agents can establish secure communication channels between the managed servers and the central management server.

    III. Offline capabilities: Agents can continue to operate even when the managed servers are disconnected from the central management server.

    IV.	Granular management: Agents allow fine-grained management and configuration of individual servers.

    V.	Reduced network traffic: Agents can optimize network utilization by transmitting only necessary data and updates between the managed servers and the central management server.

    Disadvantages of agent-based tools:
    I.	Additional resource consumption: Agents consume system resources (CPU, memory, disk space) on the managed servers. 

    II.	Installation and maintenance overhead: Agents need to be installed and maintained on each managed server, which adds an extra step to the provisioning and configuration process.

    III.	Compatibility concerns: Agents may have specific requirements or dependencies that need to be considered when deploying them on different server platforms or operating systems. 

    IV.	Security risks: The presence of agents on managed servers introduces potential security vulnerabilities. 

    V.	Agent management complexity: As the number of managed servers and agents grows, managing the agents themselves can become complex.


* Compare and contrast mutable and immutable infrastructures design paradigms.

    Mutable Infrastructure:
    a)	Definition: Mutable infrastructure refers to an approach where infrastructure components can be modified or updated directly in-place.

    b)	Modifiability: In a mutable infrastructure, changes can be made to existing infrastructure resources, such as servers, configurations, or applications, without necessarily rebuilding or recreating them.

    c)	Configuration drift: Due to the ability to modify infrastructure in-place, mutable infrastructures are prone to configuration drift, where inconsistencies or unintended changes can accumulate over time, leading to operational issues or increased complexity.

    d)	Maintenance and updates: Updating and patching a mutable infrastructure typically involves directly modifying the existing resources. This can be time-consuming, error-prone, and may require significant coordination and testing efforts.

    e)	Flexibility: Mutable infrastructures provide flexibility for immediate modifications and ad-hoc changes, making them suitable for environments with rapidly changing requirements or experimental setups.

    f)	Stateful nature: Mutable infrastructures often involve stateful components, where the configuration and data are stored within the infrastructure resources themselves. This can introduce complexities in scaling, replicating, and recovering from failures.

    Immutable Infrastructure:
    a)	Definition: Immutable infrastructure refers to an approach where infrastructure components are treated as disposable and are replaced entirely when changes are needed.

    b)	Immutability: In an immutable infrastructure, any updates or modifications are performed by creating new instances of the infrastructure components, rather than modifying the existing ones.

    c)	Consistency and reproducibility: Immutable infrastructures promote consistency and reproducibility since each instance of an infrastructure component is built from a known, predefined configuration or template.

    d)	Configuration management: Immutable infrastructures rely heavily on configuration management tools and declarative templates to define the desired state of the infrastructure. Changes are made by updating these templates and then creating new instances.

    e)	Scalability and resilience: Immutable infrastructures are well-suited for scaling and handling failures since new instances can be easily created and replace the ones that are no longer functioning properly.

    f)	Stateless design: Immutable infrastructures tend to favor stateless components, where the state and data are stored externally, such as in databases or object stores. This simplifies scaling, recovery, and replication.

* Name some commercial and enterprise tools and the circumstances under which you would recommend them.

    i.	Chef Automate: Chef is another popular configuration management tool that offers a comprehensive platform for infrastructure automation. Chef Automate provides capabilities for infrastructure configuration, application deployment, compliance, and continuous delivery. It is recommended for organizations looking for a flexible and scalable solution for managing their infrastructure and applications.

    ii.	HashiCorp Terraform: Terraform is an infrastructure-as-code (IaC) tool that enables provisioning and managing infrastructure resources across different cloud providers and platforms. It allows for declarative infrastructure configuration and automation. Terraform is recommended for organizations adopting infrastructure automation and seeking multi-cloud or hybrid cloud support.

    iii.	Docker: Docker is a containerization platform that allows packaging applications and their dependencies into portable containers. It enables consistent and isolated deployments across different environments. Docker is recommended for organizations aiming to achieve lightweight and scalable application deployments using containerization.

    iv.	Puppet: Puppet is a configuration management tool that enables automated deployment, configuration, and management of infrastructure and applications. It helps in maintaining infrastructure consistency and enables infrastructure-as-code practices. Puppet is recommended for organizations with complex and large-scale infrastructure environments.

    v.	Ansible: Ansible is an open-source automation tool that focuses on simplicity and agentless architecture. It provides a wide range of modules to automate infrastructure provisioning, configuration management, and application deployment. Ansible is recommended for organizations looking for a lightweight and easy-to-use automation tool.

* What do you understand by imperative and declarative way of provisioning infrastructure?

    Imperative provisioning involves specifying detailed instructions or steps that need to be executed to achieve the desired infrastructure state. That is, you explicitly define the sequence of actions or commands to be executed in order to set up the infrastructure. This approach focuses on specifying how the infrastructure should be provisioned step by step.

    while, Declarative provisioning involves specifying the desired end state of the infrastructure without explicitly defining the sequence of actions to achieve that state. Simply put, you define the desired configuration or state of the infrastructure, and the provisioning tool determines the necessary actions to achieve that state.

2. Describe the role that GitHub Actions plays in a fully automated CICD integrated toolchain?

GitHub Actions is a powerful workflow automation tool provided by GitHub that allows developers to define custom workflows and automate various tasks related to software development, testing, and deployment.
Below is how GitHub Actions fits into a fully automated CI/CD integrated toolchain:
    .	Continuous Integration (CI): GitHub Actions enables developers to set up CI workflows that automatically build, test, and validate code changes. Developers can define workflows triggered by events such as code pushes, pull requests, or scheduled intervals. Actions can be configured to run on different platforms and environments, ensuring consistent and reliable code integration.

    .	Automated Testing: With GitHub Actions, you can define workflows that automatically run tests on your codebase. This includes unit tests, integration tests, and any other custom tests you've set up for your project. Actions can be triggered whenever new code is pushed or when pull requests are opened, allowing for early detection of issues and ensuring the quality of your codebase.

    .	Code Quality Analysis: GitHub Actions can be used to integrate code quality analysis tools into your CI/CD pipeline. This includes static code analysis, code style checks, and code formatting tools. By adding these actions to your workflows, you can automatically enforce coding standards, detect potential issues, and maintain consistent code quality across your project.

    .	Continuous Deployment (CD): GitHub Actions simplifies the process of deploying your application or infrastructure. You can define deployment workflows that automatically package your application, provision necessary resources, and deploy it to your target environment. Actions can be configured to deploy to various platforms and cloud providers, allowing for seamless and reliable deployments.

    .	Release Management: GitHub Actions can automate the release process of your software. You can define workflows that automatically create release builds, generate changelogs, and publish artifacts to distribution platforms. This enables streamlined versioning and release management, ensuring that your software is delivered to end-users efficiently.

    .	Notifications and Alerts: GitHub Actions can be configured to send notifications and alerts based on specific events or conditions. For example, you can set up actions to send notifications to Slack or email when a workflow fails, a security vulnerability is detected, or a pull request is merged. This helps in monitoring the CI/CD pipeline and keeping stakeholders informed about the status of the software development process.

3. What is a Runner in the context of a provisioning pipeline?

    In the context of a provisioning pipeline, a "runner" refers to the execution environment responsible for running jobs or tasks defined in the pipeline. It is a component that facilitates the execution of workflows, tasks, and actions within a CI/CD system. In specific terms of GitHub Actions, a runner is a machine (physical or virtual) that has the GitHub Actions runner software installed. This runner software connects to GitHub and listens for events or triggers that initiate workflows. When a workflow is triggered, the runner pulls the workflow definition, including the necessary code, dependencies, and configurations, and executes the defined tasks or actions on the runner machine.

4. What GitHub Action code syntax would you implement to trigger a GitHub Action workflow upon a pull request on a codebase?

5. In the context of GitHub Actions, what are actions and where might you obtain them?

You can obtain GitHub actions from various sources:
    . GitHub Marketplace: The GitHub Marketplace is a centralized platform where you can discover, share, and use actions created by the GitHub community and organizations. It offers a wide range of pre-built actions that you can easily integrate into your workflows.

    . Public Repositories: Many individuals and organizations share their custom actions on public repositories hosted on GitHub. You can find actions by exploring repositories and searching for specific keywords or topics.

    . Private Repositories: Actions can also be created and used within private repositories. This allows organizations to develop custom actions tailored to their specific workflows and keep them private within their organization.

    . Create Your Own Actions: If you have specific requirements or need custom functionality, you can create your own actions. GitHub provides documentation on how to create actions using Docker containers or JavaScript functions. You can then use these custom actions within your workflows

## System Architecture and Application Design, Cloud Computing (AWS)

1. Draw a solution architecture diagram illustrating the flow of information in a provisioning pipeline comprising AWS, GitHub, your laptop, Terraform and Terraform state file stored in AWS.
2. You run a command on your local laptop to clone a public repository and then run another command to push the cloned repository to your own GitHub repository. Draw a solution architecture diagram to depict the flow of information.


## Site Reliability Engineering (SRE), Troubleshooting, Observability

1. You are asked by your manager to implement an automated system to collect metrics from your infrastructure by using a third party vendor's product. What steps might you take to ensure the system is not going to cause unwanted effects?  How might you check that?

I will follow the folling steps:
    a.	Research and Evaluation: Before implementing the third-party vendor's product, I would thoroughly research and evaluate its capabilities, reliability, and compatibility with the infrastructure. Look for customer reviews, case studies, and evaluate its track record in terms of stability and performance.

    b.	Testing Environment: Set up a separate testing environment where I can evaluate the vendor's product without affecting the production systems. 

    c.	Backup and Recovery: Implement a comprehensive backup and recovery strategy for the infrastructure to ensure proper backups of critical systems and data in case any issues arise during or after the implementation of the vendor's product.

    d.	Monitoring and Alerting: Implement robust monitoring and alerting systems to keep a close eye on the metrics collection process and its impact on the infrastructure. Set up alerts to notify of any unexpected spikes in resource usage, performance degradation, or other abnormal behavior.

    e.	Communication and Collaboration: Maintain open communication channels with the third-party vendor. Discuss the implementation plans, concerns, and expectations with their support or implementation team. Collaborate closely with them to address any potential issues or challenges.

    f.	User Training and Documentation: Provide comprehensive training to the individuals responsible for managing and monitoring the metrics collection system. Ensure that they understand the product's features, configuration options, and best practices for its usage. Document the setup process, configurations, and troubleshooting steps for future reference.

    g.	Ongoing Monitoring and Evaluation: Continuously monitor the system after implementation to detect any unwanted effects. Regularly evaluate the collected metrics, system performance, and user feedback to identify and address any issues promptly

2. Your manager asked you to run a script that is unfamiliar to you. How are you going to go about ensuring that this operation is done safely?

I will follow the folling steps to run the script:
    a)	Understand the Script's Source: Determine the source of the script and assess its trustworthiness. If it comes from a reputable and trusted source, it adds a level of confidence. Be cautious when dealing with scripts from unknown or untrusted sources, as they may contain malicious code.

    b)	Test in a Controlled Environment: Set up a controlled environment to run the script. Use a non-production system or isolated virtual environment to minimize the potential impact of the script. 

    c)	Take Backups: Before running the script, I would do a backup of relevant data and configurations. To restore the system to its previous state in case anything goes wrong.

    d)	Analyze Dependencies: Identify any dependencies required by the script, such as specific software versions, libraries, or system configurations. To make sure that the dependencies requirements are met to avoid potential compatibility issues or unexpected behavior.

    e)	Use Version Control: If the script is complex or likely to undergo modifications, I will use a version control systems like Git that allows me to track changes, revert to previous versions, and collaborate with others more effectively.

    f)	Run with Restricted Permissions: Execute the script with limited permissions. If possible, run it under a dedicated user account that has restricted access to sensitive resources or system components. 

    g)	Monitor and Observe: While running the script, I will closely monitor its execution and observe its behavior. Keep an eye on system resource usage, error messages, and any unusual activities to take prompt actions if need be. 

    h)	Analyze Output and Results: Once the script completes its execution, I will review the output and results. Check for any errors, warnings, or discrepancies that might indicate issues or unexpected behavior.

    i)	Seek Expert Advice: If you are unsure about any aspect of the script or its execution, consult with subject matter experts, colleagues, or community forums. They can provide insights, recommendations, or guidance to ensure the safe execution of the script.

## DevOps and Agile Transformation principles and methodology

1. Read the blog article given in Reference 1 (Become A DevOps Engineer in 2023: A Comprehensive Guide) and answer the following question. According to the author, what are the key technologies, tools and systems an aspiring DevOps should learn?

DevOps engineers should: 
    •	Have a strong understanding and working knowledge of variousLinux/Unix systems like: RHEL, Centos, Ubuntu, and CoreOS. 

    •	Learn how to use tools like VirtualBox and Vagrant or cloud services like AWS, GCP, or Azure as well as Cloud computing and 
    virtualization. 

    •	learn about test-driven infrastructure development and testing tools such as Ansible-test and terratest. 

    •	Understand Distributed systems like Kubernetes and Container technology, such as Docker or podman, Docker Swarm and mesh tools.

    •	Learn Security Best Practices (DevSecOps) and commonly used scripting languages such as Bash/Shell, Python, and Golang and programming and APIs.

    •	Learn Git, GitOps document their work and understand application development and release lifecycle

2. Read the blog article given in Reference 4 "How to find Remote DevOps Full time Gigs". To what extend do you agree or disagree with the main argument of the article?
2. XXXX
## New commands logs - Enter up to ten new commands you have learnt this week

| Number      | Commands | What does it do and how might you check its effect     |
| :---        |    :----:   | :---  |
| 1  | ping	      |  Sends network requests to a specific IP address or domain |
| 2  | Kill       | Sends a signal to terminate a process   |
| 3  | ps         |  Lists currently running processes|
| 4  | curl	      |  Transfers data from or to a server using various protocols   |
| 5  | top	      |  Displays real-time system resource usage  |
| 6  |wget	      |  Downloads files from the web using HTTP, HTTPS, or FTP |
| 7  |grep	      |  Searches for patterns in files. |
| 8  | gzip	      |  Compresses files |
| 9  | unzip	  |  Extracts files from a ZIP archive.  |
| 10 | chmod	  |  Changes file permissions. |

## Glossary of the week - Enter new technical words you have learnt this week and their meanings.

| Number   | Word | Meaning     |
| :---     | :----:   |  :---  |
| 1  |Idempotence |  the property of a system or operation where applying the same action multiple times produces the same result as applying it once. |
| 2  | fine-grained |  In the context of configuration management, refers to a level of detail or granularity in managing and controlling the configuration of a system or software  |
| 3  | Configuration management | It is the process of managing and controlling the configuration of a system or software application throughout its lifecycle.  |
| 4  |  "fork" | It refers to creating a copy of a repository owned by another user or organization on GitHub.   |
| 5  | Pod | A group of containers is known as a pod
| 6  | AMI | An Amazon Machine Image (AMI) is a supported and maintained image provided by AWS that provides the information required to launch an instance.   |
| 7  | GitOps   |It is an operational framework that takes DevOps best practices used for application development such as version control, collaboration, compliance, and CI/CD, and applies them to infrastructure automation   |



## Reference

1. Become A DevOps Engineer in 2023: A Comprehensive Guide
https://blog.brainboard.co/become-a-devops-engineer-in-2023-a-comprehensive-guide-db3f614e4051

2. Terraform Up and Running.

3. Kubernetes Patterns

4. How to find Remote DevOps Full time Gigs https://sharonsahadevan.medium.com/learn-how-i-found-remote-devops-jobs-from-my-perspective-382c15514cd5

