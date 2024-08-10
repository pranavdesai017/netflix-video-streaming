Here's a summary of how to configure a static website on Amazon S3 with CloudFront:

### Configuring a Static Website on S3

1. **Sign In to AWS Management Console:**
   - Go to the [AWS Management Console](https://aws.amazon.com/console/) and sign in.

2. **Navigate to S3:**
   - Type "S3" in the search bar and select the S3 service.

3. **Create a New Bucket:**
   - Click on "Create bucket".
   - Enter a unique bucket name and select a region close to your users.
   - Set the appropriate permissions, including making the bucket public if needed.

4. **Set Permissions for Public Access:**
   - Go to the Permissions tab of your bucket and add a bucket policy allowing public access.
   - Example policy:
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Sid": "AddPerm",
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
         }
       ]
     }
     ```

5. **Enable Static Website Hosting:**
   - In the Properties tab of your bucket, enable static website hosting and set the index document (e.g., `index.html`).

6. **Upload Website Files:**
   - Go to the Objects tab, click "Upload", and upload your static website files (HTML, CSS, JavaScript, images, etc.).

### Setting Up CloudFront

1. **Go to CloudFront:**
   - Access the CloudFront service in the AWS Management Console.

2. **Create a CloudFront Distribution:**
   - Click "Create Distribution" and choose "Web" as the delivery method.
   - In the "Origin Domain Name", select your S3 bucket.
   - Set "Default Root Object" to `index.html`.

3. **Create an Origin Access Control (OAC):**
   - Create a new OAC to secure your S3 bucket by restricting direct public access.

4. **Update S3 Bucket Policy:**
   - CloudFront will provide a new bucket policy. Update your bucket policy with this new policy to allow CloudFront access while blocking public access.

5. **Finalize and Access:**
   - After creating the distribution, CloudFront will provide a domain name. Use this domain to access your website.

6. **Verify Your Website:**
   - Paste the CloudFront domain name into a browser to see your website.

For additional details on each step, refer to AWS documentation:
- [Amazon S3 Documentation](https://docs.aws.amazon.com/s3/index.html)
- [Amazon CloudFront Documentation](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

Feel free to ask if you need further clarification or have additional questions!