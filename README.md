# Hosting a static website using and Implementing CI/CD

## Overview
In this project, I created a static website which I hosted on AWS using the services like S3, CloudFront. And The website if maintained by using Codepipeline. It is made by keeping in mind about the security of website.


## Architecture

A static website which is getting hosted by S3 bucket. Since the bucket is private, it cannot be accessed by others. In order to reach the endpoint of website, we are using CloudFront. And The code in the S3 bucket is getting maintaned by Codepipeline and github.

AWS services used

- S3
- CloudFront
- Codepipeline

![image](https://github.com/Abhishek9821228/Web-Hosting-and-CI-CD/assets/135989734/00e7c681-bcea-4ca4-a399-698fcf272726)

This Architecture is created in powerpoint.

# Step 1 - Creating a S3 bucket and also hosting out statc website.

In this step, I used AWS S3 to host a website and kept the bucket private, so that no one can access it publically.

    1. I created a new S3 bucket and kept the name of bucket same as my domain.
    2. Kept the bucket private and create the bucket.
    3. Now enable static hosting.
    4. Uploaded the static files (index.html in my case).

(For Domain, I get my domain from freenom website at very less price).



# Step 2 - Now Create a CloudFront and keep the source origin at S3 bucket we created.

In this step, I created cloudfront and connected it to S3 bucket.

    1. Select origin domain, (The S3 bucket endpoint in my case).
    2. Make the cloudfront endpoint public, since it needs to be accessed by other.
    3. In viewer protocal policy, I choosed Redirect from HTTP to HTTPS, such that all HTTP request get redirected to HTTPS.
    4. Select any method. My website was static so it wasn't much of any differnce to choose any method.
    5. I choosed all edge location.
    6. Keep all other values default. (give alterante domain name is needed)
    7. Requested SSL certificate.
    8. Need to verify the domain.


![image](https://github.com/Abhishek9821228/Web-Hosting-and-CI-CD/assets/135989734/82be19ab-5bcf-49ae-af28-92c78eb2b11f)


# Step 3 - Achive CI/CD using Codepipeline.

In this step, I use Codepipeline and github to make change in the bucket whenever a change is made in github.

    1. Choose a name and create new service role.
    2. Choose github as source.
    3. Connect to github.
    4. In the build section, I skip it since no build needs as I have only one HTML file.
    5. Chosse S3 bucket and create it.
    6. Create the pipeline.


![image](https://github.com/Abhishek9821228/Web-Hosting-and-CI-CD/assets/135989734/4cf09a17-a6a7-4cde-bb42-0731b2a9c9ba)

## Challeges
The cloudfront chache has some TTL time, so if we make changes the Bucket will change but the chache will not since the TTL time is not completed.

So if we want to solve this problem then we can change the chace manually too.

## conclusion

We deployed a static website a securly and we have also achived the CI/CD functionality usinf Codepipeline. 
