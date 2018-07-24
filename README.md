# 362020-Hadoop-and-Managing-Big-Data-INTENSIVE-

Below is the detailed outline of the steps required to configure your own Jupyter Data Science Notebook Server on Amazon Web Services: 

1. Create SSH Key & Security Group on AWS
    1. Create a SSH key in bash by using command `mkdir –p .ssh`
        1. If you do command `ls ~/. ssh` it should show id_rsa and id_rsa.pub which are your public and private keys
	1. Then, you use command `cat ~/.ssh/id_rsa.pub` to generate your ssh~rsa
	1. Log onto AWS and go into SSH keys in your settings
	1. Add in the ssh~rsa that you recreated in the SSH keys
	1. Create security group (includes ssh (4 types))
1. Launch a new EC2 Instance
        1. Create Key Pair
        1. Add existing security group
        1. Review (it should be on Ubuntu, t2 micro, security groups, etc.)
	1. Then, go into Bash and use command `ssh git@github.com`
	1. Then, you use command `ssh ubuntu@ipaddress`
	          1. This is the public ip address from your ec2 instance
1. Provision new instance with Docker
        1. To do this, you should already see ubuntu@ip
	          1. if not, you will use command `ssh ubuntu$ipaddress –i ~/.ssh/id_rsa`
        1. Then, you use the command `curl –sSL https://get.docker.com | sh` which will execute the docker script
	1. Then, you have to use the command `sudo usermod –aG docker Ubuntu`
1. Pull the ds-nb image
        1. In order to pull the image, you have to use the command `docker pull Ubuntu`
	1. Then, you have to use the command `docker run –it Ubuntu bash`
	1. Then, you have to use the command `docker images`
1. Run the ds-nb container
        1. Then, you use the command `docker run -p 443:8888 -v /home/ubuntu:/home/jovyan jupyter/datascience-notebook`
	1. Then, you can use the command `docker ps` to see that the jupyter data science notebook is there
1. Get the token and use Jupyter 
	1. To get the token, you need to get the status ID so you use command “j” which will populate it
	1. Then, you run command `docker exec 1234 (first four characters of the status ID) jupyter notebook list`
	          1. This will populate the token = 
        1. Then, you can go grab the public IP address from AWS and put :443 at the end at launch that in a browser to open the Jupyter notebook 
	1. Use the token above for the website and you’re in!
	

	
	
	
	Below is the financial analysis and detailed budget of the costs of running a Jupyter Data Science Notebook Server for three months using at least three different kinds of EC 2 instances:
	
	Below is the price breakdown for On Demand Pricing and Spot Pricing for the same three instances (t2.micro, m4.large, m5.xlarge)
On demand pricing:
t2.micro	1	Variable	1 GiB	EBS Only	$0.0116 per Hour

m4.large	2	6.5	8 GiB	EBS Only	$0.10 per Hour

m5.xlarge	4	16	16 GiB	EBS Only	$0.192 per Hour

Spot pricing
t2.micro	$0.0035 per Hour
m4.large	$0.0178 per Hour	
m5.xlarge	$0.0461 per Hour	

In order to do the calculation of how much I’d be charged if I ran these servers for 3 months straight, I had to calculate how many hours were in 3 months. This brought me to 2,190 (approx.) hours for a 3 month period. Therefore, I multipled each hour rate by 2,190 to bring me to my total statement. Please see below:
1.	On Demand Pricing
a.	t2.micro = $25.40
b.	m4.large = $219
c.	m5.xlarge = $420.48

2.	Spot Pricing
a.	t2.micro = $7.67
b.	m4.large = $38.98
c.	m5.xlarge = $100.96

	
The final part of this homework is the diagram of my system which is in a separate file as a Visio Document.

	
	
	
	
	
	
