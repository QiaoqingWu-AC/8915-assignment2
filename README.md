# CST 8915 - Assignment 2
The Best Buy Application is a cloud-native, microservices-based solution for managing product data, order, and customer interactions. It integrates AI-powered product descriptions and image generation using GPT-4 and DALL-E to enhance user experience. The application leverages Azure Service Bus as a backing service for order queuing and is deployed on a Kubernetes Cluster, ensuring scalability, reliability, and modularity.

## Need to TO DO
1. finish steps in lab8
2. create deployment.yaml files for each microservices
3. use Azure Service Bus
4. create docker image links for each microservices
5. finish steps in lab9

## Updated Application Architecture
![updated-architecture](./img/updated-architecture.png)

## Application and Architecture Explanation
### Application Functionality
1. **Store-Front**: A customer-facing web application for browsing products, viewing AI-generated product images and descriptions, and placing orders.
2. **Store-Admin**: An employee-facing backend web application for managing products and monitoring order status.
3. **Order-Service**: Processes order creation and publishes them to a managed message queue service via Azure Service Bus.
4. **Product-Service**: Handle CRUD operations for product data and interacts with the AI-Service to generate product descriptions and images.
5. **Makeline-Service**: Consumes messages from the order queue to process and complete orders.
6. **AI-Service**: Leverages GPT-4 and DALL-E to generate product descriptions and images dynamically.
7. **MongoDB**: A Non-SQL database that persists product and order information.

### Architecture Workflow
1. A customer visits the **Store-Front** to browse products.
2. The **Product-Service** provides product details, enriched with descriptions and images generated by the AI-Service.
3. The customer places an order, which is processed by the **Order-Service** and queued in **Azure Service Bus**.
4. The **Makeline-Service** consumes the order from the queue, processes it, and updates its status in the **MongoDB database**.
5. Employees monitor and manage orders via the **Store-Admin** application.

## Deployment Instructions
**TO DO: Step-by-step instructions to deploy the application in a Kubernetes cluster.**
### Step 1: Create Azure Kubernetes Cluster
1. Go to Azure Portal and search for **Azure Kubernetes Cluster**, then click **Create**.
2. In the Basics tap fill in the following details:
  - Cluster preset configuration: Choose `Dev/Test`.
  - Kubernetes cluster name: `AlgonquinPetStoreOnSteroidCluster`.
  - Region: Same as your resource group (e.g., EAST US).
  - Availability zones: `None`.
  - AKS pricing tier: `Free`.
  - Kubernetes version: `Default`.
  - Automatic upgrade: `Disabled`.
  - Automatic upgrade scheduler: `No schedule`.
  - Node security channel type: `None`.
  - Security channel scheduler: `No schedule`.
  - Authentication and Authorization: `Local accounts with Kubernetes RBAC`.
3. Create two node pools: `systemnodes` and `workernodes`.

## Table of Microservice Repositories
A table listing each microservice repository and its GitHub link.
| Service             | Repository Link                                   |
|----------------------|---------------------------------------------------|
| Store-Front          | [GitHub Link](https://github.com/QiaoqingWu-AC/store-front-L8)          |
| Store-Admin          | [GitHub Link](https://github.com/QiaoqingWu-AC/store-admin-L8)          |
| Order-Service        | [GitHub Link](https://github.com/QiaoqingWu-AC/order-service-L8)        |
| Product-Service      | [GitHub Link](https://github.com/QiaoqingWu-AC/product-service-L8)      |
| Makeline-Service     | [GitHub Link](https://github.com/QiaoqingWu-AC/makeline-service-L8)     |
| AI-Service           | [GitHub Link](https://github.com/QiaoqingWu-AC/ai-service-L8)           |
| MongoDB              | [GitHub Link](https://github.com/docker-library/mongo)              |
| Virtual-Customer     | [GitHub Link](https://github.com/QiaoqingWu-AC/virtual-customer-L8)     |
| Virtual-Worker       | [GitHub Link](https://github.com/QiaoqingWu-AC/virtual-worker-L8)       |

## Table of Docker Images
**TO DO: All docker images need to be created and updated here.**<br>
A table listing all Docker images you created, including their names and links to their Docker Hub repositories.
| Service             | Docker Image Link                                           |
|----------------------|------------------------------------------------------------|
| Store-Front          | [Docker Hub Link](https://hub.docker.com/r/<your-username>/store-front)          |
| Store-Admin          | [Docker Hub Link](https://hub.docker.com/r/<your-username>/store-admin)          |
| Order-Service        | [Docker Hub Link](https://hub.docker.com/r/<your-username>/order-service)        |
| Product-Service      | [Docker Hub Link](https://hub.docker.com/r/<your-username>/product-service)      |
| Makeline-Service     | [Docker Hub Link](https://hub.docker.com/r/<your-username>/makeline-service)     |
| AI-Service           | [Docker Hub Link](https://hub.docker.com/r/<your-username>/ai-service)           |
| MongoDB              | [Docker Hub Link](https://hub.docker.com/_/mongo)              |
| Virtual-Customer     | [Docker Hub Link](https://hub.docker.com/r/<your-username>/virtual-customer)     |
| Virtual-Worker       | [Docker Hub Link](https://hub.docker.com/r/<your-username>/virtual-worker)       |

## Any Issues or Limitations in the implementation (Optional)

## Demo Video
YouTube Link: 