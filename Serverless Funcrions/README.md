# Serverless
Serverless is a cloud computing execution model that

- Automatically assigns computing resource required to run application code on demand
- It scales these resource up or down depending on demand
- Scales the resource to zero when application stops running Serverless offloads all management responsibility for backend cloud infrastructure and operations task including scheduling, scaling, patching among others to the cloud provider. This allows developers to spend more time working on their application. They only pay for resource required to run their application and only when those applications are running. Amazon web services introduced serverless in 2014 with AWS Lambda.
- Today every leading cloud service provide a serverless platform including, Microsoft Azure (Azure functions), Google Cloud (Google Cloud Functions and IBM Cloud(IBM Cloud Code Engine).
- Function as a service is a subset of serverless it’s the compute paradigm central to serverless, where application code or containers run only in response to events or request. Serverless include Faas plus all the other associated resource and cloud services and resource supporting the code for instance storage, network , databases , API getaway, Authentication.
## Pros of serverless
Developers have more time to spend on app development
Customers only pay for execution
Serverless is a polyglot environment allowing developers to code in any language or framework
For certain work loads e.g. ones requiring parallel processing, serverless can be both fast and more cost-effective than other forms of compute
They provide near-total visibility into systems and user time.
## Cons
1. Stable or predictable workload may not enjoy benefits offered by serverless
1. Cold start can limit some applications e.g., financial trading.
1. Monitoring and debugging can be challenging in any distributed system
1. Vendor lock-in.