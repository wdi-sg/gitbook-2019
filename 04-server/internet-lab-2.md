# Internet Lab 2

Putting things on the internet.


## The Web Is a Big Collection of HTML Pages / resources on the Internet

We've seen how the network of the internet transports things, but what is it transporting?

The World Wide Web, or "Web" for short, is a massive collection of digital pages: that large software subset of the Internet dedicated to broadcasting content in the form of HTML pages. The Web is viewed by using free software called web browsers.

Born in 1989, the Web is based on hypertext transfer protocol, the language which allows you and me to "jump" (hyperlink) to any other public web page. There are over 65 billion public web pages on the Web today."

- Taken from [About Tech](http://netforbeginners.about.com/od/i/f/What-Is-The-Internet.htm)


### Step 1: Checkout the local network.

When you connect to the wifi you are connected to the local network.

You are protected from the "real" internet because it's more secure and because there are not enough addresses to give out.

Use your terminal to discover the IP assigned to you by the local network.
```
ifconfig
```

Find out what the internet thinks your IP is.
[https://whatismyipaddress.com/](https://whatismyipaddress.com/)

### Step 2: Serve some files.
Download and install a simple node file server.
```
npm install -g http-server
```

Run the `http-server` in your wdi files directory.
```
cd ~/wdi
http-server
```

Go to your localhost address and see your files: [http://127.0.0.1:8080](http://127.0.0.1:8080)

Take a minute to browse around and see what's there.

Run a command to make this request **from your terminal**

```bash
curl 127.0.0.1:8080
```

Why do you get this result?

### Step 3: Bypass the local network.
Now, bypass this local network so that you have an IP on the public internet.

We'll be using `ngrok`.

Follow the instructions here: [https://ngrok.com/download](https://ngrok.com/download)

Start `ngrok` from your terminal (what directory you are in doesn't matter)

When you've donwloaded the file and unzipped it, run it from that directory.

```
cd my-download-directory
./ngrok http 8080
```

### Step 3.5: Start your server for a file

Find or download an image file or gif that you like and want to share.

Make sure that *directory does not have anything sensetive in it!*

Example: `bird.jpeg` which is in the directory /Users/akira/documents/bird.jpeg

*Open a new terminal window*

Start the server in that directory so that the image file can be served.
```
cd ~/documents
http-server
```

The URL would look like this: http://127.0.0.1:8080/bird.jpeg

You can now replace `127.0.0.1` with the URL given to you by ngrok.

Example: `http://0362a557.ngrok.io/bird.jpeg`

### Step 3.6: Create text files to serve
Create a `.txt` file in that directory using sublime.

Serve the file. 

Test it at [http://127.0.0.1:8080/file.txt](http://127.0.0.1:8080/file.txt)

Try it on the command line.

```bash
curl 127.0.0.1:8000/file.txt
```

### Step 3.7: Create HTML files to serve
Create an HTML file in that directory. (It could be your unit 1 project !?)

Serve the file.

### Step 4: Test it out!
1. Send the URL in slack to others in class.
1. Open the URL on your cell phone's data connection ( a connection from the outside internet )
1. Send it to friends outside of class.
1. Browse the files in that directory.
1. Try it with the `curl` command.

### Step 5: Ports
1. Open a new terminal (leave the other one open)
1. `cd` to the directory with your files
1. run `http-server` on a different port: `http-server -p 7655`
1. See it on your computer: `http://127.0.0.1:7655`
1. Send the new IP port to people

#### Extra:
What other files can you put in that directory and serve?
You can't make a curl request for an image, but what files can you make a curl request for?
