# Sabur_13012025
QA Assessment Test 

API TESTs 

1st API Assessment 

API Endpoint: https://dummy.restapiexample.com/api/v1/create 
Verb: POST
Payload:
{
	"status": "success",
	"data": {
	    "name": "Yinus Olamilekan Sabur",
            "salary": "800000",
            "age": "30",
            "id": "s84145577"
         }
}

Business Rule: The endpoint should allow users to create an employer successfully.
{
    "status": "sucess"
}

Javascript code :
pm.test("Response status code is 200", function () {
  pm.expect(pm.response.code).to.equal(200);
});

pm.test("Response time is less than 6000ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(6000);
});

pm.test("Response has the required fields", function () {
    const responseData = pm.response.json();
    
    pm.expect(responseData).to.be.an('object');
    pm.expect(responseData.status).to.exist;
});

pm.test("Status field is a non-empty string", function () {
    const responseData = pm.response.json();
    
    pm.expect(responseData.status).to.be.a('string').and.to.have.lengthOf.at.least(1, "Status should not be empty");
});

Positive Test Scenario 
pm.test("Response status code is 200", function () {
  pm.expect(pm.response.code).to.equal(200);
});


pm.test("Response time is less than 3000ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(3000);
})
 

Negative Test Scenario :
pm.test("Response status code is 200", function () {
  pm.expect(pm.response.code).to.equal(404);
});

pm.test("Response time is less than 200ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(200);
});
 
API Functional Test Summary Report - 1st API Assessment 
API Endpoint: https://dummy.restapiexample.com/api/v1/createEmployee  
Verb: POST


 
 
API Performance Test Summary Report - 1st API Assessment 
API Endpoint: https://dummy.restapiexample.com/api/v1/createEmployee  
Verb: POST
SUMMARY REPORT:
 
ERROR REPORT :
 



2nd API Assessment 

API Endpoint: http://dummy.restapiexample.com/api/v1/employees/s84145577
Verb: GET
Payload:
{
  "employees": [
    {
      "status": "success",
      "data": {
        "name": "Yinus Olamilekan Sabur",
        "salary": 800000,
        "age": 30,
        "id": "s84145577"
      }
    },
    {
      "status": "success",
      "data": {
        "name": "Ajoku Oluchi Shalom",
        "salary": 350000,
        "age": 22,
        "id": "a84145571"
      }
    },
    {
      "status": "success",
      "data": {
        "name": "Bamidele Samuel",
        "salary": 1000000,
        "age": 38,
        "id": "b84145572"
      }
    }
  ]
}

Business Rule: The endpoint should allow users to fetch all employees at a go.

{
    "employees": [
        {
            "status": "success",
            "data": {
                "name": "Yinus Olamilekan Sabur",
                "salary": 800000,
                "age": 30,
                "id": "s84145577"
            }
        },
        {
            "status": "success",
            "data": {
                "name": "Ajoku Oluchi Shalom",
                "salary": 350000,
                "age": 22,
                "id": "a84145571"
            }
        },
        {
            "status": "success",
            "data": {
                "name": "Bamidele Samuel",
                "salary": 1000000,
                "age": 38,
                "id": "b84145572"
            }
        }
    ]
}

 


Javascript code :
pm.test("Response status code is 200", function () {
    pm.expect(pm.response.code).to.equal(200);
});


pm.test("Response time is less than 3000ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(3000);
});


pm.test("Response has the required fields", function () {
  const responseData = pm.response.json();
  
  pm.expect(responseData).to.be.an('object');
  pm.expect(responseData.employees).to.be.an('array');
  
  responseData.employees.forEach(function(employee) {
    pm.expect(employee).to.have.property('status');
    pm.expect(employee.data).to.be.an('object');
    pm.expect(employee.data).to.have.property('name');
    pm.expect(employee.data).to.have.property('salary');
    pm.expect(employee.data).to.have.property('age');
    pm.expect(employee.data).to.have.property('id');
  });
});


pm.test("Validate the status, salary, and age properties", function () {
    const responseData = pm.response.json();
    
    pm.expect(responseData).to.be.an('object');
    pm.expect(responseData.employees).to.be.an('array');
    
    responseData.employees.forEach(function(employee) {
        pm.expect(employee).to.be.an('object');
        pm.expect(employee.status).to.be.a('string').and.to.have.lengthOf.at.least(1, "Status should be a non-empty string");
        pm.expect(employee.data).to.be.an('object');
        pm.expect(employee.data.salary).to.be.a('number').and.to.be.at.least(0, "Salary should be a non-negative integer");
        pm.expect(employee.data.age).to.be.a('number').and.to.be.at.least(0, "Age should be a non-negative integer");
    });
});


pm.test("Content-Type header is 'text/html'", function () {
    pm.expect(pm.response.headers.get("Content-Type")).to.equal("text/html");
});

Positive Test Scenario 
pm.test("Response status code is 200", function () {
    pm.expect(pm.response.code).to.equal(200);
});


pm.test("Response time is less than 3000ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(3000);
});

 

Negative Test Scenario 
pm.test("Response status code is 404", function () {
    pm.expect(pm.response.code).to.equal(400);
});

pm.test("Response time is less than 200ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(200);
});
 

API Functional Test Summary Report – 2nd API Assessment 
API Endpoint: http://dummy.restapiexample.com/api/v1/employees/s84145577                                               Verb: GET
 

API Performance Test Summary Report – 2nd API Assessment 
API Endpoint: http://dummy.restapiexample.com/api/v1/employees/s84145577                                               Verb: GET
SUMMARY REPORT :
 
ERROR REPORT :
 
3rd API Assessment 

API Endpoint: http://dummy.restapiexample.com/api/v1/employees/s84145577
Verb: GET
Payload:
{
  "employees": [
    {
      "status": "success",
      "data": {
        "name": "Yinus Olamilekan Sabur",
        "salary": 800000,
        "age": 30,
        "id": "s84145577"
      }
    },
    {
      "status": "success",
      "data": {
        "name": "Ajoku Oluchi Shalom",
        "salary": 350000,
        "age": 22,
        "id": "a84145571"
      }
    },
    {
      "status": "success",
      "data": {
        "name": "Bamidele Samuel",
        "salary": 1000000,
        "age": 38,
        "id": "b84145572"
      }
    }
  ]
}

Business Rule: The endpoint should allow users to fetch one employee
{
    "status": "success",
    "data": {
        "name": "Yinus Olamilekan Sabur",
        "salary": 800000,
        "age": 30,
        "id": "s84145577"
    }
}
 

Javascript code :
pm.test("Response status code is 200", function () {
    pm.expect(pm.response.code).to.equal(200);
});


pm.test("Response time is less than 3000ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(3000);
});


pm.test("Content-Type header is 'application/json'", function () {
    pm.expect(pm.response.headers.get("Content-Type")).to.include("application/json");
});


pm.test("Response has the required fields - status and data", function () {
    const responseData = pm.response.json();
    
    pm.expect(responseData).to.be.an('object');
    pm.expect(responseData.status).to.exist;
    pm.expect(responseData.data).to.exist;
});


pm.test("Data object contains the required fields - name, salary, age, and id", function () {
    const responseData = pm.response.json();
    
    pm.expect(responseData.data).to.be.an('object');
    pm.expect(responseData.data.name).to.exist;
    pm.expect(responseData.data.salary).to.exist;
    pm.expect(responseData.data.age).to.exist;
    pm.expect(responseData.data.id).to.exist;
});
Positive Test Scenario :
pm.test("Response status code is 200", function () {
    pm.expect(pm.response.code).to.equal(200);
});

pm.test("Response time is less than 3000ms", function () {
  pm.expect(pm.response.responseTime).to.be.below(3000);

 

Negative Test Scenario :
pm.test("Response status code is 200", function () {
    pm.expect(pm.response.code).to.equal(505);
});
 
API Functional Test Summary Report – 3rd API Assessment 
API Endpoint: http://dummy.restapiexample.com/api/v1/employees                                                         Verb: GET
 

API Performance  Test Summary Report – 3rd API Assessment 
API Endpoint: http://dummy.restapiexample.com/api/v1/employees                                                         Verb: GET
SUMMARY :
 
ERROR :
 

