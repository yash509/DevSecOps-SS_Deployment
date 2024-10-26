A secret santa generator web application built using Spring Boot technologies, Thymeleaf views, JPA, H2 Database, and more. 
The project features Spring Model, View, and Controller (MVC) architecture and Service and Repository layers.

This project is based on the popular Christmas game Secret Santa where friends draw names from a hat to decide who they are required to give a present to. 
This project allows users to add names, and the project randomly generates secret santa matches.
Following are the steps you can do to deploy this application using Jenkins.

1 - Create  an AWS EC2 instance of t2.large and install jenkins, docker and maven in it.
    As the secret-santa application is running on port 8080, we need to make jenkins to run on port 8081.
    Edit the port number from 8080 to 8081 in this two files : 
    sudo vim /usr/lib/systemd/system/jenkins.service
    sudo vim /etc/default/jenkins and then restart jenkins 
    
2- Now access jenkins on port 8081 and complete the setup, once the jenkins set up is done , download some plugins required which are "eclipse turner installer", 
   "sonarqubescanner", "owasp", "docker", "docker pipeline and build stage"
   
3-  a- To use sonarqube , run it as container by docker run -d -p 9000:9000 sonarqube:lts-community
    b- username and paswd for sonarqube is "admin" and then to integrate with jenkins create a webhook and a token. (copy the token)

4-  a- Now in jenkins, credentials section , create the credentials for sonarqube (the token created in sonarqube) and for docker.
    b- In jenkins configure sonarscnner  in system section  by providing sonarqube url and token, and also configure docker .
    c- Now, configure all the installed plugins in tools section under manage jenkins.
    d- While configuring the installed tools, put the exact name of the tools present in the pipleine script or else the build will fail.

5 - Create a pipeline with the pipeline script present and build it.

6 - Dont forget to add jenkins in your docker group by sudo usermod -aG docker jenkins , after doing this restart jenkins. 



 
   Complete Jenkins CICD pipleine

  ![image alt](https://github.com/kadamvignesh/Secret-Santa-CICD/blob/main/Screenshot%20(71).png?raw=true)

  

  This is how the deployed application will look like:
  ![image alt](https://github.com/kadamvignesh/Secret-Santa-CICD/blob/main/Screenshot%20(75).png?raw=true)


  ![image alt](https://github.com/kadamvignesh/Secret-Santa-CICD/blob/main/Screenshot%20(76).png?raw=true)

  

  
  

    
