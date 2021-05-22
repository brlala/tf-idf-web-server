# tf-idf
This is the frontend server implementation for TF-IDF Distributed searching. For back-end server please rever to the following [link](https://github.com/brlala/tf-idf). It uses Zookeper for service discovery and will also re-elect the leader in the scenario where a leader drops off. The architectures is as below, 
1. The client browser front-facing for the client will allow the user to type a search query. The query will take in the search term, minimum score and also the results they are looking for. 
2. The client will send the response in JSON format to the web application server. Web application server will lookup the coordinators service registry for the ip of the leader of the cluster and forward the task to the leader.
3. Once the leader server receives the query, it will inspect the workers service registry for all available workers and send the task to all the worker nodes.
4. The worker nodes will read the task and send it back to the leader for the aggregation and scoring and send the results back to the frontend web server.  
  
**High-Level-Architecture**  
![image](https://user-images.githubusercontent.com/8999633/119233310-feba3900-bb5a-11eb-83c6-846d610db8c6.png)

# In order to execute the app
1. Build the file with maven
2. Run the program with `java -jar ./tf-idf.jar 8081`

# Used Dependency
1. Zookeeper
2. Protocol Buffers
3. Jackson
4. Maven
