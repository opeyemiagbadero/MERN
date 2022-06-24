
I spun up a server on the AWS console.

![0  chmod and ssh into the  server](https://user-images.githubusercontent.com/79456052/175547455-755960f8-ba35-4b48-af1b-1f1ecc50f847.png)

sshed into the server and carried out an update and upgrade on the server

![1  sudo apt update](https://user-images.githubusercontent.com/79456052/175547618-a632bcd5-e307-45ec-ad95-a5a1301fd1b3.png)

![2  sudo apt upgrade](https://user-images.githubusercontent.com/79456052/175547634-732e5a0f-28f5-4f9d-bdfe-173ac4a477d8.png)

I installed Node.js on the server using the command *sudo apt-get install -y nodejs* , followed by the verification of the  the node followed by
locating the Node.js software from Ubuntu repositories and installed Node.js on the server.

![3  Get Node js from ubuntu repo](https://user-images.githubusercontent.com/79456052/175549727-914831b6-b309-4337-ad64-13edab068581.png)


![4 install node js ad npm on the server](https://user-images.githubusercontent.com/79456052/175550031-5e953616-f7cb-4bc3-ba4f-a9adc7490914.png)

In setting up the application code, I created a new directory for the To-Do project, used the command npm init to initialise the  project 
so that a new file named package.json will be created.

![5  Create the Todo folder,  run the npm init cmd to initialise the project](https://user-images.githubusercontent.com/79456052/175551504-37a68984-4826-4207-80ec-cce85e9fd0a6.png)

I installed express using the *npm install express* command, created an index.js file, installed the dotenv module, opened the
index.js file and copied the codes in the documentation into the index.js file.  I confirmed that the server was running on port 5000, after editing the inbound rules of the security group of the EC2 to allow traffic  through
port 5000.

![6  Install express using npm, create abd index js file and and type the code given in the documentation into it  Confirm eeverything has workeout well so far by typing node index js and confirm that the server is running on port 5000](https://user-images.githubusercontent.com/79456052/175553026-dbec2fba-e821-43c0-b48a-2f38fda0b4e7.png)

![7  Edit the Security Group and add a rule to include port 5000](https://user-images.githubusercontent.com/79456052/175553659-a0c92f27-4b87-4fa7-bb31-da07276f1cf0.png)


I opened up my browser to access the server’s Public IP  followed by port 5000:

![8  8  Access the server's public ip address name followed by port 5000 on a browser](https://user-images.githubusercontent.com/79456052/175554004-f0d68742-5282-4861-85f8-00191e61c3ca.png)

Routes
There are three actions that our To-Do application needs to be able to do:

1. Create a new task
2. Display list of all tasks
3. Delete a completed task

Each task will be associated with some particular endpoint and will use different standard HTTP request methods: POST, GET, DELETE.
For each task, we need to create routes that will define various endpoints that the To-do app will depend on. 
 
To achieve the three actions needed by the to-do application,  I created a folder called routes, added a file called api.js and copied a set of
configuration codes from the documentation into the api.js file and saved.

I created a models directory, and a todo.js file within the directory, copied the configuration codes from the documentation into the file and saved.
 
 ![9  Install Routes and Model directories](https://user-images.githubusercontent.com/79456052/175557506-1710cd30-1072-444b-ab5f-6abe1622d8db.png)


I created an account on mongodb for storing our data, Allowed access to the MongoDB database from anywhere (Not secure, but  ideal for testing)
and the connection string to access the database in a .env file located in the Todo directory.

DB = 'mongodb+srv://opegbadero:<password>@<network-address>/?retryWrites=true&w=majority'
  
![13  Create a database user](https://user-images.githubusercontent.com/79456052/175559878-6101e115-4a1e-478e-ae6f-b12cb99c1973.png)

![15  Allow access to the MongoDB from anywhere  (Not secure, for a  production environment)](https://user-images.githubusercontent.com/79456052/175559879-64356286-ade4-40a1-a2c7-6597373408b2.png)
  
![16](https://user-images.githubusercontent.com/79456052/175559880-80b3288a-9ea1-423d-954a-cb17f3c46150.png)
  
 I updated the index.js to reflect the use of .env so that Node.js can connect to the database by deleteing the prexisting content in the file and update it the 
entire code found in the documentation.
  
I started the server by using the command  *node index.js* and confirmed that the databse had connected successfully.

  
![18  creata file in to Todo dir, name it  env and addt the connection string to access the database  in it  Ensure to update the username, password   network address  Update d index js file by copying   replacing d set of config in d file wth d one in ](https://user-images.githubusercontent.com/79456052/175561302-401a3a17-4ae5-4159-a2da-f282a280d4be.png)

 I used the postman software to test our API, set the  header key Content-Type as application/json and initiated a POST and GET request.


![32Install and open Postman  create a request which sends a new task to our todo list so d app can store it on the database](https://user-images.githubusercontent.com/79456052/175562464-361ded62-b48b-49b7-b3e7-12b25690391b.png)


![33  Create a GET request on the API that retrieves all existing records from the To-do application](https://user-images.githubusercontent.com/79456052/175562466-748f551d-3ad1-4a72-9575-c80f57f3a017.png)


  
In creating the Frontend, I ran the npx create-react-app client command  in the Todo directory, which created a folder called client and added the react codes.
Before testing the react app, I installed the concurrently and nodemon dependencies followed by deleting a part of the package.json file in the Todo directory
and replacing it with the codes in the documentation.




![33a  STEP2 FRONTEND CREATION  In the same root directory as the backend code which is the Todo dir,  run the npx create-react-app client command to  create a client  folder in the Todo directory so as to add al the react code](https://user-images.githubusercontent.com/79456052/175564216-d25660bb-faf5-4d18-9ee5-ab74803fe505.png)



![33b  Install concurrently which runs more than one command simulteneoulsy from the same terminal window and nodemon used to run and monitor the server](https://user-images.githubusercontent.com/79456052/175564234-7740219e-890a-44e4-a454-b27ad946cad0.png)


![33c  In the Todo folder open the package json file and replace the highlighted part of the screenshot in the doc with the  codes given in the documentatiion](https://user-images.githubusercontent.com/79456052/175564261-2b3af37d-1fb0-4079-9756-b44f54046f11.png)


 I opened the package.json file under the client directory and added key value pair in the package.json file "proxy": "http://localhost:5000" to the file and saved, followed by edting the inbound rules of the server on the AWS console
 to accept all traffic from port 3000
  
  ![Screenshot 2022-06-24 at 17 44 37 1](https://user-images.githubusercontent.com/79456052/175607853-2d58d68f-797d-4790-8806-e1be399c4fa4.png)
  
 I ran the npm run dev command in the Todo directory and ran the app on localhost:3000 i.e 18.212.53.235:3000

![38](https://user-images.githubusercontent.com/79456052/175565551-fa2dbe00-ea5b-4452-b5d0-5a05117003a5.png)

 In an attempt to create my react components, I created a components folder in the src folder and created three files Input.js, ListTodo.js and Todo.js. I opened the 3 files one after the other
 and copied the codes in the documentation into the file and saved.
  
 ![33d  In creating the React Components, run the cd client from the Todo directory run, move into the src directory and create a components folder  create the input js, ListTodo js and Todo js files om the components dir  Open the input js file and past](https://user-images.githubusercontent.com/79456052/175574538-57341a9c-4699-4c5a-8b5d-fbcc9650b216.png)

I made an adjustment to our react code so as to delete the logo and adjust our App.js by copying  the codes in the documentation into the App.js. I also opened the  App.css and index.css files and 
copied the codes in the documentation into the files and saved.

I ran  the npm run dev in the Todo directory and refresh the localhost:3000 i.e http://18.212.53.235:3000 to confirm that the application is  ready and fully functional with the functionality  of creating a task, deleting a task and viewing all the tasks.  
  
  
![44](https://user-images.githubusercontent.com/79456052/175577675-ddc3dba1-4735-4811-b1f8-def523b8ba38.png)






