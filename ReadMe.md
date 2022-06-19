# Learning Outcomes
In this file I will indicate where and how I have worked on the learning outcomes. I will for every learning outcome explain the importance of the learning outcome. After that I will go through everything I did this semester relating to the learning outcome.

## Table of contents
Group project:
 - [Web application](#Web-application)
 - [Agile method](#Agile-method)
 - [Cultural differences and ethics](#Cultural-differences-and-ethics)
 - [Requirements and Design](#Requirements-and-Design)
 - [Business processes](#Business-processes)
 - [Professional](#Professional)

Individual project:
 - [Web application](#Web-application)
 - [Software quality](#Software-quality)
 - [CI/CD](#CICD)
 - [Professional](#Professional)

## Web application
*You design and build user-friendly, full-stack web applications.*

*User friendly: You apply basic User experience testing and development techniques.*

*Full-stack: You design and build a full stack application using commonly accepted front end (Javascript-based framework) and back end techniques (e.g. Object Relational Mapping) choosing and implementing relevant communication protocols and addressing asynchronous communication issues.*

### 1. Why
Making sure your web application is user friendly, is a way to avoid problems in future. By testing the web application you make sure that there are less problems later on. This saves time and money, because problems get more difficult to fix later on.

### 2. React
I learned to make and develop an React application. In our group project we used typescript as our language in React. We used it to make a shopping kart and I was mainly responseble for connecting the shopping cart to the restaurants staff tool. This staff tool is also made using React and typescript. I was personally responseble for making the frontend for the manager tool. The frontend sends a get request to the server and displays the returned data in a table. 

![image](https://user-images.githubusercontent.com/49039524/174483747-976176c3-5947-4973-bf75-096f0e269a14.png)

The view I made: https://github.com/fontys-group3/Management-view

### 3. API
As told earlier, was I responseble for the connecting between the shopping kart and the restaurants staff tool. The two are connected with a Rest calls and websockets. These Rest calls and websockets are made in Spring boot. Spring boot uses java as an programming language. The shopping kart uses an post request to sent an order to the backend. When the backend receives an order, the websockets send a message to the staff tool. The staff tool then send an get request back to the backend to receive all orders. These orders get divided in drink and food orders. The staff tool has a bar and a kitchen version. The bar displays drinks and the kitchen food. In the staff tool you can change an order status, when you do this an put request is send to the backend to update the order.

The spring boot service I made: https://github.com/fontys-group3/bestel-service

### 4. Individual project
For my individual project I made a vue front-end and a springboot back-end. I used vue with javascript and uses axios to connect to the back-end. This connection is made with Rest calls. The springboot services are made with java. I have multiple services, that all use there own mysql database. The connection to the database is made with hibernate as on orm. I used usability testing to ensure that my web application is user-friendly. 

The link to my individual project: https://github.com/S3Puzzle

### 5. Design

![image](https://user-images.githubusercontent.com/49039524/174486078-a4482e9b-6779-4c2f-aaa0-ee94be6a840d.png)

In the readme of my individual project. I explain how my application works.(https://github.com/S3Puzzle)

## Software quality
*You use software tooling and methodology that continuously monitors and improve the software quality during software development.*

*Tooling and methodology: Carry out, monitor and report on unit integration, regression and system tests, with attention for security and performance aspects, as well as applying static code analysis and code reviews.*

### 1. Why
Software quality is an important aspect of coding. If you neglect sofware quality, you can get a lot of problems later on. By making sure to test things regularly, you know instantly when something goes wrong. If you fix mistakes when they happen, you prevent building on these mistakes. This saves a lot of time, because you prevent having to remake big parts of the code. It also ensures security. This is very important, when working real projects. Finally good software quality increases customer satisfaction. It makes sure everything works as expected and this makes the customer happy.

### 2. Unit and integration tests
In both the group project and in my individual project, I have made unit tests. I made these to regularly test the quality of my software. I also made integration tests for both. These run bigger parts of my project and test the connection between smaller units. For my integration test I used a mockmvc to mimic the frontend making api calls. I make sure the returns of these calls are correct.

These are my tests for the servers of my individual project: https://github.com/S3Puzzle/Leaderboard-service/tree/main/src/test/java/com/CasS3/Leaderboard

https://github.com/S3Puzzle/Name-service/tree/main/src/test/java/com/CasS3/Name

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
      
### 4. Code analyses

I decided on using sonarcloud for my code analyses. This was one of the recommened sites on canvas. I choose this one instead of sonarqub, because sonarcloud gave me the option to import my git repositories for free.

## Agile method
*You choose and implement the most suitable agile software development method for your software project.*

*Choose :You are aware of the most popular agile methods and their underlying agile principles. Your choice of a method is motivated and based on well-defined selection criteria and context analyses.*

### 1. Why
An agile software development method helps to keep track of the project. It makes it clear what has been done and what still needs to be done. In a group it also helps knowing who is doing what. This makes it so that you always know, who is responseble for a certain part of the project. This is convenient to check that everyone is doing their job, but also to know who you need to ask if you don't understand a part of the project. Agile methods help make the feedback loop with the product owners shorter and this makes for a highter quality product. 

### 2. Methods
There are a lot of different agile methods. We use scrum, I will list a few of the most populair alternatives and there characteristics.

#### Extreme Programming
With extrme programming you work in pairs. One does the coding and the other one observes. They often switch. By making someone only focus on observing, you get an very high quality product. Which makes it ideal for project with a high technical risk.

#### Kaban
Instead of using a sprint of 2 or 3 weeks, kaban is based delivering continuously. Using a kaban board the process gets visualized. It is used to look ahead and spot potential bottlenecks and fix these. This way it manages flow. Kaban is based around the goal of a smooth flow of work.

#### Dynamic Software Development Method
This method focuses on frequent delivery. It focusses on delivering high quality work, reliably and on time. There is constant feedback from the customer on the product. It works with a team where everybody has his one role.

#### Scrum
Scrum is the method we are using and it revolves around sprints. These sprints are usually 2 or 3 weeks long. The overall product is broken down in smaller features(user stories). Every sprint sprint some user stories get assigned and delivered at the end of the sprint. Other characteristics of scrum are daily standups, sprint reviews, a demo for the product owner and a retrospective. During the standup team members tell the team, what they did last time and what they are going to do today. During a retrospective the team looks back at last sprint to see what was good and what could have been better.

(https://www.agilebusiness.org/page/whatisdsdm)
(https://www.digite.com/kanban/what-is-kanban/)
(https://www.jigsawacademy.com/blogs/product-management/types-of-agile-methodology/#:~:text=The%20agile%20method%20is%20an,thereby%20encouraging%20flexibility%20to%20changes.)
(https://www.digite.com/agile/agile-methodology/#agile-methodology)

### 3. Jira board
In our group project we use jira to manage out project. At the start of our project we wrote user stories, based on the requirements from the project owners. We put there user stories on our backlog. On the beginning of every sprint we choose which user stories to implement that sprint. To help us to choose the right user stories we use storypoints. When we agree on the storypoint and the user stories we want to implement, we start the sprint. Then we divide the user stories between us. The user stories themselve we divide in to issues. We start working on the issues and log time spent on these issues. After all isseus are done a user story is done. 
![image](https://user-images.githubusercontent.com/49039524/165054590-5130bf44-fabf-4e46-b0d3-973da6ba87f2.png)

### 4. Standup and standdown
Every day we have a standup and standdown. I was the scrum master for the second and third sprint. As scrum master I was responsible for a smooth standup and standdown. During the standup we ask all members of the team what they did last time and what they are going to do that day. During the standdown we ask what was completed and what they were not able to complete that day. All the minutes are saved in discord. These are from standups and down, but also from meetings with teachers and product owners. 
![image](https://user-images.githubusercontent.com/49039524/165056092-7166df38-28a6-42f5-bf84-232974fa8c31.png)

### 5. Github project
For my individual project I use github project. This is a lot simpler tool than jira. This is convinient for a individual project. It has a backlog that I filled with user stories. I assign this user stories to git repositories. When I start working on them I place them in "In Progress". When they are completed, they are placed in "Done".
![image](https://user-images.githubusercontent.com/49039524/168060287-7cebad44-e5fa-4004-8171-a7beb337815d.png)

## CI/CD
*You design and implement a (semi)automated software release process that matches the needs of the project context.*

*Design and implement: You design a release process and implement a continuous integration and deployment solution (using e.g. Gitlab CI and Docker).*

### 1. Github actions
For both front and backend in my individual project and the group project I use github actions. For the backend it is a maven workflow. In the frontend I use nodejs. These workflows get run when there is a push request or an merge with the main branch. First they install dependencies and build the project, then the test get preformed. 

### 2. Self-hosted runner
I researched how to make a self-hosted runner. In my research I pointed out the advantages of a self-hosted runner. Most importantly being not having to wait for the workflow to be executed. The biggest challenge was setting up the mysql server. The standard git runner is an ubuntu machine, so I had to change the mysql setup from linux to windows.

### 3. Code analyses
Like earlier mentioned, I used sonacloud to anlyse my code. I made it run on every merge and push on the main branch, like the rest of my ci/cd pipeline.

### 4. Docker frontend
I added a step in my workflow to build and push to hub.docker. 

    - name: Set up QEMU
      uses: docker/setup-qemu-action@v2
    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v2
    - name: Login to DockerHub
      uses: docker/login-action@v2
      with:
        username: ${{ secrets.DOCKERHUB_USERNAME }}
        password: ${{ secrets.DOCKERHUB_TOKEN }}
    - name: Build and push
      uses: docker/build-push-action@v3
      with:
        push: true
        tags: casesselink/s3frontend:latest
        
The docker repository is casesselink/s3frontend. So you can pull the image from there and then build it on your machine.

docker pull casesselink/s3frontend

![image](https://user-images.githubusercontent.com/49039524/174300391-adb90dee-ddec-468e-8ba7-ee3f10d508c2.png)

![image](https://user-images.githubusercontent.com/49039524/174300485-bf6fabd4-e51f-4b5c-9ef9-e136ffdee3b8.png)

![image](https://user-images.githubusercontent.com/49039524/174300508-4dedcafd-457e-4aaf-9a04-cd5148eb22e3.png)

The container hosts the site on 8080 so I cast it to my localhost:3000.

Frontend git: https://github.com/S3Puzzle/S3Frontend

### Docker backend
In the backend I also push and build an image to hub.docker, but because of mysql they can't be ran. The tests in git action need the localhost url to work and the mysql docker container need the docker.host.internal url. I have spend a lot of time exploring options to fix it,  but I can't find a way to make one of them use a diffent url. I have thougt about using an different url for both of them, but I don't have the means te do this right now. I decided to keep the localhost url, making the docker image non-functional. To show that I do know how to build a container for my service using the docker mysql image, I will demonstraded with a modified version of my backend.

The commands to make the mysql container and link it to the network:

docker run -p 3307:3306  --name mysql_leader -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=leader  mysql

docker network create leader-net

docker network connect leader-net mysql_leader

Normaly you would now use "docker pull casesselink/leaderboard-service", but I will use this inside the project folder:

mvn clean install

docker build . -t leader-service 

![image](https://user-images.githubusercontent.com/49039524/174301607-4dcfe179-45f7-4aac-b045-b54945f1622f.png)

Leaderboard git: https://github.com/S3Puzzle/Leaderboard-service (in application.properties jdbc:mysql://localhost/leaderboard is replaced by jdbc:mysql://docker.host.internal:3307/leader for demo)

## Cultural differences and ethics
*You recognize and take into account cultural differences when working with multi-site teams and are aware of ethical aspects in software development.*

*Recognize:  Recognition is based on theoretically substantiated awareness of cultural differences and ethical aspects in software engineering.*

*Take into account:*

*Adapt your communication, working, and behavior styles to work with other developers from different cultures;* 

*Address one of the standard Programming Ethical Guidelines (e.g., ACM Code of Ethics and Professional Conduct) in your work.  *

### 1. Why
Understanding cultural differences is very important to avoid misunderstandings. Ignorance about cultural differences can result in unintentionaly insulting a team member. It can also cause a lack of clarity on agreements, because of different work habits. Being aware of ethics is important, because you are responible for your finished product. It means that you can be held accountable for ethical violations. 

### 2. What is culture? 
First of all it is important to know what culture is. Culture common practices and behaviour of a group that are past down over generations. An example of culture are traditions and celebrations. Like "Sinterklaas" in the netherlands. Language is often an important difference between cultures. "Gezellig" for example is an important word in dutch culture, but can't be translated to english. These small detail are the reason people often study the culture and language of a country at the same time. Because you need to place them in context to properly understand them.

### 3. Which are well-known dimensions on cultural differences? 
According to Hofstede's cultural dimensions theory there are six dimensions on cultural differences. Originaly there were only four, but a fifth and sixth were later added. The original four dimensions were individualism vs collectivism, uncertainty avoidance, power distance and masculinity vs femininity. Long-term orientation vs. short-term orientation was the fifth and indulgence vs. restraint the last.

#### Power distance index (PDI)
This index measures how easy less powerfull members of a group accept unequel power distribution. The countries that score high on this scale are mainly in southeast asia and south-america. This means that these counties have big differences in power between leaders and followers and this inequality is endorsed by lots in both groups. Austria, Isreal and denmark have the lowest PDI. This means that people are against big differences in power. The Netherlands score on the lower side at this index.

#### Individualism vs collectivism (IDV)
Individualism is focused on taking care of yourself and your direct family. Collectivism is about thinking in interest of the group. This means being loyal to a big group like an extended family. In a collectivism society ties between individuals are closer and looking after each other is very important. Ecuador and Guatemala score very low on this index, meaning they are very collective. The United States on the other hand scores very high, meaning they are very individual. Which is in line with the american dream, that is focused on selfgrowth. The Netherland score also very high on this scale.

#### Uncertainty avoidance (UAI)
Uncertainty avoidance indicates how comfortable people are unstructured situations. Cultures that score high on this scale will have a lot of rules and laws to minimize uncentaint situations. Greece and Portugal score very high on this index. They don't like uncertaint situations and are more conservative. Singapore scores very low. They don't mind a bit of uncertaintly and are more open to innovation and change. The Netherlands are in the middle on this index. 

#### Masculinity vs. femininity (MAS)
In masculin culture people are more assertive and competitive. People have stronger ego's and achievement are important. In more feminin cultures, people are more modest and caring. These cultured are more relationship oriented and focus more on quality of life. Japan scores very high on this index, meaning that it is a very masculin country. They are very competitive and work long hours. All scandinavian countries score very low on this index. They are more focused on quality of life. The Netherlands also scores very low.

#### Long-term orientation vs. short-term orientation (LTO)
Cultures that focus more on long-term, place higher value on education. They are persisent and obligations are emphasized. People from these cultures are more modest. Cultures that focus on short-term on the other hand, have strong convictions. They sell themselves to be taken seriously. They focus on personal steadiness and stability. China scores very high on this index. They focus more on long term gains. Sierra Leone scores very low. They value short term gains and quick results. The Netherlands score is in the middle. 

#### Indulgence vs. restraint (IVR)
Culture that are high on indulgence are optimistic. They focus on freedom and personal happiness. While cultures that are high on restraint are more pessimistic. They have less freedom and more controll. Russia has a very low score on this index. They have a more controlling gouverment and less freedom. The United States score relatively high. They focus a lot on freedom. The Netherlands also score high on this scale.

(https://en.wikipedia.org/wiki/Hofstede%27s_cultural_dimensions_theory#:~:text=The%20original%20theory%20proposed%20four,orientation%20versus%20person%2Dorientation)

(https://clearlycultural.com/geert-hofstede-cultural-dimensions/)

(https://www.mindtools.com/pages/article/newLDR_66.htm#:~:text=4.,predictable%20and%20controllable%20as%20possible.)
### 4. Examples of cultural differences in my study and life.
Our group consisted of only dutch speaking member, so there we no real cultural differences in our group. Samuil did give a workshop on cultural differences early in the semester and we discussed a case there. I do have an example of cultural differences from the past. When I did my introduction at tu/e, we had a couple of romanian guys in our group. Romania and the Netherlands differ a lot on most of the Hofstede's cultural dimensions. One that was very apparent, when talking to them was individualism. The individualsm index of the Netherlands is 80, this is a lot more than the 30 Romania has. They told us, that they and a lot of other romanians came to study aboard to better take care of there families. This is very different then in the Netherlands, where most people decide there study based on self interest.

(https://www.hofstede-insights.com/country/the-netherlands/)
(https://www.hofstede-insights.com/country/romania/)

### 5. Ethics
For the group project we make an application to order in restaurants. This could potentionly cost a part of the waiters their job. This could financially harm them, this would by against the AMC Code of Ethics to avoid to harm others. While you could interpreted is as this, I believe this is not the case. First of all does the app not replace waiters entirely. Food still needs to be brougt to the tables and because people can order faster, this is more work. So I believe that in most cases, the workload would just from taking orders to other responiblities, which in turn make the whole business more efficient. I also believe that our project contributes to society and human well-being. It saves the customer, everytime they come to eat. An order applicaton also makes it very easy to see if there are ingredients, that you have allergies for.

## Requirements and Design
*You translate (non-functional) requirements to extend existing (architectural) designs and can validate them using multiple types of test techniques.*

*Multipletypes of test techniques: You apply user acceptance testing and stakeholder feedback to validate the quality of the requirements. You evaluate the quality of the design (e.g., by testing or prototyping) taking into account the formulated quality properties like security and performance.*

### 1. Why
Translating requirements to design is an important first step in creating a product. Making a design gives you the change to get stakeholder feedback early on. This makes sure that the project is headed in the direction the stakeholder intends. Using disigns to tak into account things like security and performance, makes sure that the endproduct is functional for its intended use.

### 2. User stories
After receiving the case for our project, we started making user stories. After getting feedback on them and implementing that feedback, we added the user stories to our jira backlog. At the start off every sprint we and the product owners agreed on the user stories for the next sprint. We would start working on them. For every user story we write tests. We only consider an user story ready for delivery after passing those tests. If an user story passed all the test, we would demo it to the product owners. They would give feedback and we would implement it. 

### 3. Architecture
Based on our user stories we designed an architecture for our project. In this model we specified a lot of technical details. Like how many web applications and micro servers we were going to use. Where those were responseble for and how we were going to connect them. We had multiple version that we changed based on feedback from the product owners. This is our final version. 
![image](https://user-images.githubusercontent.com/49039524/174452301-237b57e3-7e24-4b66-b4e7-0dcc4d6bbfef.png)

Like you can see there are 3 micro service and 3 web applicatons, they are connected with rest calls and websockets. The management server is not connect for now. We were planning to connect it by sending rest calls from "Web appicatie Personeel" to the management service. Sadly we weren't able to discuss this with the product owners before the end of the semester.

### 4. Security and Performance
There were a few issues regarding security in this project. One was deleting your cookies to avoid payment. Our solution was to save the cookies in the backend, but this is not yet implemented. The other issue was people accesing the ordering website from outside the restaurant. An easy fix would be to check the ip-adress, but we don't want to force people to use the restaurant wifi. We tried to find other solutions, but we couldn't find a solution that suits our needs.
Jira: https://s3groupproject.atlassian.net/jira/software/projects/SP/boards/1

Restaurant Order System Documentation: https://github.com/fontys-group3

## Business processes
*You can explain simple business processes and relate them to the development of your software project.*

*Simple: predominantly sequential processes with one or two alternative paths.*

*Relate: understanding the relationships between the process and software.*


![image](https://user-images.githubusercontent.com/49039524/174286573-01a74471-938b-49b3-b1b2-736b15db720b.png)

### 1. Why
A business processes is a tool that can help you, when making a project. With every action there is the original path and the path we are planning to make. By visualising them we can see, if are path is even better and simpler. By making a business processes, it is clear how the original process worked and how you are going to improve it with your software. You can easily identify the best way to convert the original process to software. 

### 2. Ordering
![image](https://user-images.githubusercontent.com/49039524/174289814-474938d3-7ef1-4c84-aec7-c3355fddc63c.png)

In the original situation a customer decides on what to order. When a waiter comes the customer gives the order and the waiter gets the drink order to the bar and the food order to the kitchen. In our version the customer can directly order and teh order gets automaticly split between the bar and the kitchen. 

### 3. Preparing
![image](https://user-images.githubusercontent.com/49039524/174296605-c7318b40-b0ee-4921-bbd6-180f5b49afd4.png)

Without the use of our software an staff member needs to claim a order take on order on them, with a post it note for example. The orders per table also need to be documented somewhere to keep track of the bill. Our software does this automatic, you just have to claim an order in the tool and can check it off when you are done preparing it. 

### 4. Payment
![image](https://user-images.githubusercontent.com/49039524/174297116-0ceae246-3b35-49b9-bb45-52abdda701f2.png)

When you want the pay using our software, you get the bill on the website and you can pay it digitaly. Without our software you need to ask a waiter to bring you the bill then they need to bring either a pin machine or change. After that they need to print your receipt.

## Professional

*You act in a professional manner during software development and learning.*

*Professional manner: You develop software as a team effort according to a prescribed software methodology and following team agreements. You are able to track your work progress and communicate your progress with the team.*

*You  independently recognize and decide where your knowledge falls short to solve a software problem and  communicate which new knowledge and skills you need to learn.*

### 1. Why
It is essential that everybody acts professional to function as groep. If people fail to honour agreements it is way harder to make progress. Keeping track of work progress and communication are also important in making sure thing get done. People need to be independent in recognizing an deciding what to learn and to do. Doing this makes sure, that you are up to date on the project and know what is going on.

### 2. Cooperation contract
We set this up as a group with agreements that applied for this semester. These agreements were mostly regarding attendance. Being late or absent without reason or without indicating the day before was punished by a strike. After receiving 3 strikes the teacher was informed. There were giving some strikes, mostly for people that overslept, but no one got 3 strikes in a sprint. 

### 3. Attendance 
Early in the semester was absent a number of times. These were with a reason and mostly indicated the day before. So I did not receive strikes for them, but it was still inconvenient. Luckly I haven't been sick since and I have been present for almost every day after the first weeks.

### 4. Communication
Communication between group members like reporting you will be absent was done in discord. This was going mostly great. Communication with teachers and product owners was done in teams and mail. This was a bit chaotic at times, but it got better during the semester. When we were working at school, I think our communiction was great. There was a lot of cooperation and there got a lot done. When we were working online, we had a discord call. People would sit all day in call and if you had questions you could ask them. This worked great.

### 5. New knowledge and skills
For both the gp and ip I had to learn a lot new skills. We had a lot of freedom so I tried a lot of new things. I also don't have much of an ict background, so a lot is new for me. Here are some practical skills I learned this semester:

#### Spring boot
This I used for both gp and ip. I did have some java experience (tu programming course), but I never worked with spring boot or distrubuted systems. Hibernate was also new for me. Last semester we used an orm called ktorm and this was the only experience I had with databases. Hibernate is very different, but easy to get in to. This was the first time for me making an API, I always taught it was very complicated. but it was easy to pick up. 

#### Github action 
I never used it before and it started easy, but during the semester I have spend quite sometime solving problems with github actions. Setting up the mysql was quite challenging. It works for test and it is very convenient to instantly see bugs. This skill will certainly save more time in the futere than that it cost to learn. 

#### Mock mvc
For both my ip and gp I wrote unit tests and integration tests. Unit tests I had written before, but integration tests were new. It costs some time to get the mock mvc working, but it tests a lot more than just unit tests.

#### Vue
For my ip frontend I used vue. I never used vue or javascript so I had a lot to learn. I learned to make a simple page and even used router for multiple pages. I used axios to acces the API. I made a google login using firebase, which was also new to me. 

#### React
In the gp I did mostly backend, but in the end I did make react application. We were in need for a view for the management tool and because I didn't make a react project yet, I decided to make it. I used axios like in vue, but in a simpler fashion. I just display a list of object form an api request as a table. 

#### Sonarcloud
I have mentioned it already in this portfolio, but I used sonarcloud to analyse my code. I never used a code analyser before and was suprised how convenient it was. 

#### Docker
Docker was definitely one of the things I have stuggled the longest with this semester. Setting it up for my frontend was easy, but because of mysql the backend wouldn't work. For now I have worked around it. Except for that, I think docker is an amazing tool. It makes gettting your code to a larger definitely very easy and fast. It will be a very usefull skill in the future.

#### Gitrunner
I researched gitrunners this semester. For my project this semester it was not realy worht the trouble, but that can be different in the future. 

#### DOT framework
This semester I did a research with the DOT framework for the first time. I started with the youtube tutorials and it seemed a bit overwhelming. After just starting with it was not too bad and I was able to write a nice research.

Research: https://github.com/S3Puzzle/Research

## Conclusion 

GP github: https://github.com/fontys-group3

IP github: https://github.com/S3Puzzle

