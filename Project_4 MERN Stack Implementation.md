# MERN means MongoDB ExpressJS ReactJS & Node.JS

 ##  **STEP 1 – BACKEND CONFIGURATION**

<!-- I utilised AWS EC2 as my Linux portion of the stack. I used an Ubuntu server, any Linux distro would equally work.!-->

To update Ubuntu, I ran the following codes

```bash
sudo apt update
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/Update.png)

To upgrade the OS, I ran the following codes

```bash
sudo apt upgrade
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/Upgrade.png)

### *__Node.js Installation__*

To Install the Node.js software, I ran the following codes

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
> To locate the Node.js software from Ubuntu repositories.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/locate%20nodejs.png)

```bash
sudo apt-get install -y nodejs
```
> To install the located Node.js software, and NPM which serves as a package manager for Node. It is used to install Node modules & packages and to manage dependency conflicts.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/install%20nodejs%20&%20npm.png)

And I ran the following code to verify the Node.js and NPM installation.

```bash
node -v
```
```bash
npm -v
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/node%20&%20npm%20verification.png)

### *__Application Code setup__*
I created a folder called Todo, navigated into the folder using the `mkdir` and `cd` commands respectively, and initialised my project by running the `npm init` command as shown below

```bash
mkdir Todo
```
```bash
cd Todo
```
```bash
npm init
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/npm%20initialize.png)

> I followed on screen prompt and pressed enter till the `package.json` file was created.

I ran the `ls` commmand to verify the creation of the package.json file.
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/package.json%20confirmed.png) 

### *__Install ExpressJS__*

To install the ExpressJS framework for Node.js

```bash
npm install express
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/install%20express.png)

After the installation , i created an index.js file using the `touch` command and also used the `ls` command to verify creation of said file.

```bash
touch index.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/touch%20index.png) 


Using the vim text editor, i saved some code in the index.js file as shown below.

```bash
vim index.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/vim%20index.js.png)

I tried starting my server by running the `node index.js` command but i got an error of a missing module. Using npm which is the package manager for node i was able to install the missing module, and was ab le to start the server.

```bash
npm install dotenv
```
```bash
node index.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/6e74a7e2b9dc58d5b7df61f3cb8cd8521e6bb662/3.%20Project%203%20MERN%20Stack%20Implementation%20copy/starting%20the%20server.png)

After seeing that my server was up and running i  decided to verify this using my browser. i used the puublic IP address of the EC2 along with the port number returned earlier.

But for this to work i had to enable the specific port on the EC2 as it is disabled by default for security reasons.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/111841864814ae5b5e1979c0bdec10f1befa7b96/3.%20Project%203%20MERN%20Stack%20Implementation/SG%20updated.png)

> I got the `Welcome to Express` message in the browser, which verifies that the server is working.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/111841864814ae5b5e1979c0bdec10f1befa7b96/3.%20Project%203%20MERN%20Stack%20Implementation/server%20verified%20in%20browser.png)

### ***Routes***
I will require the Todo app to carry out three tasks,
1. Create a new task,
2. Display list of all tasks and
3. Delete a completed task

Each task will be associated with some particular endpoint and will use different standard HTTP request methods: POST, GET, DELETE.

For each task, I created routes that will define various endpoints that the Todo app will depend on. 

> To achieve this, I ran a sequence of codes to do the following:

1. created a routes folder,
1. navigated to the routes folder,
1. created a api.js file using the `touch` command and
1. saved some lines of code to the the api.js file using `vim`.

```bash
mkdir routes
```
```bash
cd routes
```
```bash
touch api.js
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/5473c6bafc11ffd7e213fd528e641132a294b2b5/3.%20Project%203%20MERN%20Stack%20Implementation/create%20routes%20folder.png)

```bash
vim api.js
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/5775b14af80c6a16e1cf1a7f1d7bca3143b13d8a/3.%20Project%203%20MERN%20Stack%20Implementation/api.js%20populated.png)

### ***MODELS***

To create a model that wil be used to define the schema of the mongoDB used for this app, I ran a sequence of codes to do the following:

1. Navigated back to the `Todo` folder.
1. install mongoose using the node package manager.
2. Create a new directory called `models`.
3. Navigate into the new folder, and created a `todo.js` file in the models folder using the  `touch` command.

```bash
cd .. 
```
```bash
npm install mongoose
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/5473c6bafc11ffd7e213fd528e641132a294b2b5/3.%20Project%203%20MERN%20Stack%20Implementation/install%20mongoose.png)

```bash
 mkdir models && cd models && touch todo.js
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/5473c6bafc11ffd7e213fd528e641132a294b2b5/3.%20Project%203%20MERN%20Stack%20Implementation/create%20models%20folder.png)


Using the vim text editor i saved the code below to the file;
```bash
vim todo.js
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/3eaaf08b1a1b13469665ab2941adf1d482b9d99d/3.%20Project%203%20MERN%20Stack%20Implementation/todo.js%20populated.png)

I then ran the following codes;
 ```bash
cd ~/Todo/routes
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/3eaaf08b1a1b13469665ab2941adf1d482b9d99d/3.%20Project%203%20MERN%20Stack%20Implementation/navigate%20to%20routes.png)


> To navigate back to the `routes` folder, and
 ```bash
vim api.js
```
 ```bash
:%d
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/3eaaf08b1a1b13469665ab2941adf1d482b9d99d/3.%20Project%203%20MERN%20Stack%20Implementation/api.js%20modified.png)

> This was to basically replace the previous content of the `api.js` file using the vim text editor.

### ***MongoDB DATABASE***
I needed a database where my data will be stored. For this, I will make use of [`mLab`](https://www.mongodb.com/atlas-signup-from-mlab). 

After signing up on the platform, I completed a getting started checklist, and in the process I carried out the following;
1. create a DB user and granted permission to the new user.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/create%20DB%20User.png)


2.  I allowed access to the MongoDB DB from anywhere *(Not ideal/recommended for a prodution enviroment, but it is ideal for testing).*

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/IP%20Access%20List.png)

3. Created a cluster using AWS as my cloud platform.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/create%20a%20cluster.png)

4. Created a DB and collection.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/Create%20DB%20and%20Collection.png)


5. Accessed my DB connection string by clicking on the `connect` button on the database page.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/get%20.env%20string.png)


I created a `.env` file and saved my DB connection string to it, as a `process.env` was specified in the `index.js` file to access environment variables.

```bash
touch .env
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/1ba3d7a3317b564b2de70243c234581914482113/3.%20Project%203%20MERN%20Stack%20Implementation/create%20.env%20file.png)

```bash
vi .env
```
> And the connection string to access the database in it, just as below:

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/latest%20.env%20file.png)


I then updated the content of the `index.js` file by
1. Running the `vim index.js` command,
1. Pressing the esc button,
1. Typing `:`, followed by
1. Typing `%d` and
1. Hitting the ***Enter*** button.
1. Hit `i` button to enter the insert mode in vim,
1. And finally pasting the entire code block below in the file.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/1ba3d7a3317b564b2de70243c234581914482113/3.%20Project%203%20MERN%20Stack%20Implementation/update%20index.js.png)

8. I then started my server by running the code below, and I got a `Database connected successfully` message as displayed below.

```bash
node index.js
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/final%20node%20index.js%20cmd.png)

### ***Testing Backend Code without Frontend using RESTful API***
Using `Postman`, I tested all the API endpoints to make sure they are working. For the endpoints that required a body, I sent JSON back with the necessary fields since it’s what I will be setting up in my code.

#### POST API Test
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/POST%20API%20Test%20OK.png)
> POST API test finally OK, had some fits with the url, but all sorted in the end.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/POST%20Test%20verified%20in%20MongoDB.png)

>  POST API also verified in  MongoDB (an entry was `posted` in the DB).


#### GET API Test
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/GET%20API%20Test%20OK.png)

>GET API Test Ok, this was quite straight forward.

#### DELETE API Test
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/DELETE%20API%20Test%20Ok.png)

> DELETE API test finally OK, had to send the request with the id to verify what content to delete.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/GET%20after%20DELETE.png)
> Running the GET API call after the DELETE API returned an empty body which is expected.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/DELETE%20verified%20in%20MongoDB.png)
> DELETE API call also verified in the MongoDB.

##  **STEP 2 – FRONTEND CREATION**

I created the user interface (frontend) of my my application using Reactjs. this interacts the DB at the backend using API. navigating to the `Todo` folder of my server, i ran nthe command below.
```bash
npx create-react-app client
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/create-react-app%20client.png)

This created a new folder in my `Todo` directory called client, where all the react code will be added.

### ***Running a React App***
before proceeding, I installed the `concurrently` and `nodemon` dependencies by running;

```bash
npm install concurrently --save-dev
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/Install%20concurrently.png)
> This is used to run more than one command simultaneously from the same terminal window.


```bash
npm install nodemon --save-dev
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/Install%20nodemon.png)
> While this is used to run and monitor the server.

I also edited the package.json file.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/package.json%20before.png)
> `package.json` before any changes.


![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/package.json%20after.png)
> After the value of the `scripts` key has been changed.

I also navigated to the `Todo/client` dirctory and also edited the package.json file by adding the key value pair below,

```json
"proxy": "http://localhost:5000"
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/client:package.json%20before.png)
> Before editing.


![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/client:package.json%20after.png)
> After editing.

Running the command below, I was able to verify that my app was up and running
```bash
npm run dev
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/npm%20run%20dev%20command.png)

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/npm%20run%20dev%20successful.png)

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/React%20verified.png)
> Verification that my app will run in a browser after my EC2 Security Groups to allow TCP traffic on port 3000.

### ***Creating the React Components***

From the `client` directorty, i moved to the src directory and created another directory called `components`, and created three (3) files named `Input.js`, `ListTodo.js` and `Todo.js` in the `components` directory.

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/mkdir%20components.png)

Using the nano text editor, i saved the below text to the `Input.js` file.

```bash
import React, { Component } from 'react';
import axios from 'axios';

class Input extends Component {

state = {
action: ""
}

addTodo = () => {
const task = {action: this.state.action}

    if(task.action && task.action.length > 0){
      axios.post('/api/todos', task)
        .then(res => {
          if(res.data){
            this.props.getTodos();
            this.setState({action: ""})
          }
        })
        .catch(err => console.log(err))
    }else {
      console.log('input field required')
    }

}

handleChange = (e) => {
this.setState({
action: e.target.value
})
}

render() {
let { action } = this.state;
return (
<div>
<input type="text" onChange={this.handleChange} value={action} />
<button onClick={this.addTodo}>add todo</button>
</div>
)
}
}

export default Input
```

I then moved back to the `client` directory and installed `axios` which is a Promise based HTTP client for the browser and node.js by running;

```bash
npm install axios
```
After that, by running the following commands,

```bash
cd src/components
```

```bash
nano ListTodo.js
```

I navigated back to the `components` directory and used the nano text editor to save the below text to the `ListTodo.js` file.

```bash
import React from 'react';

const ListTodo = ({ todos, deleteTodo }) => {

return (
<ul>
{
todos &&
todos.length > 0 ?
(
todos.map(todo => {
return (
<li key={todo._id} onClick={() => deleteTodo(todo._id)}>{todo.action}</li>
)
})
)
:
(
<li>No todo(s) left</li>
)
}
</ul>
)
}

export default ListTodo
```

![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/ListTodoJS.png)

Then i also saved some text to the `Todo.js` file by running the command below

```bash
nano Todo.js
```

```bash
import React, {Component} from 'react';
import axios from 'axios';

import Input from './Input';
import ListTodo from './ListTodo';

class Todo extends Component {

state = {
todos: []
}

componentDidMount(){
this.getTodos();
}

getTodos = () => {
axios.get('/api/todos')
.then(res => {
if(res.data){
this.setState({
todos: res.data
})
}
})
.catch(err => console.log(err))
}

deleteTodo = (id) => {

    axios.delete(`/api/todos/${id}`)
      .then(res => {
        if(res.data){
          this.getTodos()
        }
      })
      .catch(err => console.log(err))

}

render() {
let { todos } = this.state;

    return(
      <div>
        <h1>My Todo(s)</h1>
        <Input getTodos={this.getTodos}/>
        <ListTodo todos={todos} deleteTodo={this.deleteTodo}/>
      </div>
    )

}
}

export default Todo;
```
![Screenshot](https://github.com/ardamz/PersonalDemos/blob/main/3.%20Project%203%20MERN%20Stack%20Implementation/TodoJS.png)

To make some final adjustment to the view of the front end, i edited the `App.js`, `App.css` and `index.css` file in the `src` directory. navigating to the `src` directory
