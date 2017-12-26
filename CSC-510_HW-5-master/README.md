# CSC-510_HW-5    
        
### Setup        
Install node.js         
Install forever         
Pull/clone git repo     
Install npm packages    
        
### Tasks     
Run app: forever start main.js  
Security: Ensures bash, openssl, openssh-client, and openssh-server are running latest version.         
Cleanup: Remove content in /tmp/*               
        
[Link](./Playbook.yml) to code file     
        
### Steps to run        
Create two virtual machines: Ansible and node0

#### Setup Ansible:     
1) mkdir -p /boxes/ansible; cd /boxes/ansible   
2) run 'vagrant init ubuntu/trusty64'   
3) run 'vagrant up'     
4) Open Vagrantfile and uncomment private ip address as '192.168.33.10'         
5) run 'vagrant reload'         
        
Ansible Installation:   
sudo apt-add-repository ppa:ansible/ansible     
sudo apt-get update     
sudo apt-get install ansible            
                
                
#### Setup node0:            
Repeat above steps but, keep private ip address in step 4) as '192.168.33.100'          
        
Connecting ansible and node0:   
1) cmd node0, run the command 'vagrant ssh-config'      
2) Copy private key from the specified path 'independent key':  
3) On Ansible, (vagrant ssh) create file keys/node0.key and copy the key there          
4) Change access permissions: 'chmod 600 /keys/node0.key'       
5) Create inventory file at home location and enter:    
[nodes]         
192.168.33.100 ansible_ssh_user=vagrant ansible_ssh_private_key_file=./keys/node0.key           
                
#### Run Playbook tasks         
Run the Playbook.yml using command: ansible-playbook Playbook.yml -i inventory       
        
        
### Concepts         
        
        
**1. Why should developers use configuration management tools to manage their software programs? What can go wrong?**      
[Reference: https://www.digitalocean.com/community/tutorials/an-introduction-to-configuration-management]
        
Configuration management (CM) refers to the process of systematically handling changes to a system in a way that it maintains integrity over time. Developers should use Configuration management tools as they have following benefits:        
        
**Quick Provisioning of New Servers**   
Whenever a new server needs to be deployed, a configuration management tool can automate the provisioning process. Automation makes provisioning much quicker and more efficient because it allows tedious tasks to be performed faster and more accurately than any human could.  
    
**Quick Recovery from Critical Events**   
When a server goes offline due to unknown circumstances, it might take several hours to properly audit the system and find out what really happened. In such scenarios, deploying a replacement server is usually the safest way to get services back online while a detailed inspection is done on the affected server. With configuration management and automation, this can be done in a quick and reliable way.      
            
**Cost Reduction and Risks**    
Configuration Management saves money with the constant system maintenance, record keeping, and checks and balances to prevent repetition and mistakes. The organized record keeping of the system itself saves time for the IT department and reduces wasted money for the company with less money being spent on fixing recurring or nonsensical issues. With an updated system, there is also reduction in risks of potential lawsuits for breaches of security because of outdated software framework, which could possibly be attributed to negligence.
    
**Reliability**   
Nothing is worse than an unreliable system that is constantly down and needing repairs because a company’s configuration management team is lacking in organization and pro-activeness. If the system is used correctly, it should run like the well-oiled machine that it is, ensuring that every department in the company can get their jobs done properly. Increased stability and efficiency of the system will trickle down into every division of a company, including customer relations, as the ease and speed in which their problems can be solved and information can be accessed will surely make a positive impact.    
        
        
**What Can go wrong?**        
        
a) Configuration errors can lead to more serious mishaps like application performance problems, policy compliance violations or even security vulnerabilities.          
b) configuration management is an area where many companies either 1) put it as a 'last to solve' on their priority list (when arguably it’s quite important), or 2) try to solve it with a do-it-yourself fix, but in a way that’s not always extensible or that doesn’t end up working with their DevOps toolchain.           
c) Configuration issues stemming from the age old problem: using the wrong tool for the job as there are large number of tools available in the market.            
        
              
**2. Explain the difference bewteen continuous integration, continuous delivery, and continuous deployment, in your own words.**                
    
Continuous integration    
Everyone working in a team merges code changes to a central repository multiple times a day. Each time code is merged, an automated build is triggered, followed by tests for the given project. Continuous integration puts a great emphasis on testing automation to check that the application is not broken whenever new commits are integrated into the main branch. It acts as a safety check that helps developers prevent issues before they reach users. So, developers are able to ship code with confidence, though not necessarily fast.    
      
Continuous delivery   
Continuous delivery is the process of automating the software release process. It adds an extra step to Continuous Integration i.e. Acceptance testing. The outcome of Continuous Delivery stage is that anyone who has the privileges to deploy to production can do so in one-click.    
    
Continuous Deployment   
Continuous Deployment in simple words is: Continuous Integration + Continuous Delivery + fully automated deployment to production. Continuous Deployment is a step up from Continuous Delivery in which every change in the source code is deployed to production automatically, without explicit approval from a developer.            
                
        
                
### Screencast    
[Link](https://youtu.be/ccUrAgN2ifE) to screencast


