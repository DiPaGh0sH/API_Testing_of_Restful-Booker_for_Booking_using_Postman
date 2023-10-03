# Introduction
This documentation explains the API testing suite for the restful-booker.herokuapp.com which contains a Postman collection and environment designed to facilitate API testing for various functionalities related to Booking management. The API allows operations such as fetching any existing booking, creating a new booking, retrieving created booking, generating token for authorization, updating booking, fetching the updating booking and delete the booking dynamically and also used import dataset from csv file for create a booking and get the booking successfully.

# Summary    
I have completed all these API of Create Booking Info, Get Booking Info, Post Token, Update Booking Info, Get Updated Booking Info and Delete Booking Info using https://restful-booker.herokuapp.com/   
<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/Summary_in_Command.png?raw=true" />
</p>
 

Here in this API testing Booking managements are viewed and different tests were performed for different HTTP methods like POST, GET, DELETE, PUT.

**Summary:** Total 6 Test Scripts and 17 assertions were done. All of them passed with 0 failed tests and 0 skipped tests. The number of iteration was 1.

# Summary    
I also created booking info by importing a dataset from CSV filen and used all these API of Create Booking, Get Booking using https://restful-booker.herokuapp.com/   
<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/4.png?raw=true" /></p>

Here in this API testing Booking managements are viewed and different tests were performed for different HTTP methods like POST, GET.

**Summary:** Total 56 assertions were done. All of them passed with 0 failed tests. The number of iteration was 7.

**CSV File:**

<p align="center">
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/1.png?raw=true" /></p>

**Imported CSV File with 7 Iteration:**

<p align="center">
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/2.png?raw=true" /></p>

**Previewing Data that imported from CSV file:**

<p align="center">
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/3.png?raw=true" /></p>

# Execution Result of all iterations from CSV File:

**Iteration : 01**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration1.png?raw=true" /></p>

**Iteration : 02**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration2.png?raw=true" /></p>

**Iteration : 03**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration3.png?raw=true" /></p>

**Iteration : 04**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration4.png?raw=true" /></p>

**Iteration : 05**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration5.png?raw=true" /></p>

**Iteration : 06**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration6.png?raw=true" /></p>

**Iteration : 07**

<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/SS%20of%20CSV%20file%20Importing/Iteration7.png?raw=true" /></p>

 
# Requirements  
**Java**  
https://www.oracle.com/java/technologies/downloads/   
**Postman**   
https://www.postman.com/   
**Node JS**   
https://nodejs.org/en/    


# Assertions Details    
#### Create Booking Info
**Tests Script**
```bash
var jsonData = pm.response.json()
pm.environment.set("booking_id", jsonData.bookingid)
console.log(jsonData.bookingid)
```
**Pre-Request Scripts**

```bash   
var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
console.log("First Name: "+firstname)
pm.environment.set("first_name",firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
console.log("Last Name: "+lastname)
pm.environment.set("last_name",lastname)

var totalprice = pm.variables.replaceIn("{{$randomInt}}")
console.log("Total Price: "+totalprice)
pm.environment.set("total_price",totalprice)

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
console.log("Deposition of Payment: "+depositpaid)
pm.environment.set("deposit_paid",depositpaid)

var additional = pm.variables.replaceIn("{{$randomProduct}}")
console.log("Additional Needs: "+additional)
pm.environment.set("additional_needs",additional)

const moment = require('moment')
const today = moment()
console.log(today.format("YYYY-MM-DD"))
pm.environment.set("check_in", today.add(2,'d').format("YYYY-MM-DD"))
pm.environment.set("check_out", today.add(2,'d').format("YYYY-MM-DD"))

```
**Body**
```bash
{
	"firstname" : "{{first_name}}",
	"lastname" : "{{last_name}}",
	"totalprice" : {{total_price}},
	"depositpaid" : {{deposit_paid}},
	"bookingdates" : {
    	"checkin" : "{{check_in}}",
    	"checkout" : "{{check_out}}"
	},
	"additionalneeds" : "{{additional_needs}}"
}
```   
#### Get Booking Info  
**Tests Script**
```bash
var status_code = pm.response.code
console.log(status_code)
if(status_code == 200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
var jsonData = pm.response.json()
pm.test("First Name Validation", function () {
    pm.expect(jsonData.firstname).to.eql(pm.environment.get("first_name"));
});
pm.test("Last Name Validation", function () {
    pm.expect(jsonData.lastname).to.eql(pm.environment.get("last_name"));
});
pm.test("Total Price", function () {
    pm.expect(jsonData.totalprice).to.eql(Number(pm.environment.get("total_price")));
});
pm.test("Deposition of Payment" , function () {
    pm.expect(String(jsonData.depositpaid)).to.eql(pm.environment.get("deposit_paid"));
});
pm.test("Date of Check In" ,function () {
    pm.expect(jsonData.bookingdates.checkin).to.eql(pm.environment.get("check_in"));
});
pm.test("Date of Checking Out", function() {
    pm.expect(jsonData.bookingdates.checkout).to.eql(pm.environment.get("check_out"));
});
pm.test("Additional Needs", function() {
    pm.expect(jsonData.additionalneeds).to.eql(pm.environment.get("additional_needs"));
})}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}

```
#### Token
**Tests Script**
```bash
var tokendata = pm.response.json()
pm.environment.set("token_id", tokendata.token)

```
**Body**
```bash
{
	"username": "admin",
	"password": "password123"
}

```
#### Update Booking Info
**Pre-Request Scripts**

```bash   
var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
console.log("First Name: "+firstname)
pm.environment.set("first_name",firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
console.log("Last Name: "+lastname)
pm.environment.set("last_name",lastname)

var totalprice = pm.variables.replaceIn("{{$randomInt}}")
console.log("Total Price: "+totalprice)
pm.environment.set("total_price",totalprice)

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
console.log("Deposition of Payment: "+depositpaid)
pm.environment.set("deposit_paid",depositpaid)

var additional = pm.variables.replaceIn("{{$randomProduct}}")
console.log("Additional Needs: "+additional)
pm.environment.set("additional_needs",additional)

const moment = require('moment')
const today = moment()
console.log(today.format("YYYY-MM-DD"))
pm.environment.set("check_in", today.add(2,'d').format("YYYY-MM-DD"))
pm.environment.set("check_out", today.add(2,'d').format("YYYY-MM-DD"))

```
**Body**
```bash
{
	"firstname" : "{{update_first_name}}",
	"lastname" : "{{update_last_name}}",
	"totalprice" : {{update_total_price}},
	"depositpaid" : {{update_deposit_paid}},
	"bookingdates" : {
    	"checkin" : "{{update_check_in}}",
    	"checkout" : "{{update_check_out}}"
	},
	"additionalneeds" : "{{update_additional_needs}}"
}

```
####Dynamically Token Generation in Header**
```bash
Cookie		token={{token_id}}

```   
#### Get Last Updated Booking Info  
**Tests Script**
```bash
var status_code = pm.response.code
console.log(status_code)
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
var jsonData = pm.response.json()
pm.test("First Name Validation", function () {
    pm.expect(jsonData.firstname).to.eql(pm.environment.get("update_first_name"));
});
pm.test("Last Name Validation", function () {
    pm.expect(jsonData.lastname).to.eql(pm.environment.get("update_last_name"));
});
pm.test("Total Price", function () {
    pm.expect(jsonData.totalprice).to.eql(Number(pm.environment.get("update_total_price")));
});
pm.test("Deposition of Payment" , function () {
    pm.expect(String(jsonData.depositpaid)).to.eql(pm.environment.get("update_deposit_paid"));
});
pm.test("Date of Check In" ,function () {
    pm.expect(jsonData.bookingdates.checkin).to.eql(pm.environment.get("update_check_in"));
});
pm.test("Date of Checking Out", function() {
    pm.expect(jsonData.bookingdates.checkout).to.eql(pm.environment.get("update_check_out"));
});
pm.test("Additional Needs", function() {
    pm.expect(jsonData.additionalneeds).to.eql(pm.environment.get("update_additional_needs"));
})}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}

```
#### Delete Booking Info  
**Tests Script**
```bash
var status_code = pm.response.code
console.log(status_code)

if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}

else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}

```
####Dynamically Token Generation in Header**
```bash
Cookie		token={{token_id}}

```

# Create Test Suites   

### Using Newman   


  Newman is a command-line Collection Runner for Postman. It enables you to run and test a Postman Collection directly from the command line.
#### Install Command    
```bash
npm install -g newman    
```
#### Run Command    
- newman run “Path/CollectionName.json” -e Path/EnvironmentName.json
- newman run “Collection Link” -e “Path”/EnvironmentName.json    

#### Create HTML Report  
 
#### Install Command      
```bash
npm install -g newman-reporter-html
```
**or**   
```bash
npm install -g newman-reporter-htmlextra    
```
#### Report Run Command      
- newman run CollectionName.json -e EnvironmentName.json -r cli,html    
**or**    
- newman run CollectionName.json -e EnvironmentName.json -r cli,htmlextra

#### Newman Report File htmlextra
 <p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/1.png?raw=true"/>
 <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/2.png?raw=true"/>
 <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/3.png?raw=true"/>
    <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/4.png?raw=true"/>
    <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/5.png?raw=true"/>
    <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/6.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/7.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/8.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/9.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/10.png?raw=true"/>
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/11.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/12.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/13.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/14.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/15.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/16.png?raw=true"/>
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Restful-Booker_for_Booking_using_Postman/blob/main/newman/All%20SS%20of%20Report/17.png?raw=true"/></p>

