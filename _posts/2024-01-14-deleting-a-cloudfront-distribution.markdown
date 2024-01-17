---
layout: post
title: "Deleting a CloudFront Distribution"
date:   2024-01-14 10:16:58 +0000
categories: "Tech"
excerpt_image: https://s3browser.com/images/delete-cloudfront-distribution/cloudfront-manager-disable-distributions.png
image: https://s3browser.com/images/delete-cloudfront-distribution/cloudfront-manager-disable-distributions.png
---

CloudFront is an AWS service that provides global content delivery network (CDN) services. With CloudFront, users can distribute static and dynamic web content, as well as streaming media files, and applications at high speed with low latency. 
## Understanding CloudFront Distributions
A CloudFront distribution is a collection of edge locations where content and its metadata are cached. This allows visitors to download content from locations that are closest to them, improving performance. 
Some key points about CloudFront distributions:
- Distributions have a **state** that can be **enabled** or **disabled**. Enabled distributions actively serve content from edge locations. 
- The **status** indicates if updates are currently being deployed such as **in progress**. Or have been fully applied with **deployed**.
- Each distribution has a unique identifier called an **ID** that can be used to reference it in APIs and the console.
### Propagating Distribution Changes 
Because content needs to be distributed globally across all edge locations, it takes time for changes made to distributions to propagate fully. This includes disabling or enabling a distribution as well as other configuration updates. During propagation, the status will show as in progress until deployed. 

![](https://s3browser.com/images/delete-cloudfront-distribution/ready-to-delete-distributions.png)
## Disabling a Distribution
Before a CloudFront distribution can be deleted, it must first be disabled. This is necessary because edge locations around the world may still have cached content that needs to be invalidated. 
To disable a distribution:
1. Find the distribution in the CloudFront console and select the checkbox.
2. Choose the **Disable** option and confirm. 
3. The state will immediately update to **disabled** but propagation may still occur for a few minutes as indicated by the status.
## Deleting a CloudFront Distribution
Once a distribution has been successfully disabled and fully propagated, it can then be permanently removed. 
To delete a disabled CloudFront distribution:
1. In the CloudFront console, select the checkbox for the disabled distribution.  
2. Choose the **Delete** option and confirm removal.
3. The distribution will no longer appear in the console after deletion.
### Using the CloudFront APIs
For programmatic or automated deletion of distributions, the CloudFront API can also be utilized. The **DeleteDistribution** API takes the distribution ID as a parameter and removes it once disabled. This allows easy integration with other systems and tools.
Proper planning should be done before deleting distributions to avoid unintentional removal that could break websites or applications. And it is important to understand how long propagation may take after disabling before deletion is possible.
 ![Deleting a CloudFront Distribution](https://s3browser.com/images/delete-cloudfront-distribution/cloudfront-manager-disable-distributions.png)