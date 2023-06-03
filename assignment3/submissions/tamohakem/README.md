## My name is tamohakem Outcomer and please file below my submission
## Kubernetes, Docker, Containerisation and Virtualisation

1. What is a hypervisor and where does it sit in the server virtualisation stack?

A hypervisor, also known as a virtual machine monitor or VMM, is software that creates and runs virtual machines (VMs). A hypervisor allows one host computer to support multiple guest VMs by virtually sharing its resources, such as memory and processing. 
There are 2 different types of hypervisors that can be used for virtualization: type 1 and type 2 hypervisors.
Type 1

A type 1 hypervisor, also referred to as a native or bare metal hypervisor, runs directly on the host’s hardware to manage guest operating systems. It takes the place of a host operating system and VM resources are scheduled directly to the hardware by the hypervisor. 

Examples are: KVM, Microsoft Hyper-V, and VMware vSphere  
Type 2

A type 2 hypervisor is also known as a hosted hypervisor, and is run on a conventional operating system as a software layer or application.

It works by abstracting guest operating systems from the host operating system. A type 2 hypervisor is better for individual users who want to run multiple operating systems on a personal computer. 

Examples of a type 2 hypervisors are: VMware Workstation and Oracle VirtualBox . 

2. What is a container runtime and name the two most common runtimes?

A container runtime is a software component responsible for running and managing containers on a host system. It provides an environment for containers to execute and handles various container-related operations such as starting, stopping, pausing, and managing container resources.
The two most common container runtimes are:

a.Docker: Docker is one of the most popular container runtimes. It simplifies the containerization process by providing an easy-to-use interface and a comprehensive set of tools. Docker uses the Docker Engine as its container runtime, which leverages technologies like namespaces, control groups, and union file systems to isolate and manage containers.

b.Containerd: Containerd is an open-source container runtime developed under the auspices of the Cloud Native Computing Foundation (CNCF). It focuses on providing a minimalistic and stable runtime for container execution, emphasizing compatibility and extensibility.


## Linux administration and shell scripting
1. Use just one command to create a directory structure where the directory sports contains a directory called footballteams which itself contains africanteam which itself contains pwdkumba.

mkdir -p sports/footballteams/africanteam/pwdkumba

2. Use the tree command to display your directory structure.
3. Research the following linux commands
    a) grep
    b) sed
    c) awk
    
    a) grep: The grep command is a powerful utility in Unix-like operating systems that allows you to search for specific patterns or regular expressions within files or streams of text. It stands for "Global Regular Expression Print." The basic syntax of the grep command is: grep [options] pattern [file(s)]

    b) sed :  The sed command, short for "stream editor," is a powerful text processing tool in Unix-like operating systems. It allows you to perform various operations on text files or streams, such as search and replace, insert or delete lines, and more. sed reads input line by line, applies specified commands to each line, and outputs the result. The basic syntax of the sed command is: sed [options] 'command' [file(s)]

    c) awk : The awk command is a Linux tool and programming language that allows users to process and manipulate data and produce formatted reports. The tool supports various operations for advanced text processing and facilitates expressing complex data selections. The syntax for the awk command is: awk [options] 'selection_criteria {action}' input-file > output-file


## CICD, Git, GitHub, GitHub Action, Infrastructure as as Code (IaC), Terraform, Packer and Ansible
1. You create a repository in GitHub called <b>myfirstrepo</b>. You then clone this repository on your local laptop. On your laptop how would you check its remote address? How would you go about changing the remote address so that it points to repository called <b>mysecondrepo</b>?

To check the remote address of <b>myfirstrepo</b>, I will run the command :
 git remote -v

 And to change the remote address to point to <b>mysecondrepo</b>, I will run the command: 
 git remote set-url --add --push origin URL/mysecondrepo

2. You have a workflow running on GitHub Action that has the following code;
```
jobs:
  deploy_to_production:
    runs-on: ubuntu-latest
    name: deploy to production with soruce code
    steps:
      - name: Checkout GitHub Action
        uses: actions/checkout@v2

      - name: Login via Azure CLI
        uses: azure/login@v1
        with:
          creds: ${{ secrets.AZURE_CREDENTIALS }}

      - name: deploy to production step with soruce code
        uses: azure/spring-cloud-deploy@v1
        with:
          azure-subscription: ${{ env.AZURE_SUBSCRIPTION }}
          action: deploy
          service-name: <service instance name>
          app-name: <app name>
          use-staging-deployment: false
          package: ${{ env.ASC_PACKAGE_PATH }}
```
Describe what you think this code is doing.

This code used to deploy a production code on Azure using GitHub Actions  to run on Ubuntu-latest version


## System Architecture and Application Design, Cloud Computing (AWS)
1. You have worked thus far with systems that you have had to download and install on your local laptop as well as systems hosted remotely on some external cloud. Describe in details the features and capabilities of all the systems (local and remote) that you have worked with thus far on this training. Draw a solution architecture diagram depicting these systems and where they fit in your solution landscape.
2. For all the systems that you have installed locally, write a manual for its installation and configuration.
3. In a general manner describe would you would interact with AWS account

Interacting with an AWS (Amazon Web Services) account typically involves several steps and tools. Here's a general description of how we can interact with an AWS account:

a. Create an AWS Account: Visit the AWS website (https://aws.amazon.com/) and sign up for a new AWS account. You'll need to provide your personal or organizational details and payment information.

b. AWS Management Console: After creating an account, you can access the AWS Management Console, which is a web-based interface for managing your AWS resources. The console provides a user-friendly interface for various AWS services.

c. IAM (Identity and Access Management): IAM allows you to manage access to your AWS resources. You can create IAM users, groups, and roles with specific permissions. It's recommended to set up IAM users and avoid using the root account for day-to-day operations.

d. AWS CLI (Command Line Interface): The AWS CLI is a command-line tool that allows you to interact with AWS services through the command line. You can install the AWS CLI on your local machine, configure it with your AWS credentials, and use it to manage your AWS resources programmatically.

e. AWS SDKs: AWS provides software development kits (SDKs) for various programming languages. These SDKs enable you to interact with AWS services programmatically from your applications. You can integrate the SDKs into your code and use them to perform actions such as creating, managing, and deleting AWS resources.

f. AWS Services: AWS offers a vast range of services, including compute, storage, databases, networking, security, machine learning, and more. To interact with these services, you can use the AWS Management Console, AWS CLI, or SDKs. Each service has its own set of APIs and tools for management and configuration.

g. Infrastructure as Code (IaC): AWS provides services like AWS CloudFormation and AWS CDK (Cloud Development Kit) that allow you to define your infrastructure as code. These services enable you to create and manage AWS resources using templates or code, which can be version-controlled, reviewed, and deployed programmatically.

h. Monitoring and Management: AWS provides services like Amazon CloudWatch, AWS Config, and AWS Systems Manager that help you monitor your resources, track performance metrics, set up alarms, and perform automated management tasks. These services allow you to gain insights into your AWS environment and efficiently manage your resources.


4. AWS provide a public and a private area in which you could deploy your services. In which of these would you deploy the following services?
    a) EC2 instances
    b) DynamoDB databases
    c) VPC network
    d) S3 buckets
    e) IAM users

Here's a tabular representation of where you would typically deploy the mentioned services in AWS:
| Service      | Public area | Private Area    |
| :---        |    :----:   | :---  |
|EC2 instances|	x|  x	|
|DynamoDB databases|    |	x|
|VPC network	|    |	x|
|S3 buckets	|x| x	|
|IAM users		|     |	x|

EC2 instances: EC2 instances can be deployed in either the public or private area of your AWS account, depending on your requirements. Public EC2 instances have public IP addresses and are accessible over the internet. Private EC2 instances reside in a private subnet within a VPC and are not directly accessible from the internet.

DynamoDB databases: DynamoDB databases are typically deployed in the private area of your AWS account. These databases are not directly accessed from the internet but are accessible by the resources within your private VPC network.

VPC network: VPC (Virtual Private Cloud) networks are deployed in the private area of your AWS account. VPCs provide a logically isolated virtual network environment where you can launch your AWS resources. It allows you to define your IP address range, subnets, routing tables, network gateways, and other networking components.

S3 buckets: S3 (Simple Storage Service) buckets can be deployed in both the public and private areas of your AWS account. By default, S3 buckets have private access and are not accessible from the internet. However, you can configure bucket policies and access control to make certain S3 buckets publicly accessible.

IAM users: IAM (Identity and Access Management) users are not directly deployed as services but are created within the AWS account's identity management system. IAM users are typically managed in the private area of your AWS account. They are used to control access to AWS services and resources for individuals or entities within your organization.


## Site Reliability Engineering (SRE), Troubleshooting, Observability

1. Research on what APM (application programming monitoring)

APM, or Application Performance Monitoring, is a set of practices and tools used to monitor and manage the performance and availability of software applications. It involves tracking and analyzing various metrics and indicators to gain insights into the behavior and health of an application.

APM tools collect data from different sources, including application logs, performance counters, and network traffic, to provide visibility into the application's performance. Some common metrics monitored by APM tools include response time, throughput, error rates, resource utilization (CPU, memory, disk, etc.), and transaction traces.

By monitoring these metrics, APM helps identify performance bottlenecks, diagnose issues, and optimize application performance. It can help developers and operations teams understand how an application is behaving in real-time, detect and troubleshoot problems, and ultimately improve the overall user experience.

APM typically offers features such as:

Performance monitoring: Tracking and analyzing various performance metrics to identify slow response times, high resource consumption, or other issues impacting the application's performance.

Error monitoring: Capturing and alerting on application errors, exceptions, and crashes to help identify and resolve bugs or stability issues.

Transaction tracing: Capturing and visualizing end-to-end traces of individual requests or transactions as they move through various components of the application, helping to identify bottlenecks and performance issues.

Real-time analytics and dashboards: Displaying performance data in real-time, often through visual dashboards, to provide a quick overview of application health and performance trends.

Alerting and notifications: Generating alerts or notifications based on predefined thresholds or anomalies to proactively notify developers or operations teams about performance issues.

Diagnostics and troubleshooting: Providing tools and insights to help diagnose performance problems, investigate root causes, and optimize application behavior.

There are several popular APM (Application Performance Monitoring) tools available in the market that offer various features and capabilities to monitor and optimize the performance of software applications. Here are some widely used APM tools:

New Relic: New Relic provides end-to-end visibility into the performance of applications and infrastructure. It offers features like real-time monitoring, transaction tracing, error detection, and analytics. It supports multiple programming languages and has a user-friendly interface.

Dynatrace: Dynatrace is an AI-powered APM tool that offers automated monitoring and performance management capabilities. It provides deep visibility into application performance, user experience, and infrastructure monitoring. It also includes advanced features like AI-powered root cause analysis and real user monitoring.

AppDynamics: AppDynamics provides application performance monitoring, user monitoring, and business performance monitoring. It offers code-level diagnostics, real-time analytics, and business impact analysis. It supports multiple programming languages and provides insights into application performance across various platforms.

Datadog: Datadog is a monitoring and analytics platform that offers APM capabilities. It provides end-to-end visibility into applications, infrastructure, and logs. It supports various programming languages, offers distributed tracing, and integrates with other monitoring tools.

Elastic APM: Elastic APM is part of the Elastic Stack, which includes Elasticsearch, Logstash, and Kibana. It provides real-time application performance monitoring and distributed tracing. It supports multiple programming languages and integrates well with other Elastic Stack components.

Splunk: Splunk offers a comprehensive monitoring and analytics platform that includes APM functionality. It provides real-time monitoring, troubleshooting, and alerting capabilities. Splunk APM supports multiple programming languages and provides insights into application performance and dependencies.

These are just a few examples of APM tools available in the market. Each tool has its own unique features, strengths, and pricing models. The choice of an APM tool depends on specific requirements, budget, and the technology stack being used in the application. It's important to evaluate different tools and select the one that best aligns with your needs.


2. What is a system metric and why might it be useful to collect metrics?

A system metric refers to a quantifiable measurement or data point that represents the behavior, performance, or utilization of a computer system or its components. These metrics provide insights into the system's health, efficiency, and overall performance.

Collecting system metrics is useful for several reasons:

Performance Monitoring: Metrics help monitor and track the performance of a system, such as CPU usage, memory utilization, network throughput, disk I/O, and response times. By collecting and analyzing these metrics over time, you can identify trends, detect performance bottlenecks, and proactively optimize system resources.

Capacity Planning: Metrics provide information about resource usage and demand patterns. By analyzing historical metrics and forecasting future trends, you can plan and allocate resources effectively, ensuring the system can handle current and future workloads without degradation in performance.

Troubleshooting and Diagnostics: When a system issue arises, metrics can be invaluable for diagnosing and troubleshooting problems. By analyzing metrics related to system performance, error rates, or resource consumption, you can identify the root cause of issues and take appropriate actions to resolve them.

Anomaly Detection: Metrics can help detect anomalies or deviations from normal behavior. By setting thresholds or using machine learning techniques, you can monitor metrics in real-time and receive alerts when abnormal behavior occurs. This enables you to respond quickly to critical events or performance degradations.

Benchmarking and Comparison: Collecting metrics allows you to establish baselines and benchmarks for system performance. These benchmarks can be used to compare different configurations, hardware upgrades, software changes, or system optimizations. By comparing metrics before and after changes, you can assess the impact and effectiveness of modifications.

Decision Making and Optimization: Metrics provide data-driven insights that support decision making. By analyzing metrics, you can identify areas for improvement, optimize resource utilization, fine-tune system configurations, and prioritize performance optimization efforts.

Overall, collecting system metrics provides visibility into the inner workings of a computer system, enabling informed decision making, proactive performance management, and efficient troubleshooting. By leveraging these metrics, organizations can improve system reliability, optimize resource usage, and enhance the overall user experience.


3. What is an system log and why might you want to collect logs?

A system log, often referred to as a log file or log data, is a record of events, activities, or messages generated by a computer system, software application, or network device. System logs capture important information about the system's operation, behavior, errors, and security events.

Collecting logs is valuable for several reasons:

Troubleshooting and Debugging: Logs serve as a valuable source of information when diagnosing and troubleshooting issues. By examining logs, you can gain insights into the sequence of events leading up to an error or unexpected behavior. Logs often contain error messages, stack traces, and timestamps, which can help identify the root cause of a problem and guide the debugging process.

System Monitoring and Performance Analysis: Logs provide a detailed view of system performance and behavior. By collecting and analyzing logs, you can monitor system metrics, resource utilization, and application-specific events. This helps identify performance bottlenecks, detect anomalies, and optimize system performance.

Security and Compliance: Logs play a crucial role in security monitoring and compliance. They capture information about security events, access attempts, authentication failures, and other suspicious activities. By analyzing logs, you can detect security breaches, identify patterns of malicious behavior, and ensure compliance with regulatory requirements.

Auditing and Forensics: Logs serve as an audit trail of system activities. They provide a historical record of events and actions taken within a system, allowing for retrospective analysis, investigations, and forensics. Logs can be useful for reconstructing incidents, tracking user actions, or demonstrating compliance with policies and regulations.

Capacity Planning and Trend Analysis: Logs contain information about resource utilization, application usage patterns, and system performance over time. By collecting and analyzing logs, you can identify trends, forecast future resource requirements, and perform capacity planning to ensure optimal system performance.

Performance Optimization and Continuous Improvement: Logs can help identify areas for optimization and improvement. By analyzing performance-related logs, you can identify inefficiencies, bottlenecks, or areas of suboptimal performance. This information can be used to fine-tune configurations, optimize code, or make infrastructure changes to enhance overall system performance.

Collecting system logs provides a comprehensive record of system behavior, errors, security events, and performance metrics. Logs serve as a valuable resource for troubleshooting, monitoring, security analysis, compliance, and continuous improvement of computer systems and applications.


## DevOps and Agile Transformation principles and methodology

1. Communication, Collaboration and Automation and key aspects of a successful DevOps implementation. Describe why these traits are important in a DevOps transformation process.

Communication, collaboration, and automation are crucial elements in a successful DevOps implementation. They play significant roles in facilitating efficient processes, enhancing productivity, and promoting a culture of continuous improvement. Let's delve into the importance of each of these traits in a DevOps transformation process:

Communication: Effective communication is fundamental in DevOps as it ensures that all stakeholders, including developers, operations teams, and business units, are aligned and working towards common goals. It helps in breaking down silos and fostering collaboration, enabling teams to understand each other's requirements, challenges, and perspectives.

In a DevOps transformation, communication facilitates the sharing of information and feedback, enabling teams to iterate and improve rapidly. It also helps in identifying and addressing bottlenecks, resolving issues, and maintaining transparency throughout the development and deployment lifecycle. Open and transparent communication channels contribute to a culture of trust, accountability, and collective responsibility.

Collaboration: Collaboration is the cornerstone of DevOps. By bringing together cross-functional teams, such as developers, operations personnel, quality assurance engineers, and security experts, DevOps breaks down traditional barriers and encourages a culture of shared ownership and collective responsibility.

Collaborative practices, such as cross-team planning, pair programming, and shared documentation, enable teams to leverage each other's strengths and skills, leading to faster and more reliable software delivery. It fosters a culture of learning, innovation, and continuous improvement, as teams can learn from each other, share best practices, and collectively solve complex problems.

Through collaboration, teams can also ensure that development and operations activities are synchronized, enabling faster feedback loops, early bug detection, and proactive identification of performance and scalability issues.

Automation: Automation is a key enabler of DevOps, allowing teams to streamline and accelerate various tasks and processes. By automating repetitive and manual activities, such as build, testing, deployment, and infrastructure provisioning, DevOps teams can reduce errors, increase efficiency, and improve overall productivity.

Automation eliminates the need for manual intervention, reducing human errors and freeing up valuable time for more strategic and creative tasks. It enables faster and more frequent releases, ensuring that software is delivered to users promptly, which is essential in today's fast-paced market.

Additionally, automation promotes consistency and repeatability, as processes are defined as code and can be easily reproduced across different environments. This reduces configuration drift and enhances the reliability and stability of deployments.

Furthermore, automation plays a critical role in monitoring and observability, providing real-time insights into the performance and health of the software and infrastructure. This facilitates proactive issue detection, rapid incident response, and continuous optimization.

Communication, collaboration, and automation are integral to a successful DevOps transformation. They foster a culture of shared responsibility, effective coordination, and continuous improvement. By leveraging these traits, organizations can achieve faster time-to-market, improved quality, enhanced team morale, and ultimately, deliver value to their customers more efficiently.


2. You work for an organisation that is very keen to <b> make their work visible</b> across the organisation. What do you understand by this and how would you suggest they go about it?

When an organization aims to "make their work visible" across the organization, it means they want to improve transparency and increase awareness of the work being done by teams or individuals. It involves sharing information, progress, and results with relevant stakeholders, such as team members, managers, executives, and other departments, to foster a culture of openness and collaboration. Here are some suggestions on how to achieve this:

Utilize project management and collaboration tools: Implement project management and collaboration tools that provide visibility into tasks, milestones, and progress. Tools like Jira, Trello, Asana, or Microsoft Project can help teams organize their work, track progress, and make it easily accessible to others. These tools often offer features like dashboards, Kanban boards, or Gantt charts to visualize project status and share updates with stakeholders.

Establish regular reporting and status updates: Encourage teams to provide regular updates on their work. This can be done through status reports, weekly/monthly team meetings, or email summaries. These updates should highlight key accomplishments, ongoing tasks, and any obstacles or dependencies that might impact progress. Sharing this information regularly keeps everyone informed about the current state of projects and helps identify areas where support or coordination is needed.

Embrace visual management techniques: Visual management techniques, such as information radiators, can be used to make work visible. Physical or digital boards, like Kanban boards or task boards, can be set up in common areas or shared electronically, displaying the status of various tasks or projects. These visual representations enable quick and easy understanding of work progress, bottlenecks, and priorities.

Foster a culture of knowledge sharing: Encourage teams to share their knowledge, experiences, and learnings with others. This can be done through internal wikis, knowledge bases, or collaborative documentation platforms. By documenting processes, best practices, and lessons learned, teams can make their work visible to others, enabling cross-team learning and avoiding reinventing the wheel.

Conduct regular showcases or demos: Organize periodic showcases or demos where teams can present their work to stakeholders. This could include sharing completed features, prototypes, or successful outcomes. These showcases not only make work visible but also provide an opportunity to gather feedback, generate new ideas, and celebrate achievements.

Promote cross-team collaboration and communication: Encourage collaboration and communication across teams and departments. Foster an environment where individuals feel comfortable seeking and providing help or insights from/to others. Tools like Slack, Microsoft Teams, or other collaboration platforms can facilitate real-time communication and foster knowledge exchange.

Encourage peer reviews and feedback: Implement a culture of peer reviews and feedback to promote continuous improvement and accountability. Encourage team members to review each other's work, provide constructive feedback, and share insights. This ensures that work is not only visible but also subject to scrutiny and improvement, enhancing the quality and alignment of outcomes.

By implementing these strategies, an organization can enhance visibility of work across teams, foster collaboration, and enable better decision-making. Making work visible promotes transparency, accountability, and a shared understanding of progress, leading to improved efficiency, reduced duplication of efforts, and increased organizational alignment.


## New commands logs - Enter up to ten new commands you have learnt this week

| Number      | Commands | What does it do and how might you check its effect     |
| :---        |    :----:   | :---  |
| 1  | ssh       | Connects to a remote server using SSH protocol   |
| 2  | rm -rf       | Used to forcefully remove files and directories, including their subdirectories and contents   |
| 3  | mkdir -p       | used to create directories in Linux. The -p option allows you to create parent directories as needed.   |
| 4  | cat -b       |  This is used to concatenate and display files on the terminal by adding line numbers to non-blank lines   |
| 5  | cat -s       |  This is used to concatenate and display files on the terminal by squeezing blank lines into one line   |
| 6  | Grep       | This command searches for a particular string/ word in a text file.   |
| 7  | Ping        |  This command will ping a host remote server to check if it is responding   |
| 8  | History       | This command is used to view the previously executed command.    |
| 9  | free       |  This command is used to display memory usage statistics.   |
| 10 | ls       | List directories and files in a directory.   |


## Glossary of the week - Enter new technical words you have learnt this week and their meanings.

| Number   | Word | Meaning     |
| :---     | :----:   |  :---  |
| 1  | Cloud agnostic       | means being able to seamlessly run on any cloud platform (private or public).   |
| 2  |  Kanban Boards       | The Kanban board is a tool for workflow visualization, designed to help you bring clarity to your work process and enhance efficiency by limiting work in progress (WIP).   |
| 3  | Providers       |  Providers are plugins for Terraform that are designed to interface with external APIs.   |
| 4  | Branching       | Branching occurs when an object under review in source control is duplicated so that other developers can work on it concurrently.   |
| 5  | Lead Time       | The average amount of time needed for one feature request to make it through the entire development cycle from concept to delivery.   |
| 6  | Build Agent       | A type of agent that sends and receives messages about handling software builds.   |
| 7  | Ephemeral infrastructure       | computing resources that are temporarily created and destroyed on demand, often in the context of cloud computing to support short-term or variable workloads and are not intended to be used for long-term storage or persistent data.   |
| 8  |  Production       |It is an environment where the application or feature is accessible to users.   |
| 9  | Blue/Green deployments       | methodology for releasing new code into the production environment whose purpose is to reduce software downtime, make it easy to roll back new changes, and avoid service interruptions to applications with critical up-time requirements.   |
| 10 | Cluster       |  A set of connected computers that work together to enable load balancing, auto scaling and high availability.   |

