# Learning Outcomes
In this file I will indicate where and how I have worked on the GP learning outcomes.

## Web application
*You design and build user-friendly, full-stack web applications.*

*User friendly: You apply basic User experience testing and development techniques.*

*Full-stack: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.*

### 1. Why
Making sure your web application is user friendly, is a way to avoid problems in future. By testing the web application you make sure that there are less problems later on. This saves time and money, because problems get more diffucult to fix. 

### 2. React
I learned to make and develop an React application. In our group project we used typescript as our language in React. We used it to make a shopping kart and I was mainly responseble for connecting the shopping cart to the restaurants staff tool. This staff tool is also made using React and typescript.

### 3. API
As told earlier was I responseble for the connecting between the shopping kart and the restaurants staff tool. The two are connected with a Rest calls and websockets. These Rest calls and websockets are made with Springboot. Springboot uses java as an programming language. The shopping kart uses an post request to sent an order to the backend. When the backend receives an order, the websockets send a message to the staff tool. The staff tool then send an get request back to the backend to receive all orders. In the staff tool you can change an order status, when you do this an put request is send to the backend to update the order.

### 4. Individual project
For my individual project I made a vue front-end and a springboot back-end. I used vue with javascript and uses axios to connect to the back-end. This connection is made with Rest calls. The springboot servers are made with java. I have multiple servers, that all use there own mysql database. The connection to the is made with JPA as on orm. I used usability testing to ensure that my web application is user-friendly. 

The link to my individual project: https://github.com/S3Puzzle

## Software quality
*You use software tooling and methodology that continuously monitors and improve the software quality during software development.*

*Tooling and methodology: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.*

### 1. Why
Software quality is an important aspect of coding. If you neglect sofware quality, you can get a lot of problems later on. By making sure to test things regularly, you know instantly when something goes wrong. If you fix mistakes when they happen, you prevent building on these mistakes. This saves a lot of time, because you prevent having to remake big part of the code. 

### 2. Unit and integration tests
In both the group project and in my individual project, I have made unit tests. I made these to regularly test the quality of my software. I also made integration tests for both. These run bigger parts of my project and test the connection between smaller units. For my integration test I used a mockmvc to mimic the frontend making api calls. I make sure the returns of these calls are correct.

These are my tests for one of the servers of my individual project: https://github.com/S3Puzzle/Leaderboard-service/tree/main/src/test/java/com/CasS3/Leaderboard

Test I wrote for the group project: https://github.com/fontys-group3/bestel-service/tree/main/src/test/java/com/groep3/bestel/tests

### 3. Automating tests 
I made a maven workflow in github. This workflow build the application and runs the tests on each push and merge on the main branch. This is the workflow I made for one of the repositories in my personal project:
'''
name: Leaderboard cicd

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    env:
      DB_DATABASE: leaderboard
      DB_USER: root
      DB_PASSWORD: root
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'
        cache: maven
    - name: Set up MySQL
      run: |
        sudo /etc/init.d/mysql start
        mysql -e 'CREATE DATABASE ${{ env.DB_DATABASE }};' -u${{ env.DB_USER }} -p${{ env.DB_PASSWORD }}
    - name: Build with Maven
      run: mvn clean install
    - name: Test with Maven
      run: mvn -B test 
## Agile method
*You choose and implement the most suitable agile software development method for your software project.*

*Choose :You are aware of the most popular agile methods and their underlying agile principles. Your choice of a method is motivated and based on well-defined selection criteria and context analyses.*

### 1. Jira board
In our group project we use jira to manage out project. In jira we keep track of our userstories and we log our time spent. Every sprint we choose the userstories and predict the time needed for them using story point poker. 
![image](https://user-images.githubusercontent.com/49039524/165054590-5130bf44-fabf-4e46-b0d3-973da6ba87f2.png)

### 2. Standup and standdown
Every day we have a standup and standdown. I am the scrum master for the second sprint. As scrum master I am responseble for a smooth standup and standdown. We log the information off this meeting in discord.
![image](https://user-images.githubusercontent.com/49039524/165056092-7166df38-28a6-42f5-bf84-232974fa8c31.png)

### 3. Github project
For my individual project I use github project. On this board I keep track of my userstories. Here I choose which userstory to work on next. I assign the userstories to the right repositories as issues.
![image](https://user-images.githubusercontent.com/49039524/168060287-7cebad44-e5fa-4004-8171-a7beb337815d.png)

## CI/CD
*You design and implement a (semi)automated software release process that matches the needs of the project context.*

*Design and implement: You design a release process and implement a continuous integration and deployment solution (using e.g. Gitlab CI and Docker).*

### 1. Github actions
For both front and backend in my individual project and the group project I use github actions. For the backend it is a maven workflow. In the frontend I use nodejs. These workflows get run when there is a push request or an merge with the main branch. First they install dependencies and build the project, then the test get preformed. 

### 2. Self-hosted runner
I researched how to make a self-hosted runner. In my research I pointed out the advantages of a self-hosted runner. Most importantly being not having to wait for the workflow to be executed. The biggest challenge was setting up the mysql server. The standard git runner is an ubuntu machine, so I had to change the mysql setup from linux to windows.

## Requirements and Design
*You translate (non-functional) requirements to extend existing (architectural) designs and can validate them using multiple types of test techniques.*

*Multipletypes of test techniques: You apply user acceptance testing and stakeholder feedback to validate the quality of the requirements. You evaluate the quality of the design (e.g., by testing or prototyping) taking into account the formulated quality properties like security and performance.*

### Individual project
Using the func

## Business processes
*You can explain simple business processes and relate them to the development of your software project.*

*Simple: predominantly sequential processes with one or two alternative paths.*

*Relate: understanding the relationships between the process and software.*

## Professional

*You act in a professional manner during software development and learning.*

*Professional manner: You develop software as a team effort according to a prescribed software methodology and following team agreements. You are able to track your work progress and communicate your progress with the team.*

*You  independently recognize and decide where your knowledge falls short to solve a software problem and  communicate which new knowledge and skills you need to learn.*

