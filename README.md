# Assignment: Dockerizing WordPress with Dockerfile, Docker Compose, and Database Optimization

### Objective: The goal of this assignment is to Dockerize a WordPress application using best practices for Dockerfile and Docker Compose, as well as to optimize the database for improved performance. You are also required to create a Readme file to document your approach and provide additional notes related to the task.

Tasks:

### 1) Write a Dockerfile for WordPress:
* Create a Dockerfile for the WordPress application.
* Use an official WordPress image as the base image.
* Follow best practices for creating a Dockerfile, including minimizing layers, using appropriate labels, and securing sensitive information.
### 2) Write a Docker Compose File:
* Create a Docker Compose file (docker-compose.yml) to orchestrate the WordPress application.
* Include services for WordPress and the database (e.g., MySQL or MariaDB).
* Configure network settings and dependencies between services.
* Use environment variables to manage configuration settings securely.
### 3) Optimize the Database for Performance:
* Research and implement database optimization strategies to enhance performance.
* Consider techniques such as indexing, caching, and query optimization.
* Document the steps you took to optimize the database and explain the rationale behind each optimization.
### 4) Create a Readme File:
* Write a Readme file (README.md) that explains your approach to Dockerizing WordPress and optimizing the database.
* Provide clear instructions on how to build and run the Dockerized WordPress application using Docker Compose.
* Include any additional notes, recommendations, or challenges you encountered during the process.

## Submission Guidelines:
* Create an account on [https://github.com/]
* Fork this repository to your account.
* When completed, open a Pull Request to this main repository.
* Describe the intent of the code and the approach taken in the Pull Request description.


## Evaluation Criteria:
Your assignment will be evaluated based on the following criteria:

* Adherence to Docker best practices in the Dockerfile and Docker Compose.
* Correct setup of the WordPress and database containers.
* Effective database optimization techniques applied.
* Clarity and completeness of the Readme file.
* Documentation of your approach and rationale for optimization choices.

Note: Please make sure to test your Dockerized WordPress application thoroughly to ensure it functions as expected.

Good luck with your assignment! If you have any questions or need further assistance, feel free to ask.
Approach for Dockerizing WordPress : Gone through the official Docker documentation on WordPress & write the Dockerfile and docker-Compose.yml file with the help of the documentation and some of my prior knowledge on networking and docker.

Approach for optimizing the database : Research about different database optimization strategies. Having the basic knowledge of MYSQL queries given a big advantage.

Challenges encountered during the process : My laptop was having some issues related to storage. So, i had to used a AWS EC2 instance.
## Deployment
 Step 1:
Build the Docker image using the following command: 
```bash
  docker build -t my-wordpress-image .
Once the image is built, you can verify its existence by running:
  docker image
```
To run the container from image
```bash
  docker run -p 8080:80 --name my-wordpress-container my-wordpress-image
```
To get access of the website just hit the following url in the browser
```bash
  http://localhost:8080
```

## Step 2:
To start containers defined in a 'docker-compose.yml'
```bash
  docker-compose up -d 
```
To get access of the website just hit the following url in the browser
```bash
  http://localhost:8081 or http://your-server-ip
```
## Step 3:
To access the MySQL Container
```bash
  docker exec -it my-mysql bash
```
To log in to MySQL and enter the password
```bash
  mysql -u root -p
```
To use databse and showing the tables
```bash
  use wordpress;
  show table;
```
To Analyze Query Performance :
Identify slow-running queries using the EXPLAIN statement
```bash
  EXPLAIN SELECT * FROM wp_posts WHERE post_status = 'publish';
```
Indexing : 
Identify frequently used columns adding indexes to them 
```bash
  CREATE INDEX idx_title ON wp_posts (post_title);
```
Ensure that each table has a primary key
```bash
  ALTER TABLE wp_posts ADD PRIMARY KEY (ID);
```
Optimize Queries : Only retrieve the columns needed
```bash
  SELECT post_title, post_date FROM wp_posts WHERE post_status = 'publish';
```
Regular Maintenance : Analyze and Optimize Tables
```bash
ANALYZE TABLE wp_posts;
OPTIMIZE TABLE wp_posts;
```
Remove Unnecessary Data : Periodically remove old or unused data to reduce the size of your database.

Partitioning (For Large Tables) : Partitioning them to distribute data across multiple partitions.

Monitor Performance : Continuously monitor the performance of database using tools like MySQL's Performance Schema
## Documentation

[Documentation]https://drive.google.com/file/d/1xFKGbz8nsE3uvnvHmwa581daW5pxyDv1/view?usp=sharing


