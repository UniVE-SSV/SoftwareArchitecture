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
**Amazon Web Services (AWS)** is a comprehensive and widely adopted cloud platform offered by Amazon. It provides a broad set of cloud-based services, such as computing power, storage options, and networking capabilities, which are designed to support businesses in building and deploying applications more flexibly and efficiently. AWS offers a "pay-as-you-go" pricing model, which means you only pay for the resources you use, making it cost-effective for both small startups and large enterprises.  
AWS offers over 200 fully featured services from data centers globally, allowing businesses to use and scale various resources according to their needs without the upfront costs associated with traditional on-premises infrastructure.

**AWS Lambda** is a serverless computing service provided by AWS that allows you to run code without provisioning or managing servers. With AWS Lambda, you can focus on writing code for your application, while AWS handles the underlying infrastructure.
### Getting Started with AWS Lambda
<div class="alert alert-warning" role="alert">
To follow this section - and the upcoming - you need to create an AWS Account. However, to use AWS Lambda, you need to register a valid credit card. You can use AWS Lambda for free, up to 1 million requests per month (which for our tutorial is enough). Remember that if you you exceed this limit, aws will withdraw money from your card.
</div>
First, you need to create an account on aws (<a target="_blank" rel="noopener noreferrer" href="https://aws.amazon.com/">https://aws.amazon.com</a>). If they ask you for a support plan, select the free one (Basic Support).
After the login, you should see something similiar to this:
![AWS Intro 1]({{ site.baseurl }}/images/awslambda_intro_1.png)
Then, search for lambda, and select the first result in the search.
![AWS Intro 2]({{ site.baseurl }}/images/awslambda_intro_2.png)
If you see the Complete Sign-Up page, fill the require information (at the end, the system will redirect you to the home page, so you need to redo the first step).
![AWS Intro 3]({{ site.baseurl }}/images/awslambda_intro_3.png)
![AWS Intro 4]({{ site.baseurl }}/images/awslambda_intro_4.png)
You should see a page similiar to this:
![AWS Intro 5]({{ site.baseurl }}/images/awslambda_intro_5.png)
Take a look at the page. The idea of AWS Lambda is that you write a function (see the provided example) and AWS provides you the server that run that function, without worrying about scaling, resource allocations, etc.  
Clicking the "Create a Function" button takes you to the dashboard:
![AWS Intro 6]({{ site.baseurl }}/images/awslambda_intro_6.png)
Here, you can monitor your functions and inspect some metrics. In the next section, we will explain briefly how the platform works.
## Exercies
1. Follow the Tutorial:
![AWS Intro 7]({{ site.baseurl }}/images/awslambda_intro_7.png)