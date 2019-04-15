# AWS EC2

## Create Your Instance

1. From your [AWS Console](https://console.aws.amazon.com/console/home), type `EC2` in the search bar. This will send you to the EC2 dashboard.

![](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-search-bar.png?raw=true)

2. From the EC2 Dashboard, click "Launch Instance"

![](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-launch-instance-btn.png)

3. Choose the default image. You can click through the "Qick Start" options. It should indicate "free tier eligible".

4. Click "Launch"

6. After that a modal window will prompt you to either create or choose an
   existing `.pem` file.  
  - Create a new one:
    1. Choose "Create a new key pair"
    2. Ideally give it a lower case name with no spaces.
    3. Click "Download key pair". AWS won't let you click "Launch Instances" until you download your key pair
    4. Using terminal, you'll need to `cd` to the directory that the .pem file is
      in and type the following: `chmod 400 YOUR-PEM-FILE.pem`

7. Click the link to take you to your instance page.

8. Eventually you'll see a green dot next to your instance, letting you know
   it's ready. Take note of of the "Public DNS" line. You'll use that url to
[[SSH|SSH]] into your instance.

## Uploading your files

Go to your [EC2 Dashboard](https://console.aws.amazon.com/ec2/v2/home).

Click on '# Running Instances' ([Screenshot](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-1.png))
**NOTE**: If you need to create an instance, click [[here|Creating-an-EC2-Instance]]

Click the checkbox of the instance in question ([Screenshot](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-2.png))

Copy the Public DNS to your clipboard ([Screenshot](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-3.png))

### SCP from your computer to EC2

In your terminal, navigate to the directory your .pem file is in

```bash
scp -i THE-DIR-YOUR-PEM-FILE-IS-LOCATED/YOUR-PEM-FILE.pem THE-FILE-YOU-WANT-TO-SCP.csv ec2-user@PASTE-YOUR-PUBLIC-DNS-HERE:~/
```

**NOTE**: The `:~/` at the end of the DNS specifies which directory on the EC2 instance you want to transfer to. In this case, you're wanting your file to live in the home directory (hence the tilde).

## ssh

Go to your [EC2 Dashboard](https://console.aws.amazon.com/ec2/v2/home).

Click on '# Running Instances' 

Click the checkbox of the instance you want to SSH in to ([Screenshot](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-4.png))

Copy the Public DNS to your clipboard.

In terminal, navigate to the directory your .pem file is in

```bash
ssh -i the-directory-your-pem-file-is-located/YOUR-PEM-FILE.pem ec2-user@PASTE-YOUR-PUBLIC-DNS-HERE
```

You've successfully SSH'ed if you see the following:

```

       __|  __|_  )
       _|  (     /   Amazon Linux AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-ami/2017.03-release-notes/
1 package(s) needed for security, out of 1 available
Run "sudo yum update" to apply all updates.
[ec2-user@ip-172-31-12-226 ~]$ 
```

If you see `Run "sudo yum update" to apply all updates.` then run: 
```
sudo yum update
```

### Unprotected key file

If you see the following warning when trying to SSH:
```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'YOUR-PEM-FILE.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "dsi.pem": bad permissions
Permission denied (publickey).
```

Type the following:
```bash
chmod 400 YOUR-PEM-FILE.pem
```

After that, try the `ssh` command again.
