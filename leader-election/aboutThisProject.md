# Trivial Leader election problem

### Start the zookeeper server:
by using command ``` zkServer.cmd``` in windows and ``` .\zkSever.sh -start``` in unix and linux

![image](https://user-images.githubusercontent.com/76242298/137370815-18da2b2a-cea7-44dd-a69c-af2a1a08c9ec.png)

Now we have to get a executable jar file from the LeaderElection.java file by using command
``` mvn clean package```

You should find the jar file in target folder

Now we can use this jar file to deploy it in cluster or in cloud or simply as instances as I have shown below
the command is
``` java -jar target/leader.election-1.0-SNAPSHOT-jar-with-dependencies.jar```
Here my jar file name is leader.election-1.0-SNAPSHOT-jar-with-dependencier.jar

![image](https://user-images.githubusercontent.com/76242298/137371684-66f10b82-63fe-43e6-9256-f3d19838a56f.png)

Now In zookeeper whichever node first calls the getChildren() method will be designated as Leader

![image](https://user-images.githubusercontent.com/76242298/137372578-0e00c9ec-f338-4f7d-ae84-578bcd7e85d4.png)

But there are lot of problems with the above implementation like there is no fault tolerance and many more

This will be solved next


