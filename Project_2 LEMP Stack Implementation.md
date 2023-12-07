# LEMP means NGINX Mysql PHP

 ## 1.  **Linux**

> I utilised AWS EC2 as my Linux portion of the stack. I used an Ubuntu server, any Linux distro would equally work.

To update the OS repositories, I ran the following codes

```bash
sudo apt update
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/Update.png)


## 2. **Nginx**

To Install the nginx (web) server, I ran the following codes

```bash
sudo apt install nginx
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/Install%20nginx.png)

And I ran the following code to verify the nginx installation and status

```bash
sudo systemctl status nginx
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/verify%20nginx%20install.png)

To verify if the nginx server is up and running, i just grabbed the Public IP address of the Linux system from the AWS EC2 consoloe and put it in the browser and the (default) page below is displayed

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/verify%20nginx%20working.png)

## 3. **Mysql**

To install a mysql-server which will serve as the database of the stack, I ran the following codes

```bash
sudo apt install mysql-server
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/install%20mysql-server%20.png)

To verify mysql-server is running and to change the password for the root user:

```bash
sudo mysql 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'NEWPASSWORD';
exit
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/mysql%20config.png)

For additional security config, i ran the command below, and responded to the prompts as neccessary

```bash
sudo mysql_secure_installation
```

## 4. **PHP**
To install PHP and all dependencies for both  mysql and Apache, I ran the following codes

```bash
sudo apt install php-fpm php-mysql
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/PHP%20Installation.png)

And when prompted, I hit the Y button and pressed ENTER to confirm installation.

>I ran a sequence of codes to do the following:

1. create the root web directory for projectLEMP.
2. Change the ownership of the created directory.
3. Open a new configuration file in Nginx’s sites-available directory using the nano command-line editor.

```bash
sudo mkdir /var/www/projectLEMP 
```
```bash
 sudo chown -R $USER:$USER /var/www/projectLEMP
```
```bash
sudo nano /etc/nginx/sites-available/projectLEMP
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/codes.png)

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/LEMP%20config%20file.png)

>I also ran another batch of codes to do the following:
1. Activate my configuration by linking to the config file from Nginx’s sites-enabled directory,
2. Test my configuration for syntax errors,
3. Disable default Nginx host that is currently configured to listen on port 80,
4. Reload Nginx to apply the changes.


I also confirmed the creation of the configuration file by running:

```bash
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
```
```bash
sudo nginx -t
```
>This should return a "...syntax is ok" message if all went well.
```bash
sudo unlink /etc/nginx/sites-enabled/default
```
```bash
sudo systemctl reload nginx
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/codess.png)

I created a simple index.html file to serve as the root of the new website by running:

```bash
sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlemp/index.html

```

I then verified if the websites are served by the new web directory by inpuuting the Public IP address in a browser, and the result was the page below, which is a graphical representaion of the simple index.html that was written. 

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/LEMP%20nginx%20webpage.png) 

>This shows that websites are being served by the preojectlemp web root directory.

To test if the nginx can correctly serve .php files, I created a test PHP file in the document root,

```bash
sudo nano /var/www/projectLEMP/info.php
```
and inserting the following text into the file.

```bash
<?php
phpinfo();
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/PHP%20info%20file.png) 

To verify this, I added the  __*/info.php*__ suffix to the Public IP address of the Linux system.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/PHP%20verfied.png) 

>The result is a web page containing detailed information about the server as shown above.

As the page generated contains sensitive information about the PHP server, it was deleted after reviewing the information on it by running the command below.


```bash
sudo rm /var/www/your_domain/info.php
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/more%20codes.png) 

## 5. **Retrieving Data from Mysql Database With PHP**

 I connected to the Mysql console by running the command
 ```bash
 sudo mysql -p
 ``` 
 I then went ahead to supply the password set for the root user of the Mysql console.
 
 I then ran a series of command to achieve the following:
 
 1. Create a Database named sampleDB,
 1. Create a new user called samleUSER, and 
 1. give this sampleUSER permission over the sampleDB.

  ```bash
 mysql> CREATE DATABASE sampleDB;
 ``` 
  ```bash
 mysql>  CREATE USER 'sampleUSER' IDENTIFIED WITH mysql_native_password BY 'P@ssword1';
 ``` 
  ```bash
 mysql> GRANT ALL ON sampleDB.* TO 'sampleUSER'
 ``` 
  ```bash
 mysql> exit
 ``` 

 ![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/create%20sample%20DB.png)

 ![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/create%20sample%20user.png) 

 To login to the Mysql console as the newly created user, i ran the code below.

 ```bash
 mysql -u sampleUSER -p
 ```
 > I then put in the password used when creating the user when promted.

 Next, I created a test table named *todo_list*. From the MySQL console by running the following statement:

```
CREATE TABLE sampleDB.todo_list (
mysql>     item_id INT AUTO_INCREMENT,
mysql>     content VARCHAR(255),
mysql>     PRIMARY KEY(item_id)
mysql> );
```

I inserted a few rows of content in the test table. by running the **INSERT** command a few times using different values

```
mysql> INSERT INTO sampleDB.todo_list (content) VALUES ("My first important item");
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/write%20to%20DB.png)

To confirm that the data was successfully saved to the table, I ran:

```bash
mysql>  SELECT * FROM sampleDB.todo_list;
```
> And the output was as shown below.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/view%20DB%20table.png)

After validating entries to the database, i exited the mysql console.

Using nano text editor, I then created a `.php` script that will connect to MySQL and query for content. 

```bash
nano /var/www/projectLEMP/todo_list.php
```

I created this  new PHP file in my custom web root directory and saved the script below in it:

```bash
<?php
$user = "sampleUSER";
$password = "P@ssword1";
$database = "sampleDB";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/2.%20Project%202%20LEMP%20Stack%20Implementation/DB%20to%20PHP.png)

Finally i grabbed the Public IP address of the Linux system again and append */todo_list.php* as a suffix, and the browser returned the content of the todo_list Table in the sampleDB earlier created as shown below.

![Screenshot](https://github.com/ardamz/PBL/blob/edd20ea5402a7d08e5e15c22b89064f64203daad/PROJECT%202:%20LEMP%20images/graphical%20view%20of%20DB%20in%20PHP.png)
