# Image-Compressor-using-AWS-Lambda-and-S3-Bucket
Automated AWS Lambda image compression using S3 buckets. Up to 99.5% size reduction. Easy to integrate in any application.

# Note: If you are using my code please make appopiate changes in provided code such as replacing my s3 bucket names and user access keys With yours.

Here's a step-by-step procedure to create an image optimizer using AWS Lambda and S3 buckets:

1. **Create an AWS Account:**
   If you don't have an AWS account, sign up for one at [https://aws.amazon.com/](https://aws.amazon.com/).

2. **Create S3 Buckets:**
   - Log in to the AWS Management Console.
   - Navigate to the S3 service.
   - Create two buckets: one for the source images and one for the compressed images.

3. **Create IAM Role:**
   - Navigate to the IAM service in the AWS Management Console.
   - Create a new IAM role for your Lambda function with permissions to read from the source S3 bucket and write to the destination S3 bucket.
   - Permissions are 1-AmazonS3FullAccess 2-AmazonS3ReadOnlyAccess 3-AWSLambdaBasicExecutionRole

4. **Create Lambda Function:**
   - Navigate to the Lambda service in the AWS Management Console.
   - Create a new Lambda function.
   - Choose the "Author from scratch" option.
   - Configure the trigger: Choose the source S3 bucket and select the event type (e.g., "ObjectCreated").
   - Configure the function:
     - Name your function.
     - Select the runtime (Node.js 14.x).
     - Choose the IAM role you created earlier.
   - Upload Deployment package after changing source & destination buckets name in JS Code |OR| Write the Lambda function code to compress the image. (You      can use third-party libraries like `sharp` for image processing.)
   - Save and deploy the Lambda function.

5. **Set Up S3 Bucket Event Notification:**
   - Configure an event notification on the source S3 bucket to trigger the Lambda function when an object is created.

6. **Test the System:**
   - Upload an image to the source S3 bucket.
   - Monitor the Lambda function execution in the CloudWatch Logs.
   - Verify that the compressed image is stored in the destination S3 bucket.

7. **Optional: Frontend Interface:**
   - Develop a frontend interface (web application) for users to upload images.
   - Make a IAM User with appropriate Permissions for access key and secret access key as it will be used in interface.
   - Use AWS SDKs (e.g., AWS Amplify for JavaScript) to interact with S3 and trigger the Lambda function.
   - Deploy the frontend to a hosting service (e.g., Amazon S3, AWS Amplify Hosting).

8. **Security and Permissions:**
   - Ensure proper IAM roles and permissions for Lambda, S3, and other AWS resources.
   - Implement encryption for data at rest and during transit.

9. **Monitoring and Scaling:**
   - Set up CloudWatch Alarms to monitor Lambda function performance and errors.
   - Configure Auto Scaling for Lambda if needed.

10. **Optimization and Fine-Tuning:**
   - Optimize the Lambda function code for better performance and cost efficiency.
   - Experiment with different image compression techniques and settings.
