# CDE BOOTCAMP: DOCKER ASSIGNMENT

## Personal Assignment

### First Question

Your manager at CDE Data Engineering, department was pleased with your Linux, Scripting and Version Control Skills. Your boss, checked through your progress and found you just finished learning about Docker for data engineering. With respect, to that he has tasked you and want you to display your tools to help scale CDE data infrastructure and platform with these questions:

- CDE is planning to diversify into tourism business which will involve moving customers to touristic locations in the world. You manager has tasked you with the responsibility of ingesting countries information from the RestCountreis API which can be accessed with this [link](https://restcountries.com/v3.1/all). You are tasked with extracting these fields from the API with **Python**

- Country name

- Independence

- United Nation members

- startOfWeek

- Official country name

- Common native name

- Currency Code e.g USD, EUR

- Currency name

- Currency symbol

- Country code ( idd ) . e.g Germany country code is +49

- you need to concatenate idd root and idd suffix from the response

- Capital

- Region

- Sub region

- Languages

- Area

- Population

- Continents

Once, you are done extracting the records, you need to write the extracted records into your preferred database system (Postgres, Mysql or anyone) the choice is yours.

- Use DBT to do transformation and create model from the data (implement both dimensional and fact model).

- Use any preferred visualization tool of your choice (PowerBi, Tableau or any of your choice) to draw basic or complex visualizations.

- Dockerize the entire ETL pipeline (running the image should run the entire extraction, ingestion and possibly transformation with DBT), and push the image to `Dockerhub`. Use a good descriptive name for the image.

Ensure the ETL code is dockerize in a different docker image from the database image.

- Schedule the running of the ETL docker image with Cron (yeah,you are using CRON again 😉)

  

#### N.B

- Ensure you document your thought process on your Github Readme, you must have an ETL architectural diagram (your submission will be null and void if you do not have one), ensure you use a print function to document the steps of extracting the data, ingesting the data and loading the data. In addition, you need to write a technical post on what you have done, with a section explaining Docker, the importance and usefulness of docker in data engineering, how Docker works and all that you wish to explain to newbie (you can use either medium, hashnode or Dev.to).

- Implement a CI/CD pipeline with Github Actions for automatically pushing the images to DockerHub once you make a commit to the Dockerfile.

- Share a link to the Visuals that you made from the dataset. This can be a PowerBi URL, google data studio URL or anyone of your choice.

##### Bonus Point

- Think of how to optimize your docker image with Multi-stage build

- Think of how to optimize your Docker image build.

- Share your progress on Linkedln, tag coredataengineers, all tutors and teaching assistants.

  

### Second Question

Your manager will like you to start the ETL and Database image with one command, and he has tasked you to build a docker-compose python based command line application from scratch.

You are to use python to build your own docker-compose command from scratch which does this:

- The script checks if a file with the name `docker-compose.yml` or `docker-compose.yaml` is found in the current directory (this is if a file path is not given to the script). However, if a file path is passed with the flag `-f` then your script reads the content of the file. 
- The script accepts three flags, the first is the `-up` flag that provisions all the services(network and all arguments), the second `-down` that brings down all running containers and remove all and the last `-down volume` that removes all containers and the volume. 
- The script should use the `Yaml` file to provision the services defined in the Yaml file. Also, the script provision a docker network and attach to all services. 
- Ensure you handle services that depends on each other (i.e If service A depends on Service B then provision B before A).
**N.B**
Given the below, example docker-compose.yml file, your script should provision the postgres-db service (run the container with the environment variables, port mapping, volumes and of course the networking) before the ETL_pipeline service since the ETL_PIPELINE service depends on the postgres-db service. 
```yml
services:
  postgres-db:	
  image: postgres
  container_name: postgres-cont
  ports:
	  - 5434:5432
  environment:
    - POSTGRES_USER=postgres
    - POSTGRES_PASSWORD=postgres
    - POSTGRES_DB=docker_workshop
  volumes:
    - postgres-data:/var/lib/postgresql/data

etl_pipeline:
  image: cde_etl_image
  container_name: etl_pipeline_cont
  depends_on:
    postgres-db:
 environment:
	- POSTGRES_USER=postgres
	- POSTGRES_PASSWORD=postgres
	- POSTGRES_HOST=postgres-db
	- POSTGRES_PORT=5432
	- POSTGRES_DW=docker_workshop
	- CSV_URL=https://support.staffbase.com/hc/en-us/article_attachments/360009197031/username.csv
 volumes:
 postgres-data:
```
 **P.S**
 Ensure you can run the script from anywhere on your system and it works. i.e you can call the script from any directory and it checks for the yaml file in that directory (and does all provisioning)

## Hint

- You might need to use argparse or typer to accept flags 
 
## Group Project
For this, you have to work among your peers, and develop an open ended data engineering task. You will need to pick up a domain that your group agreed on, find a source dataset and develop an end-to-end data pipeline. The data pipeline should ingest data into a `data lake`, then copy the activity to a relational database, transform the data with `DBT` , model the data with `DBT` and get analysis from the data(with data analysis). Think critically on the architecture and come up with a well detailed architecture. Once, you have come up with the architecture, think of where you will need to use docker in this project, justify the need to your manager. Once, you are done, you need to develop a powerpoint presentation of the entire data pipeline 
- The powerpoint should show the architectural diagram
- The thought process of your group on why you did something (why you decided to go with a particular group)
- Your visuals (insight derived from the data). You need to take either a screenshot or attach a link in the powerpoint.
**N.B**
There will be a day to present your group project. You need to commit your code to Github and implement effective CI/CD with Github Actions. 
Choose a name for your group as you did in the Linux group. 

**P.S**
**Group Grouping Registration**
To be grouped, you need to drop your details below:
Drop your name, email(used to register for the Bootcamp) and Github account username on this [link](https://docs.google.com/forms/d/1Xyhgf3xtKPgnOsSmNP75UJRf6NgmESK-OQF9jFttb1g/edit)

**Group Assignment Submission**

**N.B** 
	Both Personal and Group Assignment are due in 2 week (the 4th of 	November 2024)
	Submit the personal assignment(for the email section, use the Email used to register for the Bootcamp) with this [Assignment Submission Link](https://docs.google.com/forms/d/1ip_M2toHVgMt4oKPFWyI0T5OxuSEkx2VSftjOBh4nQU/edit). I wish you all Goodluck.


**Group Assignment Submission Link, will be shared with those who indicate interest and submitted the form**
