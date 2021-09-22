updated 8-4-2020

In the next lecture, Stephen will be going over how to install Create React App globally and generate the application.
This method of generating a React project is no longer recommended.

Instead of this:

npm install -g create-react-app

create-react-app frontend

We need to run this command:

npx create-react-app frontend

Documentation:

https://create-react-app.dev/docs/getting-started#npx

If you've previously installed create-react-app globally via npm install -g create-react-app,
we recommend you uninstall the package using
npm uninstall -g create-react-app to ensure that npx always uses the latest version.







3-22-2020

Due to a recent update in the Create React App library, we will need to change how we start our containers.

In the upcoming lecture, you'll need to add the -it flag to run the container in interactive mode:

docker run -it -p 3000:3000 -v /app/node_modules -v $(pwd):/app f84a41654ab3b886136023b44fb24628030b0d9e40638b7b96e20c2bd218c948




4-1-2020

Recently, a bug was introduced with the latest Create React App version that is causing the React app to exit when starting with Docker Compose.

To Resolve this:

Add stdin_open property to your docker-compose.yml file

  web:
    stdin_open: true
Make sure you rebuild your containers after making this change with  docker-compose down && docker-compose up --build

https://github.com/facebook/create-react-app/issues/8688

https://stackoverflow.com/questions/60790696/react-scripts-start-exiting-in-docker-foreground-cmd