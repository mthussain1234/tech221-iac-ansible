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


