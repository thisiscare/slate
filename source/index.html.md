---
title: Care – API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://api.stoplight.io/v1/versions/bjxPhx5Ff4Zr7JrGP/export/oas.json' target='_new'>Open API Specification</a>
  - <a href='https://editor.swagger.io/?url=https://api.stoplight.io/v1/versions/bjxPhx5Ff4Zr7JrGP/export/oas.json' target='_new'>Swagger Editor – Open API Specification</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to our Care API Sandbox! You can use our API to access API endpoints, which can get information on Covid-19 Tests, clinics, and appointment booking.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This is an early version of a developer portal and we appreciate feedback. Do get in touch!

# Authentication

> To authorize, you need an API Key.


Care uses API keys to allow access to the API. You can get an Kittn API key from our partner team.

The APIs expects for the API key to be included in all API requests to the server in a header that looks like the following:

`apikey: 0433D373-88C3-44DE-B160-2AF5837CF5BD`

<aside class="notice">
You must replace <code>0433D373-88C3-44DE-B160-2AF5837CF5BD</code> with your personal API key.
</aside>

# Covid-19 Test Products

## Get All Available Test Types

```shell
curl -X 'GET' \
  'https://api-sandbox01.carehealth.io/v1/covid19-test/test-types' \
  -H 'accept: application/json' \
  -H 'apikey: XXXX'
```

> The above command returns JSON structured like this:

```json
[
  {
  "status": "success",
  "data": [
    {
      "code": "PREDPT_PCR",
      "testItems": [
        "PREDPT_PCR"
      ],
      "name": "PCR Nasal Swab Test",
      "description": "A long nasal swab will be inserted into the nostril to collect fluid from the back of the nose. Swabbing will be done by a healthcare professional.",
      "category": "predeparture",
      "active": true,
      "mark": null
    },
    {
      "code": "PREDPT_IGM",
      "testItems": [
        "PREDPT_IGM"
      ],
      "name": "Serology (IgM) Test",
      "description": "A sample of blood will be taken for this test. Blood sample collection will be done by a healthcare professional.",
      "category": "predeparture",
      "active": true,
      "mark": null
    }
  ]
}
]
```

List all available Covid-19 test types.

The optional query parameter 'category' allows you to get only tests that are available for 'predeparture', 'onarrival', 'nontravel'.

### HTTP Requests

`GET /test-types`   
`GET /test-types?category=nontravel`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
category | no | 'predeparture', 'onarrival', or 'nontravel'

<aside class="success">
This endpoint is performing real requests towards our backend.
</aside>

# Test Facilities & Available Slots

## Get Testing Facilities

```shell
curl -X 'GET' \
  'https://api-sandbox01.carehealth.io/v1/covid19-test/facilities' \
  -H 'accept: application/json' \
  -H 'apikey: XXXX'
```

> The above command returns JSON structured like this:

```json
[
  {
  "status": "success",
  "data": [
    {
      "location": {
        "longitude": 103.989441,
        "latitude": 1.359167
      },
      "logo": "https://doctoroneworld-dev.s3.ap-southeast-1.amazonaws.com/public/file-1610103010209?AWSAccessKeyId=AKIAJZ6RF4WFFN2RROHQ&Expires=1634044421&Signature=Wbh2OivZZm6srPqzaIG8lTbsQfI%3D",
      "thumbnail": "https://doctoroneworld-dev.s3.ap-southeast-1.amazonaws.com/public/file-1610103002607?AWSAccessKeyId=AKIAJZ6RF4WFFN2RROHQ&Expires=1634044421&Signature=tcTYL8nTwnr0U5kWethe459YdS4%3D",
      "id": -1,
      "clinicCode": "CovidTest_Clinic_SG",
      "timeZone": "Asia/Singapore",
      "slotLimit": 10,
      "slotMinute": 15,
      "name": "Care health(Only for test)555",
      "email": "qa@carehealth.io",
      "contact": "+65900000",
      "address": "585 North Bridge Rd, Singapore 188770",
      "price": 100,
      "currency": "SGD",
      "openingHours": "24/7",
      "city": "Singapore",
      "country": "SG",
      "appointmentType": "CARE_HEALTH",
      "sort": 1,
      "deletedAt": "null",
      "createdAt": "2020-11-23T10:10:10.000Z",
      "updatedAt": "2021-05-11T12:57:42.000Z"
    }
  ]
}
]
```

This API lists all clinics and facilities that offer Covid-19 tests.

### HTTP Request

`GET /facilities`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
none | no | none

<aside class="success">
This endpoint is performing real requests towards our backend.
</aside>

## Get Available Time Slots for Covid-19 Tests

```shell
curl -X 'GET' \
  'https://api-sandbox01.carehealth.io/v1/covid19-test/slots?clinicCode=G141&date=2021-07-15' \
  -H 'accept: application/json' \
  -H 'apikey: XXXX'
```

> The above command returns JSON structured like this:

```json
[
 {
  "status": "success",
  "data": {
    "timeZone": "Asia/Singapore",
    "availableSlot": [
      {
        "type": "RMG",
        "date": "2021-07-15",
        "slotId": "RMG_10460782",
        "availability": false,
        "startTime": "14:45",
        "endTime": "15:00"
      },
      {
        "type": "RMG",
        "date": "2021-07-15",
        "slotId": "RMG_10460783",
        "availability": false,
        "startTime": "15:00",
        "endTime": "15:15"
      },
      {
        "type": "RMG",
        "date": "2021-07-15",
        "slotId": "RMG_10460784",
        "availability": false,
        "startTime": "15:15",
        "endTime": "15:30"
      }
    ]
  }
}
  ]
}
]
```

Get the available time slots for Covid-19 Tests at a clinic for a specific day.

### HTTP Request

`GET /slots/clinicCode=G141&date=2021-07-15`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
clinicCode | yes | valid clinic code. Example: G141
date | yes | example: 2021-07-15

<aside class="success">
This endpoint is performing real requests towards our backend.
</aside>

# Referral Codes

## Generate Referral Code (Preview)

```shell
curl -X 'POST' \
  'https://api-sandbox02.carehealth.io/v1/covid19-test/refcode?product=PREDP_PCR&max=1&discount=100&partnerid=SM29X' \
  -H 'accept: application/json' \
  -H 'apikey: XXXX'
```

> The above command returns JSON structured like this:

```json
[
  {
  "status": "success",
  "data": {
    "code": "CPX-B6US6XYW"
  }
}
]
```

Create a referral code for Covid-19 that users can redeem inside our app.

### HTTP Request

`POST /refcode`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
product | yes | valid product code, e.g. PREDPT_PCR
nax | yes | how many times can this code be used
discount | yes | how much discount in percent will the user enjoy when using this code
partnerid | yes | your unique partner ID for chargeback

<aside class="success">
This API is in an PREVIEW stage. The endpoint is responding with mock data.
</aside>

# Book a Covid-19 Test

## Book a Covid-19 Test Appointment (Preview)

```shell
curl -X 'POST' \
  'https://api-sandbox01.carehealth.io/v1/covid19-test/appointment' \
  -H 'accept: application/json' \
  -H 'apikey: XXXX'
  -d '{
  "clinicCode": "CovidTest_Clinic_SG",
  "appointmentSlotId": "RMG_9361621",
  "testTime": "2020-12-11T09:45:00.000Z",
  "name": "John Doe",
  "idType": "PASSPORT",
  "idNumber": "X918277H",
  "nationality": "SG",
  "gender": "male",
  "mobileNumber": "+658123456",
  "email": "johndoe@gmail.com",
  "dateOfBirth": "1962-08-05T00:00:00.000Z",
  "timeZone": "Asia/Singapore",
  "prepaid": "true",
  "bizId": "SM29X"
}'
```

> The above command returns JSON structured like this:

```json
[
  {
  "status": "success",
  "data": {
    "code": "APPT-B6US6XYW"
  }
}
]
```

Book a Covid-19 Test at a facility.

### HTTP Request

`POST /appointment`

### Request Body (JSON)

Parameter | Required | Description
--------- | ------- | -----------
clinicCode | yes | a valid clinic code, e.g. "CovidTest_Clinic_SG"
appointmentSlotId | yes | a valid slot id, e.g. "RMG_9361621"
testTime | yes | the time allocated to this slot, e.g. "2020-12-11T09:45:00.000Z"
name | yes | the name of the patient, e.g."John Wang"
idType | yes | the type of ID the patient will produce for identification. Valid types are: NRIC, PASSPORT, FIN, and HKID
idNumber | yes | the ID number, e.g. "X0861234B"
nationality | yes | the patient's nationality, e.g. "SG"
gender | yes | "male", "female", "unknown"
mobileNumber | yes | e.g. "+6581234565"
email | yes | e.g. "johndoe@gmail.com"
dateOfBirth | yes | e.g. "1992-08-05T00:00:00.000Z"
timeZone | yes | e.g. "Asia/Singapore"
prepaid | yes | is the test pre-paid or does the patient have to pay at the clinic? e.g. "true", "false"
bizId | yes | your partner ID

## QR-Code: Book a Covid-19 Test Appointment (Preview)

```shell
curl -X 'POST' \
  'https://api-sandbox01.carehealth.io/v1/covid19-test/appointmentqr' \
  -H 'accept: application/png' \
  -H 'apikey: XXXX'
  -d '{
  "clinicCode": "CovidTest_Clinic_SG",
  "appointmentSlotId": "RMG_9361621",
  "testTime": "2020-12-11T09:45:00.000Z",
  "name": "John Doe",
  "idType": "PASSPORT",
  "idNumber": "X918277H",
  "nationality": "SG",
  "gender": "male",
  "mobileNumber": "+658123456",
  "email": "johndoe@gmail.com",
  "dateOfBirth": "1962-08-05T00:00:00.000Z",
  "timeZone": "Asia/Singapore",
  "prepaid": "true",
  "bizId": "SM29X"
}'
```

> The above command returns a PNG image.

![](https://thisiscare.github.io/slate/images/qr-04cd18d4.jpg)

Book a Covid-19 Test at a facility and receive a QR code.

### HTTP Request

`POST /appointmentqr`

### Request Body (JSON)

Parameter | Required | Description
--------- | ------- | -----------
clinicCode | yes | a valid clinic code, e.g. "CovidTest_Clinic_SG"
appointmentSlotId | yes | a valid slot id, e.g. "RMG_9361621"
testTime | yes | the time allocated to this slot, e.g. "2020-12-11T09:45:00.000Z"
name | yes | the name of the patient, e.g."John Wang"
idType | yes | the type of ID the patient will produce for identification. Valid types are: NRIC, PASSPORT, FIN, and HKID
idNumber | yes | the ID number, e.g. "X0861234B"
nationality | yes | the patient's nationality, e.g. "SG"
gender | yes | "male", "female", "unknown"
mobileNumber | yes | e.g. "+6581234565"
email | yes | e.g. "johndoe@gmail.com"
dateOfBirth | yes | e.g. "1992-08-05T00:00:00.000Z"
timeZone | yes | e.g. "Asia/Singapore"
prepaid | yes | is the test pre-paid or does the patient have to pay at the clinic? e.g. "true", "false"
bizId | yes | your partner ID

<aside class="success">
This API is in an PREVIEW stage. The endpoint is responding with mock data.
</aside>
