---
layout: post
title: "The Truth About Folders in Amazon S3 Buckets"
date:   2024-01-24 14:16:28 +0000
categories: "AWS"
excerpt_image: https://cdn.skeddly.com/Blog/aws-s3-folders-1.PNG
image: https://cdn.skeddly.com/Blog/aws-s3-folders-1.PNG
---

### Searching Through Millions of Objects is Expensive  
When listing all objects in an S3 bucket through the aws cli, the costs can add up quickly. Each 1000 list requests costs $0.005 in us-east-1 region. For millions of objects, it would cost $5 just to retrieve the complete list. **While the aws cli is useful for smaller buckets,** it is not practical for extremely large datasets. Some creativity is needed to reduce costs by excluding known objects from the ls command. After all, what is a developer's time worth?

![](https://i0.wp.com/ipwithease.com/wp-content/uploads/2019/08/img_5d62ce8b55c00.png?resize=545%2C390&amp;ssl=1)
### A Database Index is Needed to Query Large Amounts of Data  
S3 is great for storage, but very expensive to search through at scale. Instead of searching directly in S3, **a metadata database like DynamoDB or a SQL database** should be used to index and query object metadata outside of S3. This allows searching without incurring list request fees from S3. However, populating such an index from scratch requires an initial scan of the bucket.  
### Use S3 Inventory to Seed a Metadata Database
If no preexisting index exists, S3 inventory can be leveraged. S3 inventory exports a CSV file containing a full or filtered inventory of the bucket on a daily/weekly basis. This file can then be used to initially populate the metadata store. Tools like AWS Athena or Redshift Spectrum can query the CSV directly as well. Over time, the index stays in sync with changes in S3 through event notifications.
### "Folders" Don’t Exist - It’s All Just Object Names
While folders may be displayed, S3 is completely flat—there is no hierarchical structure. All that exists are object names that sometimes contain path-like delimiters. **Searching within a "folder" name is no faster than a normal prefix search.** Developers just need to include the full path in queries to locate objects under that "folder".
### Inventory Features Keep Metadata and Storage in Sync
For buckets that already contain data, incremental inventory files keep the metadata database up-to-date with any changes. When new objects are added, modified or deleted in S3, the inventory process picks up those changes to sync the metadata store. **This prevents expensive full rescans and maintains an accurate view of objects stored in S3.**
### Summary 
In summary, while S3 provides scalable storage, its design as a flat object store means it is inefficient for large-scale searching. Maintaining accurate metadata in a separate database through techniques like inventory and event notifications allows querying objects without paying list request fees. This hybrid approach maximizes the strengths of both services for any size data set.
 ![The Truth About Folders in Amazon S3 Buckets](https://cdn.skeddly.com/Blog/aws-s3-folders-1.PNG)