
## Introducing Today's Project!

### Project overview

Today, I am hosting a live, public website using an Amazon S3 bucket. This project demonstrates how to configure cloud storage for web hosting, manage global naming conventions, and control public access permissions.

### Tools and concepts

I learned how to use Amazon S3 to host a live site and manage object storage with unique naming. I also practiced cloud security by fixing 403 Forbidden errors using ACLs and writing Bucket Policies to protect my files from deletion.

### Time, challenges, and wins

It took me about an hour to finish everything, including the Secret Mission part. Most of the time was spent getting the bucket policy and permissions right to fix that 403 error.

---

## How I Set Up an S3 Bucket

### What I did in this step

Today, I am opening the Amazon S3 console and creating a dedicated storage space, known as a bucket, to host my website files. I am ensuring the bucket is initialized and ready to receive the project's web assets.

### How long it took to create the bucket

Creating an S3 bucket took me 5 minutes.

### Region selection

I am choosing the us-east-2 (Ohio) region because it provides a reliable and cost-effective environment with low-latency access for users in the Eastern and Central United States.

### Understanding bucket name uniqueness

Since S3 bucket names have to be unique across all of AWS, it means no two people in the world can have the same bucket name. I am picking a custom name so my website has its own unique web address that doesn't overlap with anyone else's.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

I am downloading the HTML file and the image assets to my local machine. I am then uploading these files directly into my S3 bucket to provide the content for my website. This step ensures that all the necessary files are in the cloud and ready for the next configuration.

### Files I uploaded

I am uploading the index.html file and a zip folder containing the site's images into the bucket. These files provide the core code and media that allow the website to display properly once it's live.

### How the files work together

The index.html is the blueprint that structures the page, while the images provide the actual visual content. You need both because the HTML tells the browser exactly where and how to display those images to make the site look complete.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, I will configure my S3 bucket for static website hosting and vist the website with a public link.

### Understanding website hosting

Website hosting means putting my files on a server so they have a public URL that anyone can visit.

### How I enabled website hosting

I went into the bucket properties, scrolled down to the Static Website Hosting section, and clicked edit to enable it.

### Access Control Lists (ACLs)

An ACL is a a set of rules that decides who can get access to a resource. I enabled ACLs because I want to manage access for each object in my bucket individually.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

The bucket website endpoint is the unique web address AWS creates so anyone can actually view the site in their browser. It acts as the public link that points directly to my hosted files.

### What I saw when I tested the endpoint

I saw a 403 Forbidden error message because S3 buckets are private by default. Even though I enabled hosting, I still need to update the permissions to let the public actually see the files.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, I am updating the bucket permissions to resolve the 403 Forbidden error and make the website publicly accessible. I'm disabling the Block all public access setting and adjusting the Access Control Lists (ACLs) so anyone with the link can view the site.

### How I resolved the 403 error

I resolved the error by turning off the Block all public access setting and then selecting the files to Make public via ACL. This changed the permissions from private to public, allowing the browser to finally load the site.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

### What I did in this extension

In this project extension I'm about to set up a bucket policy that stops people from deleting my index.html file.

### Understanding bucket policies

An alternative to ACLs are bucket policies. These are JSON-based rules that apply to the entire bucket. The benefit of using bucket policies is that I can manage permissions at scale with more flexibility. ACLs are useful for managing access for specific, individual objects within the bucket.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

My bucket policy protects the site by preventing anyone from deleting the index.html file. It specifically denies the s3:DeleteObject action for that file while still allowing the rest of the site to function normally. This adds a layer of safety so the core of my website stays intact.

---

---


<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Zain Syed  
**Email:** zainalabideen2006@gmail.com

---

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

I am here today to launch and configure a virtual server using Amazon EC2. My goal is to host a web server and learn how to manage cloud computing resources directly.

### Tools and concepts

I learned how to launch and manage Amazon EC2 virtual servers and use IAM to control user access. Key concepts included using Tags to organize resources, creating Account Aliases for easier login, and writing JSON Policies to restrict specific actions like ec2:StopInstances on production servers.

### Project reflection

It took me about one hour to complete the project. The most rewarding part was seeing the JSON policy actually work when the production instance blocked my "Stop" request, confirming my security setup was solid.

---

## Tags

### What I did in this step

In this step, I will launch two Amazon EC2 instances so that I can increase the computing power.

### Understanding tags

Tags like labels you can attach to AWS resources for organization. They are useful for tracking costs and managing large groups of resources without getting confused.

### My tag configuration

I am using the Key Env with the Value production for my first instance and development for the second. This helps me separate my live environment from my testing space.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will create an IAM policy that gives access to the development instance but not the production instance. This is to make sure changes are not pushed to the production enviroment on accident.

### Understanding IAM policies

IAM Policies are rules that give permissions to IAM users, groups, or roles, saying what they can or can't do on certain resources.

### The policy I set up

For this project, I’ve set up a policy using JSON

### Policy effect

I’ve created a policy that allows some actions (like starting, stopping, and describing EC2 instances) for instances tagged with "Env = development" while denying the ability to create or delete tags for all instances.

### Understanding Effect, Action, and Resource

In a JSON policy, Effect specifies if the rule is an "Allow" or a "Deny." Action lists the specific AWS service tasks being permitted or blocked, like s3:GetObject. Resource identifies the exact AWS object the policy applies to using its Amazon Resource Name (ARN).The Effect, Action, and Resource attributes of a JSON policy means...

---

## My JSON Policy

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I am creating an AWS Account Alias to replace my long, numeric Account ID with a custom, easy-to-remember name. This makes the IAM login URL much simpler for me to use

### Understanding account aliases

An Account Alias is a custom name that replaces the default 12-digit AWS Account ID. It makes the IAM login URL much easier to remember by turning a string of numbers into a recognizable name.

### Setting up my account alias

It only took a few seconds. I just navigated to the IAM dashboard, clicked Create, and typed in my custom name.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I am creating an IAM Group and IAM User for my new intern. By adding the user to this group, I can manage permissions for all future interns in one central place rather than configuring them one by one.

### Understanding user groups

IAM user groups are a collection/folder of IAM users.

### Attaching policies to user groups

Attaching the policy to the IAM Group automatically grants those permissions to every IAM User I add to it. It ensures all my interns get the same access instantly without me having to configure them individually.

### Understanding IAM users

IAM users are unique identities I create within my AWS account to represent specific people or applications. Each user has their own set of security credentials, like a password or access keys, so they can sign in and interact with AWS resources securely.

---

## Logging in as an IAM User

### Sharing sign-in details

I can share a new user's sign-in details by emailing the instructions directly from the AWS console, which sends the sign-in URL and username. Alternatively, I can download a .csv file that contains the username and password to share with them securely.

### Observations from the IAM user dashboard

In my new IAM user's AWS dashboard, I observed that I could view both instances, but I was only able to perform actions on the development instance.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I am logging in as the IAM user I created to verify that the permissions are working correctly. I'll test their access by attempting to stop both the development and production instances. This confirms the intern can only manage the resources they are authorized to use, while being restricted from sensitive production systems.

### Testing policy actions

I tried to stop both instances to test my permissions.

### Stopping the production instance

When I tried to stop the production instance, the action was blocked and I received an "Encoded Authorization Failure Message." This proved that the IAM policy I attached to the group was working correctly, as it only allowed control over the development instance while denying access to production.


![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

When I tried to stop the development instance, the action was successful, and the instance state changed to "Stopping."

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

In this secret mission, I am using the IAM Policy Simulator to test user access. This tool allows me to verify that my JSON policies are working correctly without having to log in and out of different accounts, ensuring the intern's permissions are exactly where they need to be.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a sandbox for testing JSON policies without touching real resources. It lets you verify that specific permissions, like your development tag, work as intended before they go live. It’s the best way to troubleshoot "Access Denied" errors safely and ensure your security boundaries are solid.

### How I used the simulator

I set up a simulation for the development instance using the ec2:StopInstances action. The results were Allowed, showing that the permission logic works for the development environment. I had to adjust the context keys in the simulator to include the Env tag with the value development to get the green light.

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-security-iam_069d8a621)

---

---
