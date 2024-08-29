---
title: 1. Introduction
category: 9. AWS Lambda
order: 1
---
![AWS Lambda logo]({{ site.baseurl }}/images/awslambda_logo.png)
<h2>Contents</h2>
* toc
{:toc}
## Serverless Computing
Until now, we saw solutions where we deploy servers that host our application.  
Deploying a server require to allocate resources like CPU, RAM, storage, and bandwidth to run your application and handle its traffic. Hosting a server requires to keep particular attention to:
1. Cost: you pay for the resources that you have allocated for your server, regardless of how much you use them. This can lead to overprovisioning (i.e., underutilisation), resulting in unnecessary costs.
2. Scalability: Scaling up (adding more resources) or scaling down (reducing resources) can be challenging and may require significant effort, such as migrating to a larger server or splitting the application across multiple servers.
3. Maintenance: You are responsible for maintaining the server, including hardware upkeep, software updates, security patches, and monitoring for uptime.
4. Performance: The performance of your application is directly tied to the server resources. If you allocate fewer resources than required to handle the expected workload, your server may suffer from underprovisioning. This could lead to server overlead and crashes.

Serverless computing is a cloud computing execution model where the cloud provider automatically manages the infrastructure required to run your application. In a serverless model, you don't have to worry about allocating CPU, RAM, storage, or bandwidth. Instead, the cloud provider dynamically allocates these resources as needed, based on the actual demand of your application.

## AWS Lambda
AWS Lambda is a serverless computing service provided by Amazon Web Services (AWS) that allows you to run code without provisioning or managing servers. With AWS Lambda, you can focus on writing code for your application, while AWS handles the underlying infrastructure.
### Getting Started with AWS Lambda
First, you need to create an account on aws (https://aws.amazon.com/it/).
After the login, you should see something similiar to this:

Then, search for lambda, and select the first result in the search.
<div class="alert alert-warning" role="alert">
  This is a warning alert—check it out!
</div>