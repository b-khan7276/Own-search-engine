# Ditch Google!! (build your own PRIVATE search engine)

-  Install Docker on you VM or Cloud 
```bash
sudo apt install docker.io -y
sudo apt install docker-compose -y
```
- You can buy a domain name and change the Cname with the cloud IP
- OR you can just use the localhost

First, log in to Linode and get a server set up running Ubuntu 20.04 LTS


```bash
Check to see if you have any updates by running

sudo apt install && sudo apt upgrade -y
```


Next we need to install Docker by running
```bash
sudo apt install docker.io -y
```
If this command doesn't work, use the commands below
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

Next let's install docker-compose
```bash
sudo apt install docker-compose -y
```


Now we can move to the directory where we want to install Searx
```bash
cd /usr/local
```


Then install Searx using git
```bash
git clone https://github.com/searxng/searxng-docker.git
```


<b> Verify that it copied correctly in to your current directory </b>
![image](https://user-images.githubusercontent.com/58091942/177004514-82c69779-72bd-4840-b39d-0fe950ab33b1.png)

![image](https://user-images.githubusercontent.com/58091942/177004534-cb30f8c8-c942-4f28-a9a3-e70af4481594.png)




Now change in to the new directory

Use the ll command to view the hidden files and make sure the `.env` file is there 





If you are using a public server you can adjust the content of the .env file

Now use nano to edit the file if you are using a public server and want to use a custom hostname or if you want to add an email so it can make you an SSL certificate. 

**If you do not have a custom hostname, put in your IP address in the "SEARX_HOSTNAME" field and leave the "LETSENCRYPT_EMAIL" commented out**


```bash
nano .env
```

![image](https://user-images.githubusercontent.com/58091942/177004540-c7ab4dd8-9eef-4e22-a27f-554ba64b762f.png)



Once you are done exit the file using Ctrl+X hit "Y" and then "Enter"



Run this command to generate a super secret key
```bash
sed -i "s|ultrasecretkey|$(openssl rand -hex 32) |g" searxng/settings.yml
```


Now to start SearX run this command
```bash
sudo docker-compose up -d
```


You should see the output below

Once you see this output, you are good to start up Searx!
```bash
sudo docker-compose up -d
```
Now throw your IP address in to your browser's address bar and you should be able to access your Searx search engine!



Then if you want to tear down your instance, you can either turn off the server or tear it down using this docker command.
```bash
sudo docker-compose down
```
![image](https://user-images.githubusercontent.com/58091942/177004415-55cf0703-f11c-47cd-bf4a-fa3f4cae18dc.png)


