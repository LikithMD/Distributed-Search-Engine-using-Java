# Pdc-project
Distributed java file search engine as part of project for college

I am using zookeeper 3.4.12 version for this and JAVA 17 under maven project

## project working demo
First start the zookeeper server

![image](https://user-images.githubusercontent.com/76242298/176110396-107393fc-f964-44a7-889b-28460da09df9.png)

run the front end jar
now run the cluster and slave node jar file with 4 instances for 3 slaves and 1 master

![image](https://user-images.githubusercontent.com/76242298/176110567-e9806a3b-8fa2-485a-9315-af875e532dd0.png)

Whichever registers first will become the master

![image](https://user-images.githubusercontent.com/76242298/176110789-02603c1f-62a9-4258-81c3-b2d862809cc6.png)

Here left most instance marked is the leader
And top right is watching the leader and bottom left is watching top right
And bottom right is watching bottom left as shown in Image.
Here leader is keeping service registry which contain address of slaves
To make system fault tolerant
Now if we open frontend web browser search engine

![image](https://user-images.githubusercontent.com/76242298/176111016-d320bc0f-2915-4eb2-a816-fb910656ec62.png)

Now we can give any term and search engine will give us the best result
by calculating tf-idf algorithm.
Suppose I give the term “monster” it should give us books from it’s
database related to that term.

![image](https://user-images.githubusercontent.com/76242298/176111106-0243c2cb-31db-4e16-a293-71f43746db21.png)

And below is the image how work was distributed

![image](https://user-images.githubusercontent.com/76242298/176111180-b7c197b7-fb9e-4d1e-af45-ea8d168f00ef.png)

The top left was the leader and it distributed the work among 3 slaves by
dividing the 18 files from database evenly for each slave.
Now suppose any slave gets disconnected It should be updated to master
registry

![image](https://user-images.githubusercontent.com/76242298/176111241-7ab27682-e9e0-41f5-b9c0-1052572eecd9.png)

In the above Image bottom right node was terminated and it’s address
was removed from registry which we can see in top left marked image
And now the search engine should be working fine but the documents
will be dived among 2 nodes

![image](https://user-images.githubusercontent.com/76242298/176111324-8b2bfe02-d1b0-4177-b67e-f8809807f235.png)

![image](https://user-images.githubusercontent.com/76242298/176111427-b3fa4a5a-420f-4cd7-89c4-a071b5e23c82.png)

Now in the nodes work was divided only across two nodes
Now suppose if leader itself gets terminated ,new leader will be elected

![image](https://user-images.githubusercontent.com/76242298/176111498-b144e56d-4603-4750-bd57-f642e5dc55bc.png)

As we can see leader is terminated and top right was elected as leader
and it has service registry
Now there is only one slave all the documents has to be searched by
only 1 slave


![image](https://user-images.githubusercontent.com/76242298/176111767-8df0f423-f424-47d0-8669-9c5b263fd1b8.png)


Now only bottom left was the only slave remaining .Hence it received
all the 18 documents from database.
And also user can read whichever book they want to read from clicking
on the name in front end page

![image](https://user-images.githubusercontent.com/76242298/176111835-4700a2be-0b7f-4ee1-8c27-c488602573da.png)



