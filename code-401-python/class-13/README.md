# Class-13
## Serverless Functions
### Reading
##### What is Serverless Computing?
![](https://www.turningcloud.com/blog/wp-content/uploads/2022/02/serverless.jpeg)
- **What is Serverless?**
    Serverless is a cloud application development and execution model that lets developers build and run code without managing servers, and without paying for idle cloud infrastructure.
- **Serverless DOES NOT mean 'NO servers'**
    Serverless simply means that the customer does not need to worry about managing or configuring the servers themselves. The provider takes care of all of that for them.
- **Serverless is more than just FaaS**
    - **FaaS (Function-as-a-Service)** is a type of cloud-computing service that allows you to execute code in response to events without the complex infrastructure typically associated with building and launching microservices applications.
    - **Serverless** is focused on any service category, be it compute, storage, database, messaging, api gateways, etc. where configuration, management, and billing of servers are invisible to the end user. **FaaS**, on the other hand, while perhaps the most central technology in serverless architectures, is focused on the event-driven computing paradigm wherein application code, or containers, only run in response to events or requests.
![](https://kubesphere.io/images/blogs/en/serverless-vs-faas/serverless-faas.png)
- **Serverless vs. PaaS, containers, and VMs**
![](https://i0.wp.com/allaboutdynamic.com/wp-content/uploads/2020/05/2-vm-vs-container-vs-serverless.png?resize=474%2C186&ssl=1)
- **Pros and cons of serverless**
    | Pros | Cons |
    |-----------------|-----------|
    | Improved developer productivity | Unacceptable latency for certain applications | 
    | Pay for execution only | Higher costs for stable or predictable workloads |
    | Develop in any language | Vendor lock-in|
    | Streamlined development/DevOps cycles | Monitoring and debugging issues |go wrong  |
    | Cost-effective performance | - | 
    | Usage visibility |  -  | 
- **Use cases for serverless**
    - Serverless and microservices
        The microservices model is focused on creating small services that do a single job and communicate with one another using APIs.
    - API backends
    - Data processing
    - Massively parallel compute/“Map” operations
    - Stream processing workloads