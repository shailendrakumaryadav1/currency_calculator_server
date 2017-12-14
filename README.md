# currency_calculator_server

### How to run the server

Server is written in Spring Boot on Java 8. You should have a Java Development Kit v8 installed in your machine to run the server.
Use the following command to start the server on your machine.

Linux/Mac -
```sh
./mvnw clean spring-boot:run
```

Windows -
```sh
mvnw.cmd clean spring-boot:run
```

After the server has started, go to the below link in your browser and you should see, "App running".
Link: http://localhost:8080


### APIs Available

Following APIs are available for you to use –

* 1. Get All Currencies

URL: /api/currency
Method: GET

Response:
A list of Currency Object. Each currency object has –
1. code – 3 alphabet code of currency
2. country – name of the country
3. name – name of the currency
4. flagPath - path to the image of flag
5. rate - equivalent conversion to USD rate


Example Response: 
```sh
[
    {
        "code": "CHF",
        "country": "Switzerland",
        "name": "Swiss Franc",
        "flagPath": "/flags/ch.png",
        "rate": 1.0369
    },
    {
        "code": "CNY",
        "country": "China",
        "name": "Chinese Yuan Renminbi",
        "flagPath": "/flags/cn.png",
        "rate": 0.1528
    },
    {
        "code": "EUR",
        "country": "European Union",
        "name": "Euro",
        "flagPath": "/flags/eu.png",
        "rate": 1.1875
    }
]
```



* 2. Get Exchange Rate

URL:   /api/exchange?baseCode=<baseCode>&targetCode=<targetCode>
Note that baseCode and targetCode are required parameters and refers to the 3-alphabet 
code of the currency. 
For example, to convert Japanese Yen to Indian Rupee your request should be:
/api/exchange?baseCode=JPY&targetCode=INR
Method: GET

Response: An exchange object.  Exchange object contains the following fields.
1. baseCode: The currency you want to convert from.
2. targetCode: The currency you want to convert to.
3. rate: effective conversion rate.

Example Response:
```sh
{
    "baseCode": "CNY",
    "targetCode": "MYR",
    "rate": 0.64201677
}
```

This means 1 CNY equals to 0.64201677 MYR

