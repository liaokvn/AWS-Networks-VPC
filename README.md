# AWS-Networks-VPC

# Overview
Designed and deployed a custom VPC to practice AWS networking fundamentals. Learned how CIDR blocks, subnets, and gateways form the backbone of secure cloud architectures.

# Services Used
- Amazon VPC – custom private network environment

- Subnets – organized resources across availability zones

- Internet Gateway – enabled external communication for public subnets

- AWS CLI / CloudShell – created and managed VPC resources programmatically

# Key Accomplishments
- Created a custom VPC with a defined CIDR block.

- Built a public subnet with auto-assigned public IPs.

- Attached an Internet Gateway to allow external access.

- Used AWS CLI to provision resources, troubleshooting a missing CIDR parameter.

# What is Amazon VPC?
 Amazon VPC is a Virtual Private Cloud that lets me create an isolated,
 customizable network inside AWS. It is useful because it gives me full control
 over IP address ranges, subnets, routing, and security, so I can safely run
 resources like EC2 instances and databases while deciding how they connect to
 each other and the internet.

 # Virtual Private Clouds
 VPCs are isolated, private networks inside AWS where I can launch and manage
 my resources. They let me control IP address ranges, create subnets, and decide
 how my resources connect to each other and the internet. Without VPCs,
 everything in AWS would be in one open space with no boundaries, making it
 difficult to secure or organize resources.
 There was already a default VPC in my account ever since my AWS account was
 created. This is because AWS wants new users to be able to launch resources
 like EC2 instances right away without needing to set up networking from
 scratch. The default VPC comes pre-configured with subnets, routing, and an
 internet gateway so resources can connect to the internet immediately.
 To set up my VPC, I had to define an IPv4 CIDR block, which is a range of IP
 addresses written in Classless Inter-Domain Routing (CIDR) notation. It tells AWS
 what private IP addresses my resources can use inside the VPC. For example,
 10.0.0.0/16 gives me about 65,000 possible addresses that I can divide into
 smaller subnets.

 <img width="830" height="640" alt="Image" src="https://github.com/user-attachments/assets/570b9527-3d59-4f29-9003-870f82b2b471" />

 # Subnets
 Subnets are subdivisions of a VPC’s IP address range that allow me to organize
 and control where resources are placed. Each subnet maps to a specific
 Availability Zone, and I can create both public subnets (with internet access) and
 private subnets (without direct internet access). There are already default
 subnets in my account—one for every Availability Zone in the default VPC.
 Once I created my subnet, I enabled auto-assign public IPv4 addresses. This
 setting makes sure that any EC2 instance launched in this subnet automatically
 gets a public IP, so that it can connect to and be accessed from the internet
 without having to manually assign one.
 The difference between public and private subnets is whether they have a route
 to the internet. My subnet is not considered public yet because it does not have
 a route to an Internet Gateway. For a subnet to be public, it must be associated
 with a route table that directs traffic to the Internet Gateway, allowing resources
 inside to connect to the internet

 <img width="1025" height="218" alt="Image" src="https://github.com/user-attachments/assets/615a5f00-1169-4810-8ead-a8be83e6af25" />

 # Internt Gateways
  Internet gateways are AWS components that connect a VPC to the outside world,
 allowing resources in public subnets to send and receive traffic from the internet.
 They act like a bridge between your private cloud network and the internet,
 making it possible for instances with public IPs to be accessible to external users.
 Attaching an internet gateway to a VPC means my resources in public subnets
 can send and receive traffic from the internet. If I missed this step, any instance I
 launched would only have private IPs and could not connect to or be accessed
 from the internet, which would block external communication.

 <img width="1237" height="211" alt="Image" src="https://github.com/user-attachments/assets/203aad8f-d4a3-4bbb-aab5-f48670505d4d" />

 # Using the AWS CLI
 VPC resources could also be created with CloudShell, which is a browser-based
 shell environment built into AWS that gives me instant access to the AWS CLI
 without needing to install or configure anything locally. The CLI (Command Line
 Interface) is a tool that lets me manage AWS resources by typing commands
 instead of using the console, making it faster, more efficient, and easier to
 automate tasks.
 I ran into an error because my create-subnet command was missing the --cidr
block parameter, which tells AWS what IP range the subnet should use. To avoid
 this error, I need to include a valid CIDR block that falls within the range of the
 VPC’s CIDR block. For example, if my VPC is 10.0.0.0/16, I could create a subnet
 with 10.0.1.0/24.
 Compared to using the AWS Console, an advantage of using commands in
 CloudShell is speed and repeatability, I can launch and configure resources
 quickly without clicking through multiple pages, and I can reuse the same
 commands for automation. An advantage of using the Console is that it’s more
 visual and beginner-friendly, making it easier to understand the overall
 architecture when setting things up for the first time. Overall, I preferred using
 the CLI for efficiency, but I see the Console as helpful when I want a clear visual
 of my resources.

 <img width="1122" height="49" alt="Image" src="https://github.com/user-attachments/assets/62fb91e5-9715-40d9-a6dc-09ef0d7698a3" />

 # Summary 
 In this project, I built a custom Amazon VPC to practice cloud networking fundamentals and understand how AWS isolates and secures resources. I defined a CIDR block, created a subnet, and attached an Internet Gateway to enable external connectivity. Along the way, I troubleshot CIDR alignment errors and compared using the AWS CLI versus the Console, which gave me both a deeper technical understanding of IP planning and hands-on experience balancing efficiency with clarity. The project demonstrated my ability to design and configure secure cloud networks while problem-solving real-world setup issues
