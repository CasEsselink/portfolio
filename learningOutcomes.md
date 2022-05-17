# Learning Outcomes
In this file I will indicate where and how I have worked on the GP learning outcomes.

## Web application
*You design and build user-friendly, full-stack web applications.*

*User friendly: You apply basic User experience testing and development techniques.*

*Full-stack: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.*

### 1. React
I learned to make and develop an React application. In our group project we used typescript as our language in React. We used it to make a shopping kart and I was mainly responseble for connecting the shopping kart to the restaurants staff tool. This staff tool is also made using React and typescript.

### 2. API
As told earlier was I responseble for the connecting between the shopping kart and the restaurants staff tool. The two are connected with a Rest calls and websockets. These Rest calls and websockets are made with Springboot. Springboot uses java as an programming language. The shopping kart uses an post request to sent an order to the backend. When the backend receives an order, the websockets send a message to the staff tool. The staff tool then send an get request back to the backend to receive all orders. In the staff tool you can change an order status, when you do this an put request is send to the backend to update the order.

## Software quality
*You use software tooling and methodology that continuously monitors and improve the software quality during software development.*

*Tooling and methodology: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.*

### 1. Unit and integration tests
In both the group project and in my individual project, I have made unit tests. I made these to regularly test the quality of my software. I also made integration tests for both. These run bigger parts of my project and test the connection between smaller units. For my integration test I used a mockmvc to mimic the frontend making api calls. I make sure the returns of these calls are correct. Below you see some images of my unit and integration tests.

### 2. Automating tests 
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
For both front and backend in my individual project and the group project I use github actions. For the backend it is a maven workflow. In the frontend I use nodejs. 
