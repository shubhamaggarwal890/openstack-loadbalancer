# Application-level Load Balancer in Java #
This project implements a simple load balancing program written in Java, with a Client and a Server program demonstrating its functionality. The functionality is as below:
* All clients connect to the Load Balancer, which is a single entry point for all requests. The requests consist of a string- an ID- the data corresponding to which is to be obtained from Workers and displayed on terminal.
* The Load Balancer accepts requests from clients and redirects them to appropriate workers selected using Round-Robin or Least-Connections scheduling, whichever is specifed by user via command-line.
* The Workers(Servers) extract information corresponding to recieved requests(IDs) from a MySQL Database, and return the data in the form of JSON responses to the Load Balancer, which forwards it to the clients as mentioned above.
* The Client, Load Balancer and Workers are all Multithreaded, and hence capable of Sending/Serving multiple requests at once.

## To Dos: ##
* Set up multiple worker nodes and load balancer instance on openstack.
## Steps to replicate: ##
* Prerequisites:
  * JDK 8 or above
  * MySQL Server(8)
  * Necessary Jar files
  * Import students.sql file to replicate the schema and table used with project.
  * The hostname:port pairs are extracted from worker_list.txt, modify if needed. The scheduling algorithm is given as a command-line argument to LoadBalancer.class file.
* To launch all processes:
   * Compiling the files **javac -cp json-20180813.jar:mysql-connector-java-8.0.15.jar *.java**
   * Worker **sudo java -cp json-20180813.jar:mysql-connector-java-8.0.15.jar:./ Worker $port**
   * Loadbalancer **sudo java -cp json-20180813.jar:mysql-connector-java-8.0.15.jar:./ LoadBalancer RR**
   * Client ** java -cp json-20180813.jar:mysql-connector-java-8.0.15.jar:./ Client**

* Once launched, windows corresponding to Workers, Load Balancer, and Client will show appropriate outputs on terminal.
