Case Study 1 – Digital Bank – Phase 1

Digi Bank wants to embark on the journey on the Digital Transformation and needs to integrate with Mint and Personal Capital Companies which would allow consumers to integrate their Bank Account Balances with the Mint and Personal Capital. Also, DigiBank wants to start with a Mobile App which will support the basic features like

·       Retrieve Account Balance 
Input: Customer Id and Account Number
Output: Account Balance, TimeStamp, Account Number
Transaction Type [C/D]

·       Update User Profile
Input: Customer Id, Email, Phone Number, Twitter Id
Output: Status 

 

·       Submit a Payment Transfer
Input: From Account, To Account, Amount, Transfer Date
Output: Payment Transfer Id

The project needs to be delivered in 2 Months. The MINT and Personal Capital are unable to consumer the Legacy SOAP based webservices from backend. The Bank already has the SOAP based Webservices for the Account Balance. MINT and Personal Capital need a REST API which will expose the backend data to the Mint and Personal Capital.

Below are details required from MINT and Personal Capital

-         API Swagger Document for Account Balance API which clearly explains

o   Base Path

o   HTTP Status Code

o   Query Param

o   Security – OAUTH

o   Request/Response Examples

-         API request Portal

-         API Test cases and Scenarios

·       API Developer Portal – Similar to https://openbank.apigee.io/

 

Digi Bank Product Owner – User Stories

-         Given a Customer logs into the DigiBank when he Clicks on the Account Balance, then he should be able to see his Account Balance as of the requested timestamp

-         Given a Customer logs into the DigiBank when he Clicks on the Update User, then he should be able to update the Contact details.

-         Given a Customer logs into the DigiBank when he Clicks on the Payment Transfer, then he should be able to perform the Payment from his account to any other linked Mobile Number and Bank Name.

 

So, the IT is presented with 2 API Business Initiative.  Third-party Aggregator API for MINT and Personal Capital and Mobile App API initiative.

 

API URL

•      htttp://www.digibank.com/api/v1/account?custid=1234&acctnumber=12345678- GET

•      htttp://www.digibank.com/api/v1/account/statements – GET

•      htttp://www.digibank.com/api/v1/user- PUT

•      htttp://www.digibank.com/api/v1/payment- POST

 

 

IT Architects have decided to have an API Management Platform to Design, Develop, Publish, Monitor and manage the API using the APIGEE Edge.

 

Here are the high-level functional Requirements for the API Implementation.

·       Design

o   Create all the API Design using the Swagger Hub https://app.swaggerhub.com/

o   Create all the Mock Services using any of mockable.io so that the MINT Developers can start developing the UI based on the API Contract.

https://www.mockable.io/

o   Ensure all the Design best practices are followed

https://swagger.io/blog/api-design/api-design-best-practices/

https://www.javaguides.net/2018/06/restful-api-design-best-practices.html

·       Develop

o   Create API Proxy for 3 API as defined by Business Requirements

o   Validate the Query Parameters and send custom error message with following

{

  "error": {

    "code": DIGI-1234,

    "message": "Validation Occurred"

  }

}

 

o   Create the Quota Policy for the API with 10 calls per minute and on violation show the following error message.

{

  "error": {

    "code": DIGI-4567,

    "message": "Quota Violation"

  }

}

 

o   The backend response for Account Balance should be cached using the Cache Policy for 30 mins.

o   The Customer Twitter Id are present in Salesforce. Connect to Salesforce to update the Twitter Id.

·       Secure

o   Implement the OAUTH Token for the Account Balance API

o   Implement the JWT Token for the Payment Transfer API

o   Implement the Basic Auth for the Customer Profile API.

·       Publish

o   Create 2 Products for 3 API and 1 API based on the API Consumer

o   Assign the API Key for each API Consumer

o   Build a Development Portal

·       Analyze

Business Owners and Application Owners need to know the metrics for the various proxies.

o   Response time

o   Request latency

o   Request size

o   Target errors

o   API product name

o   Developer email address

o   App name

o   Many others

 

·       Monetize

o   Create Monetization Plan for the Mint and Personal Capital based on the call invocation.

o   Create Reports for both the API Consumers

References:

·       https://openbank.apigee.io/
