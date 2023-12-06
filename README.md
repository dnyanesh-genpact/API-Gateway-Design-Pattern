# API-Gateway-Design-Pattern
The API Gateway Design Pattern of Microservices Architecture

# Problem that API Gateway Design Pattern solves
Microservices architectures often involve multiple services that clients need to interact with. Directly managing these individual service endpoints can be complex for clients.

# Solution for this problem 
API Gateways aggregate multiple microservices into a single entry point, simplifying client interactions by providing a unified API.

# Prerequisites
  - Java Development Kit (JDK 8 or above)
  - Maven
  - IDE like STS(Spring Tool Suite) or Eclipse

# Architecture Overview
We will create 3 microservices : 
  - Account Service -> Manages Bank Account creation and fetching
  - Fund Transfer Service -> Manages trasnfer of funds for accounts
  - Banking Gateway Service -> This will be our API Gateway Service that will have both Account and Fund Transfer services registered with it.

# Steps : 
  1. Create Microservices :
      Create three separate Spring Boot projects (either via Spring Initializr or your preferred method). 

  2. Add Dependencies :
      For API Gateway Service, add following dependencies :
     ![image](https://github.com/dnyanesh-genpact/API-Gateway-Design-Pattern/assets/152908296/a53ed24e-a60b-4fea-8a9f-6329a5220449)
  

      For Account and Fund Transfer service, add following dependencies :
      ![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/cf699ba3-9153-4ce7-8c1c-ea5c642f5430)


  4. Business Logic :
       1) Account Service - Create a REST API to get an account by account number.
       2) Fund Transfer Service - Create a REST API to get transaction details for specific account.
       3) Banking Gateway Service(API Gateway Service) - Create a basic API Gateway Service that will call above 2 services upon getting client request.


  5. API Gateway Configuration :
       Configure the API Gateway service with URI and Header based routing for Account and Fund Transfer Service respectively.
      

  7. Run the services : 
      Start all 3 services i.e. Account Service, Fund Transfer Service and API Gateway Service.


  8. Test and connect h2 DB connection : 
      Connect to Account Service DB using jdbc:h2:mem:AccountService_DB on h2 console.
      Connect to Account Service DB using jdbc:h2:mem:FundTransfer_DB on h2 console.

      
  9. For testing Gateway, make a few calls on both Account and Fund Transfer Services using following URLs that use port 8080(Default API Gateway port): 

      Account Service POST call - http://localhost:8080/banking/account/createAccount

      Fund Transfer Service POST call - http://localhost:8080/banking/fundTransfer/newFundTransferRequest

      Account Service GET call -  http://localhost:8080/banking/account/getBankAccounts

      Fund Transfer Service GET call - http://localhost:8080/banking/fundTransfer/getTransactions


      Make sure to make use of Header along with Body while making a POST call on Banking Gateway Service.


# Microservices Configuration
Customize the behavior of services by editing the respective application.properties file. Adjust settings such as port, logging, and error handling.

 ![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/bfda74dc-097c-4b7e-bcff-bfa827195d0e)


 ![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/cbb933cf-a442-47f3-a23b-d073329d5cf3)


 ![image](https://github.com/dnyanesh-genpact/API-Gateway-Design-Pattern/assets/152908296/3f4d4dca-a1a7-4b87-b061-55e0a9ff8419)

   


# Sample Code for Controllers and Models
 **Account Controller** : 

![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/d512c8de-348f-4948-86e8-314fbb19309f)


**Account Model** : 

![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/b1d28399-57ac-4e5b-b97b-c0dc450b41ad)


**FundTransfer Controller** : 

![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/bc4d3069-634e-43dc-aae5-c0b37f1bb8c5)


**FundTransfer model** : 

![image](https://github.com/dnyanesh-genpact/Aggregator-Design-Pattern/assets/152908296/6a13fb64-5f08-43f7-92c0-0db4137da220)



# Contributing
  Contributions are welcome!

# Contact
  For questions or feedback, please email at tathoded@gmail.com OR dnyaneshsunilrao.tathode@genpact.com.



  
