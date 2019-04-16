# AWS EC2

## Sign Up for AWS
[https://aws.amazon.com/](https://aws.amazon.com/)

## Create Your Instance

1. From your [AWS Console](https://console.aws.amazon.com/console/home), type `EC2` in the search bar. This will send you to the EC2 dashboard.

![](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-a.png?raw=true)

2. From the EC2 Dashboard, click "Launch Instance"

![](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-b.png?raw=true)

3. Choose the default image. You can click through the "Qick Start" options. It should indicate "free tier eligible".

4. Click to `Configure Security Group`. Add `http` - it will configure to port 80 automatically.
![](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-5.png?raw=true)

5. Click to "Launch"

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

## ssh

Go to your [EC2 Dashboard](https://console.aws.amazon.com/ec2/v2/home).

Click on '# Running Instances' 

Click the checkbox of the instance you want to SSH in to ([Screenshot](https://github.com/wdi-sg/gitbook-2019/blob/master/images/ec2-4.png?raw=true))

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

Once you can log into the instance, prepare it for the express app:

```
sudo yum update
sudo yum install git
sudo su - root
```

Install nvm - instructions from here: [https://github.com/creationix/nvm](https://github.com/creationix/nvm)

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
```

```
source ~/.bashrc
```

```
nvm install node
```

#### Setting up your own App

Fork this express basic app on github: [https://github.com/wdi-sg/express-basic](https://github.com/wdi-sg/express-basic)

Clone it to your computer.

So that you know that it's yours, make a single change in the app. `response.send` something different. Commit those changes and push them to your github repo.

Then inside the AWS instance, clone it, install the dependencies and start the app.

```
git clone [https://github.com/<YOUR USER>/express-basic.git]
cd express-basic
npm install
node index.js 80
```

Copy the "Public DNS" from the AWS console. Paste it into the browser to see your running app.

See the request handler `console.log` in the ssh terminal.

### pairing exercise
Repeat the above steps
