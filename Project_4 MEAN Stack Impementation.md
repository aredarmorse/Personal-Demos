# MEAN means MongoDB ExpressJS Angular & Node.JS


<!-- I utilised AWS EC2 as my Linux portion of the stack. I used an Ubuntu 20.04 LTS server, any Linux distro would equally work.!-->

To update the OS repositories, I ran the following codes

```bash
sudo apt update
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/apt%20update.png)

To upgrade the OS, I ran the following codes

```bash
sudo apt upgrade
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/apt%20upgrade.png)

### *__Step 1 -  Node.js Installation.__*

To Install the Node.js software, I ran the following codes


```bash
sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates

curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/add%20certificates.png)

> To add certificates, and

```bash
sudo apt install -y nodejs
```
> To install Node.js software.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/install%20node.png)

### *__Step 2 -  MongoDB Installation.__*

I installed the MongoDB by running the following code;


```bash
sudo apt install -y mongodb-org
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/install%20mongodb.png)

> The procedures followed can be found [here](https://www.cherryservers.com/blog/how-to-install-and-start-using-mongodb-on-ubuntu-20-04)

```bash
mongod --version
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/mongod%20version.png)
> I ran this to verify the MongoDB installation.

I then proceeded to start the server, and verify same by running the following codes

```bash
sudo service mongod start
```

```bash
sudo systemctl status mongod
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/start%20server.png)


#### Install npm – Node package manager.

```bash
sudo apt install -y npm
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/install%20npm.png)
>To install npm, I ran the command above,

To install body-parser package, I ran the code below

```bash
sudo npm install body-parser
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/install%20NPM%20body-parser%20.png)

I then went ahead to create a folder named `Books`, navigate to the `Books` directory and initialized an npm project by running the folowing commands;

```bash
mkdir Books && cd Books
```
```bash
npm init
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/npm%20init.png)

I added a file to the directory named `server.js` 

```bash
vi server.js
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/populate%20server.js.png)
> Popluated the `server.js` file as above.


### *__Step 3 - Install Express and set up routes to the server.__*

Mongoose is a package which provides a straight-forward, schema-based solution to model our application data. I will use Mongoose to establish a schema for the database to store data of our book register.

```bash
sudo npm install express mongoose
```
> I ran the above command to insatll mongoose.

From the `Books` folder, I created a folder named `apps`, and created a `routes.js` file in this new directory by running the following commands.

```bash
mkdir apps && cd apps
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/apps%20and%20routes.png)

```bash
vi routes.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/routes.js.png)
> I poplulated the routes.js file as above.

From the `apps` folder, I created a folder named `models`, navigated to the folder and created a `books.js` file by running the following commands;

```bash
mkdir models && cd models
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/models%20and%20books.png)

```bash
vi book.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/books.js.png)
> I poplulated the books.js file as above.

### *__Step 4 – Access the routes with AngularJS.__*
> AngularJS provides a web framework for creating dynamic views in  web applications. In this project, I made use of AngularJS to connect my web page with Express and perform actions on my book register.

I navigated to the `books` directory by running the command below.
```bash
cd ~/Books
```
I then went ahead to create a folder named `public`, navigated to the folder, created and populated a file named `script.js` with some lines of code using the `vi` command.

```bash
mkdir public && cd public
```
```bash
vi script.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/public%20and%20script.png)

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/script.js.png)
> I poplulated the script.js file as above.

In the same `public` folder, I also created and populated an  `index.html` file with some lines of code using the `vi` command.

```bash
vi index.html
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/index.html.png)

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/indexhtml.png)
> I poplulated the index.html file as above.

I navigated back to the `Books` folder, and started the server by running the following commands.

```bash
cd ..
```
> To navigate to the Books folder.

```bash
node server.js
```
>To start the server.


![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/start%20node%20server.png)

Running the `curl -s http://localhost:3300` returned the content of the `index.html` to my terminal screen as shown by the image below.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/curl%20localhost.png)

I also verified the status of the server by visiting the public IP address of my server, and i was able access and interact with my Web Book Register APplication as shown by the pix below.
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/website.png)
>Before populating my DB

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/4.%20Project%204%20MEAN%20Stack%20Implementation/DB%20populated.png)
>After populating my DB.







