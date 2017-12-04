***

Apigee Edge:
------------

***
Using policies in Apigee:

Policies:
1. Quota: These policies are defined in the preflow of proxy end point which is the first point of request interception
 - Default: Resets every start of minute (duration predefined) based on the time. (no type defined
 - Rolling window: Checks number of requests previous hour( predefined time) (type=”rollingwindow”)
 - Flexi Type:  The timer starts when the first request is made and the count increase starting then. (type=”flexi”) ..Type is case sensitive
 - Conditional: Based on the query param (request.queryparam.appTeam) the quota can be configured different.
 - Error Handling:  Custom error message for quota overflow: Use Allow tag and AssignMessage 
http://hireshoban-trial-test.apigee.net/quotacustomerrormessage --> Try 5 times and see the custom error message
 - Flow Variables: Leverage flow variables to intercept and display message for quota. 
http://hireshoban-trial-test.apigee.net/quotaflowvariabledemo --> Try 5 times and see the quota availablity
- Specific Quota with API Key: curl -i http://hireshoban-trial-test.apigee.net/quota-specific-to-key?apikey= 
2. Security: TBD
3. Mediation: JSON to XML, XML to JSON, XML Transform, Assign Message, Extra Variables, Key Value Map Operations
   http://hireshoban-trial-prod.apigee.net/v1/xmltojson
4. Extension: TBD

Admin related work:

- Create maintain Users, Roles etc
- Environment variables for different environments (Prod, test etc), using in policies
- Adding a value when returning to client. http://hireshoban-trial-test.apigee.net/v1/kvm-get
- Creating and updating KVM : http://hireshoban-trial-test.apigee.net/kvm-create-update?kvmname=name&kvmvalue=shoban
- Caching values (tested for performance): https://apigee.com/platform/hireshoban-trial/proxies/kvm-cache/   
- API Keys: Keys can be used to authorize use of API Products that developers use
- Developers registers Apps in Apigee, each App can use 0 or more API Products. We can expire and revocation keys,  
http://hireshoban-trial-test.apigee.net/quota-specific-to-key?apikey=
- API Keys generated for Never, Duration and Date 
- Other:
- Converted Apigee API spec to Open API spec (apigee2openapi), below is an example
![enter image description here](images/image.png)
- Used postman for testing
