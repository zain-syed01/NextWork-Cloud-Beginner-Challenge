<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Zain Syed  
**Email:** zainalabideen2006@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build a secure cloud network by creating a custom VPC and using IAM policies to control instance access. I'm doing this project to learn how to manage permissions through resource tagging and to understand the networking fundamentals required for a professional AWS environment.

### What is Amazon VPC?

Amazon VPC is my own private, isolated corner of the AWS cloud. It is useful because it gives me total control over my network, letting me decide who can enter and how my resources talk to each other.

In today's project, I used Amazon VPC to build a custom, isolated network for my resources. I used it to define my own IP ranges and create subnets, giving me full control over which parts of my infrastructure are public and which stay private and secure.

### Personal reflection

This project took me about an hour to complete. Most of that time was spent getting comfortable with the CLI commands and troubleshooting that CIDR block error to make sure my subnets actually fit within the VPC.

One thing I didn't expect in this project was how strict CIDR math can be. I realized that a /24 VPC is actually pretty small, and I had to be careful with my subnet ranges to make sure they actually fit inside the network I built without overlapping or running out of room.

---

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will demonstrate how to initialize a Virtual Private Cloud (VPC) to serve as the isolated network for my resources.

### How VPCs work

A VPC (Virtual Private Cloud) is a private, isolated section of the AWS cloud where you can launch resources in a network you define

### Why there is a default VPC in AWS accounts

A default VPC is included in every AWS account so you can immediately launch resources like EC2 instances without manually configuring a network. 

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To set up my VPC, I had to define an IPv4 CIDR block, which is a range of IP addresses assigned to the network. The number after the slash, like /16, determines the total number of IPs available, ensuring the VPC has enough space for all subnets without overlapping.

---

## Subnets

### What I did in this step

In this step, I am setting up a subnet to partition my VPC into smaller, manageable IP ranges. I am doing this to isolate different types of resources, like placing web servers in a public subnet while keeping databases secure in a private one.

### Creating and configuring subnets

Subnets are smaller chunks of a VPC that let me group my resources. There are already subnets existing in my account, one for every Availability Zone, which AWS gives me by default so I can launch stuff quickly without needing to build a whole network first.

### Public vs private subnets

The difference between public and private subnets is basically how they talk to the internet. For a subnet to be considered public, it has to have a route to an Internet Gateway in its route table. This lets resources like web servers send and receive traffic from the outside world, whereas private subnets stay tucked away for things like databases that shouldn't be exposed.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

I enable auto-assign public IPv4 addresses so any instance I launch in this subnet automatically gets a public IP.

---

## Internet gateways

### What I did in this step

In this step, I’m creating an Internet Gateway (IGW) to give my VPC a doorway to the outside world. I'm doing this because, by default, the vpc is isolated. Without an IGW, my public subnet won't actually have a path to the internet.

### Setting up internet gateways

An Internet Gateway is my VPC’s connection to the internet. 

Attaching an internet gateway to a VPC means I'm basically plugging my private network into the actual internet. If I missed this step, my public subnet would stay totally isolated, and I wouldn't be able to reach any of my instances from my browser or terminal.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

### What I'm doing in this extension


In this secret mission, I am using AWS CloudShell to build my network directly from the command line instead of clicking through the console. I'm doing this to learn how to use the AWS CLI to automate infrastructure,

### Exploring CloudShell and CLI

### Debugging my setup

To set up a VPC or a subnet, you can use the command aws ec2 create-vpc or aws ec2 create-subnet. Make sure to avoid errors by including a valid CIDR block (like 10.0.0.0/16) so AWS knows exactly which IP addresses to reserve for your network.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-networks-vpc_9b2465411)

### Comparing CloudShell vs AWS Console

Compared to using the AWS Console, an advantage of using commands is speed and automation. I can script the whole setup instead of clicking through dozens of menus. An advantage of using the Console is the visual layout, which makes it easier to double-check my work as a beginner.

Overall, I preferred the commands because they're way more efficient and give me a better feel for how the cloud actually works under the hood.

---

---
