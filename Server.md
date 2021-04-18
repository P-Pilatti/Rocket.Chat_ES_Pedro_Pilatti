
Server.md
# Deploying Rocket.Chat Server – Installing in my own server.

## I chose to create a Hyper-V Virtual Machine with Linux Ubuntu 20.04 as my server.

# 1. Create VM:
 1.1. Enable Virtualization in BIOS and restart the computer.

 1.2 Enable the Hyper-V role through setting > Right click on the Windows button > Apps and Features > Programs and Features > Turn Windows Features on or off > Select Hyper-V role > Restart de computer.

 1.3. Run Hyper-V > New > Virtual Machine > Load Linux Ubuntu 20.40 ISO and install the SO.

# 2. Install Rocket.Chat Server on Ubuntu using snaps:
2.1. Run Terminal and Install snap:

``` 
$ sudo snap rocketchat-server 
```
 
Then browse to http://localhost:3000 and create user at Rocket.Chat. 

# 3. Exposing localhost.
For this I used ngrok, it’s a reverse proxy that creates a secure tunnel from a public endpoint to a locally running web service. More information hete -> Install ngrok on Arch Linux using the Snap Store | Snapcraft
 ``` 
 $ sudo snap install ngrok
 ```
3.1. Expose localhost to the internet.
The ngrok documentation can be found here -> ngrok – documentation
 ``` 
 $ ngrok http 3000
 ```
When started ngrok, it’ll display a UI in the terminal with the public URL 
![UI](https://user-images.githubusercontent.com/82692186/115153874-6f4ad300-a04e-11eb-8ca2-44b87b2ab184.png)
This URL can be accessed on any network.
3.2. Tunneling only HTTPS.  
``` 
$ ngrok http -bind-tls=true localhost:3000
```
![httpsUI](https://user-images.githubusercontent.com/82692186/115154035-3bbc7880-a04f-11eb-9269-015704c4b2fc.png)
 
Only forward HTTPS traffic.
On the free plan, ngrok’s URLSs are randomly generated and temporary. 

