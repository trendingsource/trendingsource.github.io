---
layout: post
title: "Customizing Error Pages in AWS with S3 and CloudFront"
date:   2024-02-26 03:56:36 +0000
categories: "DevOps"
excerpt_image: https://d1tcczg8b21j1t.cloudfront.net/strapi-assets/s3_diagram_cloudfront_acm_route53_c2a411d6a4.png
image: https://d1tcczg8b21j1t.cloudfront.net/strapi-assets/s3_diagram_cloudfront_acm_route53_c2a411d6a4.png
---

## Leveraging S3 Websites for Custom Error Handling
Amazon S3 offers the ability to host static websites directly from S3 buckets. This includes the capability to define custom error pages that will be displayed when a 404 Not Found or 403 Forbidden response is generated. By configuring a CloudFront distribution to use an S3 bucket as its origin, this allows for centralized error page configuration with CloudFront's high performance content delivery.
### Configuring an S3 Bucket as a Website
S3 allows buckets to be configured as static websites through setting the appropriate properties. To enable this functionality, select the bucket and navigate to the Properties tab. Under Static Website Hosting, choose the index and error document you wish to use. Common options are index.html for the index page and 404.html or error.html for the 404 error document. Enabling this converts the bucket to act as a static website origin. 

![](https://www.bluematador.com/hubfs/Guardian DevOps/blog/Negative TTL in AWS Cloudfront/negative-ttl-in-aws-cloudfront.jpg)
### Creating Custom Error Documents
With the bucket configured as a website, custom error pages can now be hosted directly within the bucket. Simply upload the HTML files you wish to use for the 404 and 403 errors. **S3** will automatically serve these pages when a visitor encounters the corresponding error code. This provides full control over the look and messaging of error experiences. Common elements included on custom pages are a description of the error, suggestions to fix it, and links back to the site homepage.
## Routing Traffic through CloudFront 
After setting up the S3 origin with custom error handling, CloudFront can be leveraged to efficiently deliver those pages to users globally. To do so, create a new CloudFront **distribution** and configure the S3 bucket as the origin. Leave the default cache behavior and custom error response settings. Visitors will now have their traffic routed through CloudFront which will in turn fetch resources like the custom error pages from S3. Any 404s or 403s encountered will display the pretty error pages rather than the basic browser defaults.
### Monitoring for Errors
While custom pages improve the user experience for errors, it does not provide insights into what is causing them. S3 server access logging can be configured to log all requests, including errors, to a log file in the bucket. From there, tools like AWS Lambda and Athena can analyze these logs for 4xx and 5xx response codes. Any sudden increase in a specific error could indicated an issue needing attention. The logging also allows tracking overall error rates over time.
## Summary
By leveraging Amazon S3's website hosting capabilities along with CloudFront's CDN, it is possible to have beautifully designed, customized error experiences for any site. Configuring S3 to serve static pages and custom error documents allows full branding and messaging control. Coupling that with CloudFront ensures low latency global delivery of those resources. The combination empowers building polished digital experiences, even during unplanned outages or visitor mistakes. **S3** and CloudFront work seamlessly to prevent faceless default pages from negatively impacting users and systems.
 ![Customizing Error Pages in AWS with S3 and CloudFront](https://d1tcczg8b21j1t.cloudfront.net/strapi-assets/s3_diagram_cloudfront_acm_route53_c2a411d6a4.png)