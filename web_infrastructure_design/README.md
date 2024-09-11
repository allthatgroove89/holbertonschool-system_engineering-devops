# Web Infrastructure Design

## Learning Objectives

At the end of this project, you should be able to explain the following concepts to anyone, without the help of Google:

### General

- Draw a diagram covering the web stack you built with the sysadmin/devops track projects.
- Explain what each component is doing.
- Explain system redundancy.
- Understand all the mentioned acronyms: **LAMP, SPOF, QPS**.

## Requirements

- A `README.md` file at the root of the folder of the project is mandatory.
- For each task, once you have completed whiteboarding (on a whiteboard, piece of paper, or software of your choice), take a picture or screenshot of your diagram.
- This project will be manually reviewed:
  - As each task is completed, the name of that task will turn green.
  - Upload a screenshot showing that you completed the required levels to any image hosting service (such as Imgur).
  - For the following tasks, insert the link of your screenshot into the answer file.
  - After pushing your answer file to GitHub, insert the GitHub file link into the URL box.
  - You will also have to whiteboard each task in front of a mentor, staff, or student - no computer or notes will be allowed during the whiteboarding session.
- Focus on what you are being asked:
  - Cover what the requirements mention; details will be explored in a later project.
  - Keep in mind that you will have 30 minutes to perform the exercise; you will get points for fulfilling the requirements.
  - Similar to a job interview, answer what the interviewer asks for; avoid being too verbose - always ask if going into details is necessary.
  - In this project, again, avoid going into details if not asked.

## Tasks

### 0. Simple Web Stack

Design a simple web infrastructure with a single server that hosts the website reachable via <www.foobar.com>. Start your explanation by describing a user accessing your website.

#### Requirements:

- **Use**:
  - 1 server
  - 1 web server (Nginx)
  - 1 application server
  - 1 application files (your code base)
  - 1 database (MySQL)
  - 1 domain name **foobar.com** configured with a **www** record pointing to your server IP **8.8.8.8**
- **Explain**:
  - What is a server
  - The role of the domain name
  - What type of DNS record **www** is in <www.foobar.com>
  - The role of the web server
  - The role of the application server
  - The role of the database
  - How the server communicates with the user’s computer
- **Explain the issues with this infrastructure**:
  - **SPOF** (Single Point of Failure)
  - Downtime during maintenance (e.g., when deploying new code, the web server needs to be restarted)
  - Cannot scale with high traffic

**Repository:**

- GitHub repository: `holbertonschool-system_engineering-devops`
- Directory: `web_infrastructure_design`
- File: `0-simple_web_stack`

---

### 1. Distributed Web Infrastructure

Design a three-server web infrastructure that hosts the website <www.foobar.com>.

#### Requirements:

- **Add**:
  - 2 servers
  - 1 web server (Nginx)
  - 1 application server
  - 1 load balancer (HAProxy)
  - 1 set of application files (your code base)
  - 1 database (MySQL)
- **Explain**:
  - For every additional element, why you are adding it
  - The distribution algorithm your load balancer is configured with and how it works
  - Whether your load balancer enables an Active-Active or Active-Passive setup and the difference between both
  - How a database Primary-Replica (Master-Slave) cluster works
  - The difference between the Primary node and the Replica node regarding the application
- **Explain the issues with this infrastructure**:
  - **SPOF** (Single Point of Failure) locations
  - Security issues (e.g., no firewall, no HTTPS)
  - No monitoring

**Repository:**

- GitHub repository: `holbertonschool-system_engineering-devops`
- Directory: `web_infrastructure_design`
- File: `1-distributed_web_infrastructure`

---

### 2. Secured and Monitored Web Infrastructure

Design a three-server web infrastructure that hosts the website <www.foobar.com>. It must be secured, serve encrypted traffic, and be monitored.

#### Requirements:

- **Add**:
  - 3 firewalls
  - 1 SSL certificate to serve <www.foobar.com> over HTTPS
  - 3 monitoring clients (data collectors for Sumologic or other monitoring services)
- **Explain**:
  - For every additional element, why you are adding it
  - The purpose of firewalls
  - Why traffic is served over HTTPS
  - The purpose of monitoring
  - How the monitoring tool collects data
  - How to monitor your web server's QPS (Queries Per Second)
- **Explain the issues with this infrastructure**:
  - Why terminating SSL at the load balancer level is an issue
  - Why having only one MySQL server capable of accepting writes is an issue
  - Why having servers with all the same components (database, web server, and application server) might be a problem

**Repository:**

- GitHub repository: `holbertonschool-system_engineering-devops`
- Directory: `web_infrastructure_design`
- File: `2-secured_and_monitored_web_infrastructure`

### 3. Scale Up

Understand the difference between an **Application Server** and a **Web Server**.

#### Requirements:

- **Add**:
  - 1 additional server
  - 1 load balancer (HAProxy) configured as a cluster with the existing load balancer
  - Split components:
    - Each component (web server, application server, database) should be on its own dedicated server.
- **Explain**:
  - For every additional element, why you are adding it.
- **Explanation of the Infrastructure**:
  - Application Server vs Web Server**:
    - Understand the distinct roles and responsibilities of an application server and a web server.
  - New Components**:
    - Additional Server: Explain the need for an extra server to handle increased load or redundancy.
    - Load Balancer (HAProxy) Cluster Configuration**: Describe how clustering the load balancers provides redundancy and ensures high availability.
    - Separated Components:
      - Detail the benefits of having the web server, application server, and database on their own dedicated servers, such as improved performance, scalability, and fault isolation.

**Repository:**

- GitHub repository: `holbertonschool-system_engineering-devops`
- Directory: `web_infrastructure_design`
- File: `3-scale_up`