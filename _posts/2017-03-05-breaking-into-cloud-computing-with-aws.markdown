---
title: Breaking into Cloud Computing with AWS
date: 2017-03-05 03:13:00 Z
tags:
- cloud computing
- aws
- amazon
---

During my sophomore year of college, I found the need to have a site hosted for one of the projects that I was working on. Just a simple apache web server was needed.(I don't remember the project exactly, but it was something along the lines of an e-commerce web page that sold something). Since I was in college at the time, I was looking for an affordable solution, preferably free since it was just a small school project. I had stumbled upon <a target="_blank" href="https://www.000webhost.com/">000webhost</a>, which provided exactly what I needed. It worked and I used it throughout the rest of my undergraduate year for the primary reason of it 'just working'.

Now since they don't really cover how the industry actually works, this sort of thing is put on the back burner for students to learn themselves. So learning how to properly set up a hosted website was for me to figure out and the school to never know if I was successful. 

Finally, I was working on a side project that actually needed a more reliable source of truth. It was a web app front end admin tool that I was working on that had an API that communicated with our mobile application client. 000webhost worked fine for the school stuff, but I wanted a paid solution to have the support if I needed it. Not knowing the app was ever even going to be used or successful, I didn't mind and still evaluated my options. After researching it came down to three options

* <a target="_blank" href="http://www.hostgator.com/">Hostgator</a>
* <a target="_blank" href="https://www.bluehost.com/">Dreamhost</a>
* <a target="_blank" href="https://www.dreamhost.com/">Bluehost</a>

It could have been naivety or fear of trying something too complex, but these three options I felt wouldn't have been too far over my skill level.  I was accustomed to the CPanel environment which all of these sites provided. I imagine that all of these sites were just hardware with a CPanel front end.  I wasn't as comfortable to SSH into a server and mess around that way. Anyway, the decision was to go with Bluehost simply because at the time there were a tiny bit of cost savings(maybe a dollar or two/month over the other two)

This worked for some time. I had co-founded a small company in the mean time that was going to be working on a few new side projects. We would still be using Bluehost moving forward as our development server for the sake of cheapness. However, after evaluation, we did not see this as fit for a production ready server that needed to be reliable as far as uptime and consistency. Since Bluehost is a shared tendency you get all the crap of having to deal with other's on the same server as you.(Not that AWS doesn't have the same thing but they provide a lot better handling and surely have a lot better infrastructure than a company like Bluehost) 

As our side projects got more serious, there was more of a need to have that reliability and granular control of our stuff. Our applications weren't complex but the need for stability came with people actually using our software and noticing things like when it was slow, when it was down, etc. More research had to be done on what we could do to make things better for our apps.  <a href="https://aws.amazon.com/" target="_blank">AWS</a> stood out to us as an up and comer in the cloud industry. There was nobody else really like it at the time. I believe google cloud was very immature at the time, so we decided against that platform. The most appealing part to amazon was the 12 months free. It's actually deceiving if you don't read carefully because it's 12 hours running time. So if you have two EC2 instances it will drain that in half the time, so just an FYI for anyone thinking about trying amazon. With our mindset that we could at least try amazon and evaluate the performance at the very least, we started spinning up servers that mocked our current environment. Even with micro-instances, we were able to see performance over the Bluehost environment.

## How we use it

I'm not going to get into specifics on what we use for AWS environment, because if I told you, then I would have to kill you, but I will give a quick overview of what services we use and how we use them in no particular order:

**EC2(Elastic Compute)** - This is amazon's virtual server environments. They provide environments with different operating systems you can choose including, windows and different flavors of Linux. We use this for our web servers that need to be up all the time. Crucial for us since we provide we applications and solutions.

**EBS(Elastic Beanstalk)** - An abstraction of EC2 instances that makes deploying and managing applications easier.

**RDS** - Hosted relational database. Choose from a myriad of DBMS from oracle, MySQL, MSSQL and more. Very simple and self-explanatory.

**Route 53** - Managed DNS

**IAM(Identity Access Management)** - Security to access all of your AWS services. Be sure to remove the root accounts and to remove all keys and secrets from any open source repository. I had an issue where a bot found it from sample code I had taken from a tutorial and spun up $600/mo worth of servers in the Asia AV Zone.

**Cognito** - User directory service for mobile applications. This is something new we are trying out for future projects.

**CodeDeploy** - Deployment utility. Provide a git or mercurial version and link and will deploy the version you need. This is a very handy tool because rollback and updates are very easy.

**Codecommit** - Managed git repository. I hate to admit but we abandoned using code commit due to the complexity of setup. It was a pain to manage SSH keys so we switched to use bitbucket.

**API Gateway** - A gateway for HTTP request to be routed as a proxy to another HTTP endpoint or lambda function. We are setting up new serverless API's for an application that uses this in conjunction with triggers that fire lambda functions.

**Lambda** - FAAS.(Functions as a service) This is the newest piece of technology we are using. You can select from a small list of runtimes(NodeJS, JVM, python at the time of this writing) and write small functions that are executed based on some trigger

## Disadvantages

Although with those advantages we saw some disadvantages. One of the largest disadvantages was cost. Unfortunately, we did have to pay a little more to get the kind of granular control that AWS provides, but it was something we wanted.  It was worth it for us to have the control, elastic scaling, and reliability of the AWS platform.

Amazon also has a bit of complexity to managing all of their services. They have a lot of services and there isn't one AWS user that is using every single service.  If they had a customizable dashboard for services that you have it may be a little better user experience. Another useability thing that bugs me about it is that there isn't a way to see all instances of something across multiple zones. For instance, if you have two servers running in east-1 and two servers running in east-2. The user has to directly select the zone they want to view the instances. 

Overall, AWS provides a great platform to create production-ready software for developers. With all of the services they have, they will have something to fit your needs. However, there are competitors now that are catching up like Google and Microsoft. They have maturing platforms, so research and evaluation would have to be done before choosing!

Links:


<a target="_blank" href="https://aws.amazon.com/">AWS</a><br />
<a target="_blank" href="https://www.000webhost.com/">000webhost</a><br />
<a target="_blank" href="http://www.hostgator.com/">Hostgator</a><br />
<a target="_blank" href="https://www.bluehost.com/">Bluehost</a><br />
<a target="_blank" href="https://www.dreamhost.com/">Dreamhost</a><br />