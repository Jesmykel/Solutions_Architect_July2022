# Task 2: Create Amazon S3 bucket with bucket policies and life cycle management

1. Launch AWS Console

I launched AWS console from the navigation bar

2. Create a S3 bucket with enforced ownership

I created S3 bucket and enforced bucket ownership

![create bucket](Image/create%20bucket.jpg)

3. Create a single lifecycle policy

I craeted a lifecycle policy that Permanently delete noncurrent versions of objects after 5days

![lifecycle policy](Image/lifecycle%20policy.jpg)

![lifecycle policy](Image/lifecycle%20rule%20enable.jpg)

4. Create a single bucket policy

I craeted a single bucket policy under "permission" that enables MFA for a bucket object

![bucket policy](Image/bucket%20policy.jpg)

![bucket policy](Image/bucket%20policy%20enabled.jpg)

5. Delete all policies

I deleted the policies i created from tasks (3) and (4) above

![delete policies](Image/delete%20policies.jpg)

6. Delete S3 bucket

I deleted the jesmykel bucket

![delete bucket](Image/delete%20bucket.jpg)



For guide, kindly visit

https://docs.aws.amazon.com/cli/latest/reference/s3api/create-bucket.html

https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html

https://docs.aws.amazon.com/cli/latest/userguide/cli-services-s3-commands.html
