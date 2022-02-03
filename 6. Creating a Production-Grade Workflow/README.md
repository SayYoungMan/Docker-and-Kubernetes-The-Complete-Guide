# Creating a Production-Grade Workflow

## Development Workflow Specifics
- Github Repository is the main core of development
- Two branches:
    - Feature branch where the development takes place
    - Master branch is where the clean history is kept
- When committed to master with PR, it will go to Travis CI which will run tests and automatically deploy to AWS hosting

## Docker's Purpose
- Docker is a `tool` in a normal development flow
- Docker makes some of theses tasks a lot easier

## Necessary Commands for React App
- `npm run start` starts up a development server
- `npm run test` runs tests associated with project
- `npm run build` builds a production version of the application

## Docker Volumes
- `Docker volume` will set a mapping from the folder inside the file to folder outside by referencing
- `docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image-id>`
- Colon in `$(pwd):/app` suggests mapping of folder inside the container to the one outside

## Shortcomings on Testing
- Attaching to tests container will not enable you to interact with STDIN or STDOUT
- This is because the process we attached to is not the process that is running the test

## Need for Nginx
- In Dev Environment, there is Dev server that gives you right file to the browser
- But in Production, there is no Dev server so we need Production server that reacts to Browser request
- For this purpose, we are going to use `Nginx`