# Scaled-Up Web Infrastructure for www.foobar.com

## Infrastructure Diagram

![Alt text](./3-scale_up.png)

## Infrastructure Components

### 1. Servers (3)

Three separate servers, each dedicated to a specific component: web server, application server, and database.

### 2. Load Balancer (HAproxy)

Configured as a cluster with another load balancer for high availability and to distribute incoming traffic.

### 3. Web Server

Dedicated server running Nginx to handle HTTP requests and serve static content.

### 4. Application Server

Dedicated server to run the application code and process dynamic content requests.

### 5. Database Server

Dedicated server running MySQL to store and manage the website's data.

## User Access Flow

Imagine a user wants to access the website <www.foobar.com>. Here's what happens:

    - The user types [www.foobar.com](http://www.foobar.com) into their web browser.
    - The user's computer sends a DNS query to resolve [www.foobar.com](http://www.foobar.com).
    - The DNS server returns the IP address of the load balancer.
    - The user's browser sends an HTTPS request to the load balancer's IP address.
    - The load balancer distributes the request to one of the five servers.
    - The web server (Nginx) on the selected server receives the request.
    - Nginx processes the request, potentially passing it to the application server.
    - The application server executes the necessary code, possibly interacting with the MySQL database.
    - The server sends back an HTTPS response to the user's browser via the load balancer.
    - The user's browser renders the received web page.

## Specifics of the Infrastructure

### Additional Server

Added to separate concerns and allow for independent scaling of components. This improves performance and maintainability.

### Load Balancer (HAproxy)

Added to distribute traffic evenly across servers, improve reliability, and enable horizontal scaling. Configured as a cluster for high availability.

### Split Components

Web server, application server, and database each have their own server. This allows for:

- Independent scaling based on specific needs
- Improved security through isolation
- Better resource allocation and performance optimization
- Easier maintenance and updates
