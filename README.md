# DATA DOG -- Set up:
For this project I created a Centos VM using Vagrant, and installed the Datadog agent, where I created tags, set up dashboard regarding metrics from my virtual machine.

## What is Datadog? 
> It is an org/software used for monitoring:
* Infrastructure
* Cloud 
* APM
* RUM
* Container
* Security
* Logs
<hr>

## STEP 1: 

1) Spin up Centos machine 
2) Create DD trial membership:
3) Install DD Agent on VM : Create API key, run in CLI
4) Check out DD config file - '/etc/datadog-agent/datadog.yaml'
<code>
sudo vi /etc/datadog-agent/datadog.yaml
</code>

![img](img/dd2.png)

![img](img/dd3.png)

5) stop and restart dd agent to set changes: 
6) Confirm DD agent is recognized on DD website/app and gathering metrics of VM:
![img](img/dd4.PNG)
![img](img/dd5.PNG)   
7) Install EPEL repo, install Stress to run fake cpu load to catch data/metric on VM. 
<code>
sudo yum install epel-release
<br>
sudo yum install stress -y
</code>
8) Set up APACHE integration on DD:
* sudo yum install httpd
* sudo systemctl start httpd.service | systemctl status httpd.service

![img](img/dd6.PNG) 
9) install mod status and enable to monitor web server load - https://www.tecmint.com/monitor-apache-web-server-load-and-page-statistics/
![img](img/dd7.PNG)
![img](img/dd8.PNG)
10) Confirmed from DD Metrics dashboard that Apache is integrated and providing metrics:
![img](img/dd9.PNG)
11) Ran stress test on machine to gather cpu metrics
<br>
<code>stress --cpu 2 --timeout 60</code>

![img](img/stress2.PNG)
![img](img/dd10.PNG)
12) Create a monitor based on host and metrics: - if host is down, will get notification from monitoring
![img](img/dd11.PNG)
![img](img/stress1.PNG)
13) Monitors are showing that apache is breaking threshold and sending alert. 
14) Create new dashboard listing specific metrics want to show :
![img](img/dash.PNG)