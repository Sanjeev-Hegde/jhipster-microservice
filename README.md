#Development 

Run the followin thing before running the application

1. <h5>Keycloak Authorization server:</h5> 
This is required to perform single sign-on on all micro services required for theis application
This can be run by following ways
* Run using docker
    <pre>
    docker-compose -f ./gateway/src/main/docker/keycloak.yml up
    </pre>
* Download keycloak and run independently from official website.
  Ensure the following things are properly configured in this case:
  1.Client ID is created in keyclok server which chould be same in all microservices
  2. Ensure all security configuration are properly configuration in all application 
    
   
2. <h5>Postgres database:</h5>
The database instances can be created by following ways.<br /> 
* Create single postgres instance running with multiple database one for each microservice.
 To do this you can either install postgres locally and create database
 <br/><strong>or</strong><br/>
 Run a docker instance using following command:<br/>
    <pre>docker-compose -f ./gateway/src/main/docker/postgres.yml up</pre>
    In both the cases create database and role with login for each microservices
    <br />
    <pre>
     Login into docker as postgres user
     docker exec -ti <postgres docker name> /bin/bash
     psql
     create database elegal;
     create role elegal with login;
     </pre>
* Go to each microservice /src/main/docker and run the above docker -compose to create one database instance for each microservice
  SInce its for local development keep different port and update the port in <strong>application-dev.yml</strong> under recource forlder of each microservice
  
3. <h5>Jhipster-registry:</h5>
<pre>
cd registry
mvn
</pre>

4. <h5>Run all remaining microservices</h5>
Microservice can be run by just going to folder and running <pre>mvn</pre>
Or use spring profile and run from IntelliJ


#Production 

--TODO--
     
