## What is Infrastructure as Code (IAC)?

- IAC is an approach thats allows for infrastructure provisioning and management, by using machine readable config files rather than manaully setting it up
- Infrastructure configs are treated as code -> allowing for version control, automation and reproducibility
- Helps streamline deployment and management of infrastructure resources


## Benefits of IAC
- Agility - as there is rapid provisioning and deployment of infrastructure resources by automating this process
  - Changes to infrastructure made by programming, allowing you to adapt to changing business needs, and reducing the time compared to manual setup
- Consistency - IAC ensures consistent configs across environments, no manual errors which could happen in manual setup
  - Config files can be shared and reused, infrastructure setup is reproducible, improves stability and reduces inconsistencies
- Scalability - Infrastructure provision is automated, can easily scale resouces up or down when needed
  - Enables business to handle increase workloads, accomodate growth, and respond to changes in demand


## Use cases of IAC

- Cloud deployment - IAC used to automate provisioning of insfrastructure resources in cloud environments
- Continuous Delivery - IAC helps integrate infrastructure setup into CD pipeline, allows for faster and more reliable software release
- DevOps practices - IAC uses same principles as DevOps, using IAC, Dev and Ops teams can work together to define
and manage IAC, improved communication -> faster feedback loops -> increased efficiency when delivering software


## Who is using IAC

- Netflix - Automate deployment of streaming services on AWS, allows them to scale services based on demand -> seamless user experience
- Airbnb - uses IAC tools like Terraform to automate provisioning of their resources, can easily spin up and remove instances based on needs, can quickly deploy their platform in various regions, supporting global user base.
- Nasa - leverage IAC tools like Ansible and Puppet to automate the config management of their complex IT infrastructure, helps NASA streamline operations, reduce manual errors, and accelerate deployment of critical systems used in their research.
- Home Office - use Ansible and Chef to automate their provision of their IT infrastructure. Can rapidly set up serverts, networks and security configs. Using IAC, Home office manage their IT resources, enhance their system security, and respond to changing requriements.


## How IAC is used in industry

- Infrastruccture Provisioning - IAC tools can automate the creation and config of these resources ( VMS, networks, storage etc), streamline process
, reduce manual effort, and make sure it is consistent across environments

- Config Management - IAC allows for consistent config of resources, configs are designe din code, so the infrastructure components are set up correctly and uniformly
Simplifies management, reduces human error, and enhances security 

- Continuous Deployemnt (CD) - IAC integrates with CI and CD piplines, changes to infrastructure can be automatically deployed alongside code changes
giving them a seamless and automated deployment process -> reduced deployment time -> icnreased consistency -> frequent and reliable realease of working software

## Configuration management?

- Config management - managing and controlling software and system configs across environemnts
- makes sure that the systems are setup consistently, sticking to the correct states, security policies and requirements
- Config Management tools can atuomate the process -> easy to maintain, manage processes, enforce standards in config -> increases stability, seucrity and compliance

## What is ansible - benefits- use cases- what is YAML and playbooks

- Ansible like Jenkins is an open source automation tool - simplifies configuration management, app deployment
- Uses language that is easy to learn and use for automating various tasks, has an agentless architecture -> no additonal agents needed, can communicate with nodes using SSH
- Simple and efficient way to manage infrastructure configs, automate maual repetitve operations, and streamline workflows

- Benefits: 
  - Has easy syntax, uses YAML based config files, easy to read write and understand
  - Agent less architecture
  - Enables automation and orchestration of complex tasks, you can have streamlined operations, less manual effort and better efficiency

- Use cases:
 - Infrastructuer automation, app deployment, config management

- YAML
 - YAML (short for "YAML Ain't Markup Language") is language in human readable format 
 - used in Ansible playbooks to define infrastructure resources and configurations in a structured way.
 - Playbokos deifne tasks to be executed on nodes
 - Playbooks can include conditionals, loops, and variables, making them a powerful way to automate complex workflows.


# Ansible Controller

1. Create a `VagrantFile` in your VScode in the repository you created for IACs.
2. In that, if you are in Windows copy and paste this code below to create our 3 VMs `app` `db` `web`
```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what

# MULTI SERVER/VMs environment
Vagrant.configure("2") do |config|
    # creating our Ansible controller
    config.vm.define "controller" do |controller|
      controller.vm.box = "bento/ubuntu-18.04"
      controller.vm.hostname = 'controller'
      controller.vm.network :private_network, ip: "192.168.33.12"
      # config.hostsupdater.aliases = ["development.controller"]
    end
  
    # creating first VM called web
    config.vm.define "web" do |web|
      web.vm.box = "bento/ubuntu-18.04"
      # downloading ubuntu 18.04 image
      web.vm.hostname = 'web'
      # assigning host name to the VM
      web.vm.network :private_network, ip: "192.168.33.10"
      # assigning private IP
      #config.hostsupdater.aliases = ["development.web"]
      # creating a link called development.web so we can access web page with this link instead of an IP
    end
  
    # creating second VM called db
    config.vm.define "db" do |db|
      db.vm.box = "bento/ubuntu-18.04"
      db.vm.hostname = 'db'
      db.vm.network :private_network, ip: "192.168.33.11"
      #config.hostsupdater.aliases = ["development.db"]
    end
  end
  ```
3. After this, in Git Bash, `cd` to the folder with the VagrantFile, you can remove any previous VagrantFiles in other locations
4. We now `vagrant up` to launch our 3 VMs
5. `vagrant ssh app` to ssh into our app and perform ``` sudo apt-get update
sudo apt-get upgrade -y```, to install the required dependencies needed
6. Repeat step 5 for `controller` and `db`, installing the required packages
7. Once done, we now only need to stay in the `controller` VM
8. In the `controller` VM, run these commands in order:
```
sudo apt update -y
sudo apt upgrade -y

sudo apt install software-properties-common
sudo apt-add-repository ppa:ansible/ansible

sudo apt update -y
sudo apt install ansible

ssh vagrant@192.168.33.10 # password is vagrant
```
9. With the final command shown above, it will `ssh` us into the `web` VM, using its IP address.
10. Do `sudo apt install tree` then `tree` to use command, more presentable than using `ls`





![image](https://github.com/mthussain1234/tech221-iac-ansible/assets/129314018/3c686db8-1097-4d4d-bdb6-78b858ca592d)

```sudo nano hosts```, then edit file as shown below

![image](https://github.com/mthussain1234/tech221-iac-ansible/assets/129314018/755942ad-f39a-4857-ae9b-847c39114499)

![image](https://github.com/mthussain1234/tech221-iac-ansible/assets/129314018/42423a6c-80ef-42ec-a136-d850e01eb09a)

sudo nano hosts again

```
192.168.33.10 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
```

![image](https://github.com/mthussain1234/tech221-iac-ansible/assets/129314018/ad8bae27-bd75-4721-9941-7491bfbf8179)

Saving and exiting run the command 
```
sudo ansible web -m ping
``` 
again and it should show a new outcome after changing our hosts file.

![image](https://github.com/mthussain1234/tech221-iac-ansible/assets/129314018/c50cd552-3a31-43eb-9e64-0379ae332953)









