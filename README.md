#WMBDeploy

A simple Ant script I wrote back in 2009 to automate the deployment of BAR files for WebSphere Message Broker 6. At the time we had 473 MsgFlows, split based on alphabetical order across 12 Execution Groups. And could potentially take up to 2 hours to deploy a full set manually.

I did some research and found WebSphere Message Broker deployment scripting using Ant
http://www.ibm.com/developerworks/websphere/library/techarticles/0706_spriet/0706_spriet.html?ca=drs-

Alternatively you can also use the Configuration Manager Proxy API
http://www.ibm.com/developerworks/websphere/library/techarticles/0611_lucas/0611_lucas.html

Since I was short on time and coming from a Java Developer background, I chose to use the Ant approach.

##Overview
Basically my script does the following:

1. check out a project from either CVS or SVN (yes we still used CVS back then, if it was up to me, we'd all be using git of course)
2. build a number of BAR files using mqsicreatebar.exe
3. use mqsiapplybaroverride.exe to update properties such as extra MsgFlow instances 
3. SCP all the BAR files to the Broker Server
4. Call a shell script which in turn calls mqsideploy. Depending on the result, copy the BAR files to either Deployed or Failed directory.

I'm a visual person, so a picture is worth 1000 words:

##Usage
It's been so long since I wrote this I've actually forgotten. Will revise the next time I use this script.

##Disclaimer
This code base is uploaded mainly for my own reference, with the hope that it may offer some inspiration to others. I offer no support whatsoever and make no gurantees it will work out of the box. There may be better tools available for WMB deployment automation now and I will update accordingly when I come across them.
