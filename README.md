Secure S3 Bucket Runbook 


Pre-requisites;


  
  -- Access to the console

   --- Network access to the internet


1 Create an Encrypted S3 Bucket


  A. Login to S3 in the AWS Console

  B. Click on “create bucket”

   C. Named my bucket—-”my-s3-littlebucket’’

   D. Scrolled down to Default encryption:

  Select Enable 

  Chose SSE-S3 

  E.    Enabled versioning

  F.    Leave other settings as default.

  G.   Click Create bucket.

![Image 2025-10-20 at 21 06 33](https://github.com/user-attachments/assets/cd89b745-fdfa-482f-a572-6234ae9d5344)


My “my-s3-littlebucket” bucket is encrypted


2.  Enable Versioning


      A.   Go to the new “my-s3-littlebucket”

      B.   Click the Properties tab.

      C.   Scroll to Bucket Versioning.

      D.   Click Edit, choose Enable, then Save changes.

      E.   Versioning is now on.


3.  Block All Public Access


      A.   Go to the Permissions tab of the bucket

      B.   Click Edit next to Block public access.

      C.   Check all four options :

       Block public ACLs

       Block public bucket policies

       Ignore public ACLs

       Restrict public bucket policies

     D.   Click on Save changes.

     E.   Public access is blocked.


![WhatsApp Image 2025-10-20 at 21 26 43](https://github.com/user-attachments/assets/2b8a54ea-52b1-44c1-8605-f6bec4e6d0fa)


4.  Add a Bucket Policy for IP Restriction


     A.   Go to the Permissions tab.

     B.   Scroll down to Bucket policy.

     C.   Click Edit.

Paste this policy, replacing:

  my-secure-bucket with my bucket name; my-s3-littkebucket
    Replaced YOUR_IP_ADDRESS with my actual IP; 54.87.233.162



    {
      "Version": "2012-10-17",
    "Statement": [
    {
      "Sid": "AllowGetFromMyIP",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-s3-littkebucket/*",
      "Condition": {
        "IpAddress": {
          "aws:SourceIp": "54.87.233.162/32"
            }
          }
        }
      ]
    }



   Click Save changes.
     Successfully edited the policy

![WhatsApp Image 2025-10-20 at 21 31 33](https://github.com/user-attachments/assets/06ceaf7d-09b6-4867-a352-8748d7d57b60)


5.  Upload Sample Files via Console


     A.   Go to the bucket– Objects tab.

     B.   Click Upload.

     C.   Upload two files

           report.txt 

           data.csv 
![WhatsApp Image 2025-10-20 at 21 36 36](https://github.com/user-attachments/assets/35e1ce96-f99b-410c-9fbc-29d0f41f5f57)


  D.   Click Upload.

   E.   Files are now in S3.


6. Generate a Pre-signed URL


      A.  In the bucket, find report.txt under Objects.

      B.  Click the checkbox next to it.

      C.  Select Actions; share with a pre-signed URL.

![WhatsApp Image 2025-10-20 at 21 14 08](https://github.com/user-attachments/assets/84ef9629-af0d-4224-9cba-9319864529ab)

  D.  Set expiration time (60  minutes).

![WhatsApp Image 2025-10-20 at 21 14 08](https://github.com/user-attachments/assets/6f3dbb8c-56cd-4eef-a23e-d9df5bad2cd0)

   E.  Copy the generated URL.

![WhatsApp Image 2025-10-20 at 21 13 47](https://github.com/user-attachments/assets/fce6ebce-084e-4f54-88da-52b3a9f74d2e)

   F.  Test it by opening the URL in your browser.

![WhatsApp Image 2025-10-20 at 21 14 24](https://github.com/user-attachments/assets/b3cdb286-cc26-478b-9384-d3f24e5cdcc0)


 7.  Clean Up


     A.   Go to the bucket 

     B.   Empty to delete bucket

![WhatsApp Image 2025-10-20 at 21 14 48](https://github.com/user-attachments/assets/480514e9-27f7-4b96-a79f-e0cd876c52a6)

![WhatsApp Image 2025-10-20 at 21 15 15](https://github.com/user-attachments/assets/fd4ae8e5-8af1-436f-981d-910ce28e8dd5)

  C.   Back to the S3 dashboard, select the bucket.

  D.   Then delete

https://github.com/Adedunni99/Secure-S3-Bucket-Runbook/blob/main/WhatsApp%20Image%202025-10-20%20at%2021.15.15.jpeg?raw=true
