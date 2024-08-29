---
title: 1. NodeJS
category: 10. Node JS and React
order: 1
---
![NodeJS logo]({{ site.baseurl }}/images/nodejs_logo.svg)
<h2>Contents</h2>
* toc
{:toc}
## Introduction

Let's create a NodeJS that interact with our REST API and shows a front-end.  
Node.js, often referred to simply as Node, is an open-source, cross-platform runtime environment that allows developers to run JavaScript code on the server side. It enables the creation of scalable and high-performance applications, particularly web servers, that can handle numerous simultaneous connections with high throughput.

## Install NodeJS
Execute the next commands in your terminal to install NodeJS (alternative, you can use the official <a href="https://nodejs.org/en/download/prebuilt-installer">installer</a>, or use a Docker image).
{% highlight bash %}
# installs nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
# download and install Node.js (you may need to restart the terminal)
nvm install 20
# verifies the right Node.js version is in the environment
node -v # should print `v20.17.0 (or above)`
# verifies the right npm version is in the environment
npm -v # should print `10.8.2 (or above)`
{% endhighlight %}
- **nvm** stands for Node Version Manager and is a tool used to manage multiple versions of Node.js on a single machine. It allows developers to easily switch between different versions of Node.js, which is particularly useful when working on multiple projects that require different versions of Node.js or when testing code compatibility with different versions. With the above snippet of code, we had downloaded and ran the nvm installer. Then, with nvm, we installed NodeJS v20.x.
- **npm** stands for Node Package Manager. It is a powerful tool that helps developers install, share, and manage JavaScript packages and dependencies in their projects. npm is included with Node.js, so when you install Node.js, npm is also installed automatically. It is like **pip** for Python.
