# MSR-TEST-INTENSHIP

# LETS DIVIDE THE TOTAL PROJECT INTO N NUMBER OF STAGES

# STAGE-1

# CREATING INFRASTRUCTURE (CREATING INSTANCE)

--> For this we need to have a AWS account --(Create a account in AWS which will be free for one year)

-->Creating a Instance
 
#Step-1 : Open AWS account and login with credentials, Select services & select EC2 (ELASTIC CLOUD COMPUTE)
 
 ![instance creating](https://user-images.githubusercontent.com/44922458/50392921-5977bc80-0778-11e9-8278-cff78ddebc6e.PNG)
 
#Step-2 : Select required region & select Launch Instance tab 
 
 ![instance creating -1](https://user-images.githubusercontent.com/44922458/50392957-aa87b080-0778-11e9-9701-21fcd3e48960.PNG)

#Step-3 : Here we will find seven stages for creating instance, we will go one by one, The first one is 

Choosing Amazon Machine Image (AMI), as per our project instructions we are taking here Ubuntu server 16.04 LTS, search for ubuntu where we will find different versions of ubuntu, select required one (i.e. 16.04 LTS version).

![instance creating -2](https://user-images.githubusercontent.com/44922458/50393025-57622d80-0779-11e9-9792-71d75116bfe8.PNG)

#Step-4 : The secong stage of instance creating is selecting of instance type (As per instructions i have taken t2-micro) which is eligible         for free tier.

![instance creating -3](https://user-images.githubusercontent.com/44922458/50393115-f850e880-0779-11e9-878a-72f4ddfab834.PNG)

#Step-5 :The Third stage is configuring Instances - where we will select no of instances, VPC, Subnet etc.. for time being here we are not creating any VPC..
 Here as per project requirement, we are creating 2 instances by giving 2 in no of instances tab.
  Note: Alternatively we can create one instance normally and for second instance we can create by ansible script.
  
  ![instance creating -4](https://user-images.githubusercontent.com/44922458/50393952-af039780-077f-11e9-8287-496c24b135c5.PNG)
  
  Alternative option for creating instance by ansible script:
  
  ![playbook-instance creating](https://user-images.githubusercontent.com/44922458/50394118-3998c680-0781-11e9-853e-25edef7625f6.PNG)
  
#Step-6 : the fourth stage is Add Storage (by default for t2-micro size will be 8Gb)
  
  ![instance creating -5](https://user-images.githubusercontent.com/44922458/50394057-a6f82780-0780-11e9-972d-f5ce52b49bd3.PNG)
 
#Step-7: The fifth stage is creating tags, which we can skip and the sixth stage is selecting security group, where we can select default security group or we can create one security group (in which we will keep all the required ports open)
note: here we are performing some ansible tasks so we should keept ssh ports open.

![instance creating -6](https://user-images.githubusercontent.com/44922458/50394174-bb88ef80-0781-11e9-80df-2a9cc96cb028.PNG)

#Step-8: The seventh & last step of creating instance is to review and once if everything is okay, we can select launch instance.

![instance creating -7](https://user-images.githubusercontent.com/44922458/50394191-f5f28c80-0781-11e9-8ea2-1b2751353938.PNG)

#Step-9: once we hit launch instance tab, one tab will appear on screen regarding key pairs, where we can use existing key pairs or we can create one new key pair, here we are creating a new keypair with the name intenship Project after that hit download key pair, a pem file will be downloaded.

![key pair downloading -1](https://user-images.githubusercontent.com/44922458/50394370-0820fa80-0783-11e9-901f-b84db6b62771.PNG)

#Step-10: converting pem file to private key--> for this we need to download puttygen, after than we have to load our key pair (named intenship Project) which we have downloaded in step-9, Afterthat hit save privatekey button sothat our key PPK file will be saved, which will be used for opening our instances.

![converting pem file to private key -2](https://user-images.githubusercontent.com/44922458/50394492-e5431600-0783-11e9-8455-1195846d3602.PNG)

![converting pem file to private key -1](https://user-images.githubusercontent.com/44922458/50394502-f12ed800-0783-11e9-8395-73a17ce88df1.PNG)

#Step-11: Renaming of instance--> Name the instance as per our project requirement (MSR-test-Instance-1 & MSR-test-Instance-2)

![renaming instances](https://user-images.githubusercontent.com/44922458/50394572-7c0fd280-0784-11e9-981a-2b3c1f725016.PNG)

#Step-12: Starting Instance --> for this step, we should select the instance which we required to open then go to Action tab, select instance state and press start, after that our instance will be started after some status checks (system status & instance status checks)

![opening instance -1](https://user-images.githubusercontent.com/44922458/50394775-a7df8800-0785-11e9-9ea4-55aa6175f53d.PNG)

#Step-13: Opening Instance --> we have to open putty for this and copy IPv4 Public IP of required instance which you need to copy and paste in putty hostname/IP address tab.

![opening instance -2](https://user-images.githubusercontent.com/44922458/50394789-b9289480-0785-11e9-9b97-18b76a49afbf.PNG)

#Step-14: Loading of PPK key into Putty --> for opening of our instance we have load our Private key (which we have converted and saved in step 10) in putty and hit OPEN

![opening instance -3](https://user-images.githubusercontent.com/44922458/50394899-b11d2480-0786-11e9-8020-5ad929e08751.PNG)

#Step-15: A Command line interface will be opened asking Login as, since we have taken "ubuntu" we should type ubuntu (for RHEL & Amazon linux it is "ec2-user" for centos default login is "centos")

![login of instance -1](https://user-images.githubusercontent.com/44922458/50394991-5801c080-0787-11e9-82f7-656c86a45a4a.PNG)




