# Serverless Development with AWS Amplify 🛠 Part: 01

Today in this article I am going to dive into hands on development with Amplify. I will try to point out few basics to get started with AWS Amplify development. I am going to wrap up this within these 5 steps to follow up and get a clear idea about the flow on how Amplify is used to configure, connect and automate the deployment to get a custom domain to see the final result.

## Create IAM User as Admin

Don't ever use ROOT user to create repo or for any other configuration on console. Create an IAM user with all Admin access and use that to create new repo in CodeCommit and use that user CodeCommit credential to clone the repo.

Make sure you select the same AWS Region where your CodeCommit Repository is and where you want to create your Amplify application.

![aws01](https://user-images.githubusercontent.com/47071968/179140260-d2ed2933-8466-4fae-a3c3-19f2d4e52179.png)


## Create React project and test locally first.

For this example I am going to use this github [react landing page](https://github.com/imranxpress/landy-react-template).


After you cloned the repo, run this command outside of the repo folder:

~~~
npx create-react-app REPO_NAME --template adrinlol

cd  REPO_NAME

npm start
~~~

If last command opens up your browser with a landing page then your project is running good and you are good to go for next step. if not then you are may be having issues with either Node installation in your system.


### Try checking out this Pre-requisites for installation.

Install [ Node.js®](https://nodejs.org/en/download/)and [NPM](https://docs.npmjs.com/getting-started) if they are not already on your machine.
Verify that you are running at least Node.js version 10.x and npm version 6.x or greater by running node -v and npm -v in a terminal/console window.

### Add, Commit and Push git changes to remote repository.

Run these commands to check out your repo status and add + commit + push the recent changes to the repo:
~~~
git status

git add .

git commit -m "initial commit with react landing page code"

git push origin master 
~~~

Place your credentials from the AWS admin user and push the code.

### Configure the Amplify App and connect the repository.


1.Launch the [Amplify Console page](https://aws.amazon.com/amplify/hosting)

 2.Click Get Started under Deploy with Amplify Console.

 3.Click for "New App" button and choose "Host Web App" button.

![aws02](https://user-images.githubusercontent.com/47071968/179143364-12668a67-9ee3-4f78-a049-ba193ee23036.png)


Select the Repository service provider used today and select Next.


![aws03](https://user-images.githubusercontent.com/47071968/179143473-4126f066-3dde-42f9-a8a7-47cc1aa8b74f.png)


If you used GitHub, you'll need to authorize AWS Amplify to your GitHub account. In our case CodeCommit repository.

From the dropdown select the Repository and Branch just created.

![aws04](https://user-images.githubusercontent.com/47071968/179143682-105a8daf-df88-40f7-8ace-a4ea12c68b5c.png)

On the "Configure build settings" page leave all the defaults and select Next.

![aws05](https://user-images.githubusercontent.com/47071968/179143769-95faa4a0-dd88-4204-8793-162aa51ea00b.png)

On the "Review" page select Save and deploy:
![aws06](https://user-images.githubusercontent.com/47071968/179144166-89c5b6fc-a5fa-470e-92f7-a7a6feb3fe21.png)


The process takes a couple of minutes for Amplify Console to create the necessary resources and to deploy your code.

![aws07](https://user-images.githubusercontent.com/47071968/179144277-13065418-f542-4582-8b0c-a03b024a70d2.png)


### Can you see the Build #2 here? It's because I got an issue in my Build #1 while I had to provide the Amplify IAM role attached to this new app for the specific repo.

Congrats you have deployed your first Serverless Application on AWS with AWS Amplify. You can check out your frontend on the Domain provided by AWS Amplify on the above screenshot. And remember this is a fully managed and fully automated CI/CD for your application. 


To check this automated CI/CD feature just change anything on the frontend and push your code to the remote repository in the same branch which is connected to this Amplify Application.You will notice the pipeline started to running automatically...

### This is all for the day. Hope you enjoyed the whole article and hope to continue this further for adding up Backend features like [REST APIs, Lambda Functions, Static Storages, DynamoDB DataStores etc] to this Amplify app step by step going forward.





