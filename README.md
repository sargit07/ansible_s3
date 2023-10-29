Install jenkins and ansible in one ec2 .
To install ansible use :-
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
pip install boto3
sudo apt install ansible
To install jenkins:-
[ https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-20-04 ]
Go to the jenkins Dashboard ,go to the Manage Jenkins , 
Click Plugin Manager-> in available search ansible plugin & install it.
Go to in manage jenkins => global tool configuration=> choose ansible 
Give name as 'ansible' and path to ansible for this path open this ec2 through putty and give command which ansible it will give path choose up to /usr/bin/
Click on save.
Go to dashboard click on new item => give name ansible_s3 
select pipeline and click on ok.
In advance project option select pipeline script and write a script 
Click on pipeline syntax.
In sample step choose ansiblePlaybook:Invoke an ansible playbook 
• In Ansible tool it automatically select our ansible plugin name 
=> in Playbook file path in workspace give .yml file name which we want to execute example:- s3_bucket.yml 
• In Inventory file path in workspace give file name our credentials of ec2 example:- creds.yml
• SSH connection credentials click on add select ssh with private key 
-> In Id give ec2 machine id -> user name as ubuntu -> In private key click on add and add here .pem key content 
And click on add.
Then click on none and select ubuntu 
And click on generate a pipeline 
 Now again click pipeline syntax.
• Add step choose git
• Repository URL:- give repo url 
Select branch
Click on generate pipeline script and put it on the pipeline script
stage('SCM Checkout')
Click on save 
And click on Build Now
 In first or second build I got error 
To fix this I change the name of my bucket in s3_bucket.yml file 
Again click on build now .


