# MSR-TEST-INTENSHIP

# LETS DIVIDE THE TOTAL PROJECT INTO 4 NUMBER OF STAGES

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


# STAGE-2

--> INSTALLING ANSIBLE IN ONE INSTANCE & LINKING OF SECOND INSTANCE THROUGH ANSIBLE HOSTS
------------------------------------------------------------------------------------------

#Step-1:
-------
Open one instane (i.e MSR-test-Instance-1)
--> change hostname as MSR1 for identification purpose (cmd--> sudo hostname MSR1 --> exec bash)

#Step-2:
--------
Installing Ansible in MSR1 instance
--> following commands for installing ansible:
-->sudo apt-get update
-->sudo apt-get install ansible
checking ansible version --> ansible --version

![ansible installation](https://user-images.githubusercontent.com/44922458/50397818-f4808e80-0798-11e9-9b30-172440a89934.PNG)

#Step-3:
--------
Open other instance (MSR-test-Instance-2) in the similiar way described in STAGE-1 (step 14 & 15) & change the hostname similarly as shown as above)

#Step-4:
--------
Go to instance-1 (MSR-1) and change to root with cmd ($ sudo -i) and generate ssh-keys by using command $ ssh-keygen

#Step-5:
--------
Now we have go to path /root/.ssh, there we will find public keys, copy public key (id_rsa.pub) and paste in authorized keys file of both instances (i.e MSR1 & MSR2)

#Step-6:
--------
Now go to ansible path (i.e /etc/ansible) there you will find hosts file edit that file and add PUBLIC IP of second instance and localhost also.

![hosts adding](https://user-images.githubusercontent.com/44922458/50398364-f9474180-079c-11e9-8350-5df4f042d336.PNG)


# STAGE-3 --> CHECKING FOR HOST CONNECTIONS

#Step-1:
--------
         Be sure that you have installed Python in second instance
         Installation: $ sudo apt-get update & $ sudo apt-get install python
        
#Step-2:
--------
Now go to MSR1 instance (i.e where we have installed Ansible) and type cmd $ ansible -m ping all, then we can see a message like this

![checking connections](https://user-images.githubusercontent.com/44922458/50398652-41fffa00-079f-11e9-8b9e-1fb73920809f.PNG)


# STAGE-4 --> INSTALLING SOFTWARES

#Step-1: --> Installing GIT
---------------------------
  --> Create a playbook for installing Git in MSR1 Instances
    
   ---
   - hosts: all
     become: true
     tasks:
     - name: installing GIT
       apt: name=git state=present update_cache=yes
    
  --> Run Playbook with command $ ansible-playbook git-playbook.yml  and the result is
    
   ![git playbook -result](https://user-images.githubusercontent.com/44922458/50399330-af625980-07a4-11e9-8740-448a33cd0270.PNG)
    
  --> git version installed is 2.7.4
  
#Step-2: --> Installing DOCKER
------------------------------
--> Create a playbook for installing Docker in MSR1 Instance

****
      ---
      - hosts: all
        become: true
        tasks:
      - name: Add Docker GPG key
          apt_key: url=https://download.docker.com/linux/ubuntu/gpg

        - name: Add Docker APT repository
          apt_repository:
            repo: deb [arch=amd64] https:https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
        - name: Install list of packages
          apt:
            name: ['apt-transport-https','ca-certificates','curl','software-properties-common','docker-ce']
            state: present
            update_cache: yes
****
--> Run Playbook with command $ ansible-playbook docker-playbook.yml and the version of Docker is  18.09


#Step-3: --> Installing Docker-Compose
--------------------------------------
--> Create a playbook for Docker compose as follows

*****
      ---
      - hosts: all
        become: true
        tasks:
        - name - name: Install Docker Compose (Docker-complex)
          get_url:
             url: https://github.com/docker/compose/releases/download/1.23.2/docker-compose-Linux-x86_64
             dest: /usr/local/bin/docker-compose
             mode: 4777
  ****
  --> run the playbook using command ansible-playbook docker-compose.yml
  and the version of docker-compose is docker-compose version 1.23.2, build 1110ad01

 #Step:4: Installing Node 8.12.0 
 -------------------------------
 --> Create a playbook for installing Node 8.12.0 in ansible installed instance
*****
      ---
      - hosts: all
        become: true
        tasks: 
       - name: nodejs 8.12
          get_url:
            url=https://nodejs.org/dist/v8.12.0/node-v8.12.0.tar.gz
            dest=/opt

        - name: Extract node tar.xz
          unarchive:
            src: /opt/node-v8.12.0-linux-x64.tar.xz
            dest: /opt/riyaz
            remote_src: yes

        - name: Rename
          command: mv /opt/riyaz/node-v8.12.0 /opt/node-v8
        - name: create 'nodejs-env.sh' 
          file: path=/etc/profile.d/nodejs-env.sh state=touch owner=root group=sys mode=0555

        - name: ensure file exists
           copy:
           dest: /etc/profile.d/nodejs-env.sh/   
           content:
              export NODEJS_HOME=/etc/node/node-v8.12.0/bin
              export PATH=/etc/node/node-v8.12.0/bin:/etc/node/node-v8.12.0
 *****
--> run the playbook using command ansible-playbook node-playbook.yml
  and the version of node is 8.12.0
  
 #Step-5: Installing NVM 0.33.2
 ------------------------------
--> Create a Playbook for installing NVM
****
      ---
      - hosts: all
        roles:
          - role: ansible-role-nvm
            nodejs_version: "0.33.2"
****
--> run the playbook using command ansible-playbook nvm.yml
  and the version of nvm is 0.33.2
  
 #Step-6: Installing OpenSSL
 --------------------------
 --> Create a Playbook for installing OPENSSL
****
      ---
      - hosts: all
        become: true
        tasks:
        - name: installig open ssl
          get_url:
            url: https://www.openssl.org/source/openssl-1.1.1a.tar.gz
            dest: /usr/src
        - name: urarcheiving
          unarchive:
               src: /usr/src/openssl-1.1.1a.tar.gz
               dest: /usr/src/
        - name: Shell commands
          shell:
          args:
           chdir: /usr/src/openssl-1.1.1a
           executable:
               ./config
               make
               make_test
               make install

****
--> run the playbook using command ansible-playbook ssl.yml
  and the version of 1.1.1a
   
end of the task
Hello
commit changesq
