---
layout: post
title: A Layman's Guide to SSH Tunneling
---
11/03/12 - Waterloo

Recently, it has come to my attention that quite a few people are under the impression that most "United States Only" content is actually only available in the United States. Now the DMCA has basically allowed for a plethora of free, legal, video and movie content to be accessable on the internet. Unfortunatly, Canadian's are excluded from that sweet, sweet content. However, the solution to this is - well realitivly - simple. Once you have finished reading this post, not only will you be able to listen to all the Pandora you want and experience the joys of Hulu, you will even be able to use the United States version of Netflix which is, arguablly, infinatly better than its Canadian counterpart. All of this is possible to the magic of SSH. Even better, it's totally free!

The first step in your journy into a content discovery coma will be to sign up for an Amazon AWS account. Now, AWS is what Amazon describes as a "set of services that together form a reliable, scalable, and inexpensive computing platform 'in the cloud". Now you may be saying to yourself "inexpensive, doesn't that imply there's a cost to this?" and you would be right. Normally, the cheapest instance of Amazon EC2, the platform we are intereseted in, would cost you a starteling $0.085 an hour. Oh god, that's actually around $60 a month if you run continuously, certainly more than the $0.00 I promised you. Here's where we add the awesomesauce of using Amazon, Bezo's and company have decided to offer all new AWS customers *a full year* of free usage for an EC2 Micro instance (which happens to be substantially more powerful than what we need for SSH tunneling). Now, I'll leave the setup of EC2 for you to figure out but it shouldn't take you longer than an hour. [Amazon](http://docs.amazonwebservices.com/gettingstarted/latest/awsgsg-freetier/TestDriveFreeTier.html?r=8587) has some great docmentation when it comes to getting set up on the Free Usage Tier so feel free to follow it. And just a quick sidenote, there are literally thousands of machine images to choose from when setting up your EC2 instance but for simplicities sake I'm going to continue this tutorial under the assumption that you have chosen the stock Ubuntu instance. 

Once you've got your instance set up, the rest is a fairly simple process. All you really have to do is make sure that SSH is setup correctly on your local machine. For OS X and *nix users, there's a good chance you already have SSH setup on your machine (though if memory serves me correctly, you might need to enable it first on your Mac). Windows is a more tedious process but only slightly so. I recommend just installing Cygwin and selecting SSH as one of the packages during the installation. 

We're on the final strech now. In your terminal (or Cygwin instance), run:
    
    ssh -D 80 -i KEYPAIR.pem USER@HOST

That's it!

Well almost. The last step is to set your browser up to connect through a SOCKS proxy. Basically, this will run all your browser traffic through the SOCKS proxy you just setup on port 80 without effecting any of the other programs on your machine. I tend to just use Firefox for this because it is the only browser I've found that easily lets me do this; in my expericene Chrome and Safari just redirect you to your system settings for tunneling, something I would rather not bother configuring. In Firefox just go to Preferences -> Options -> Advanced -> Network, check the box marked "route traffic through tunnel" and enter the following settings.

    HOST: LOCALHOST
    PORT: 80

Wasn't that easy? Your browser is now tunneling all its traffic though Amazon's server in the *United States*. Feel free to vist your [favorite IP checking website](http://www.ipchicken.com) and verify your results. I typically just leave *Insert United States Based Music Streaming Service* running in Firefox and use Chrome for all my typical browsing. 