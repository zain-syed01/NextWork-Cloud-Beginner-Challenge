<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Zain Syed  
**Email:** zainalabideen2006@gmail.com

---

![Image](http://learn.nextwork.org/contented_red_clever_iara/uploads/aws-host-a-website-on-s3_5d4474f9)

---

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
