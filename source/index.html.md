---
title: Care – API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

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
    },
    {
      "code": "PREDPT_DTS",
      "testItems": [
        "PREDPT_DTS"
      ],
      "name": "COVID-19 PCR Test",
      "description": "For Raffles Medical - International Airport:\nFor bookings on Monday to Friday, patients may opt for either a Deep Throat Saliva (DTS) Test or a Nasal Swab Test.\nFor bookings on Saturday, Sunday and Public Holiday, only the Nasal Swab Test will be offered.\n\nFor Raffles Medical - Central:\nOnly DTS test will be offered.\n\nRegardless of test selected, results may take up to 48 hours to be ready after test administration.",
      "category": "predeparture",
      "active": true,
      "mark": "Available in Hong Kong only"
    },
    {
      "code": "ONARRIVAL_PCR",
      "testItems": [
        "ONARRIVAL_PCR"
      ],
      "name": "PCR Nasal Swab Test",
      "description": "A long nasal swab will be inserted into the nostril to collect fluid from the back of the nose. Swabbing will be done by a healthcare professional.",
      "category": "onarrival",
      "active": true,
      "mark": null
    },
    {
      "code": "ONARRIVAL_IGM",
      "testItems": [
        "ONARRIVAL_IGM"
      ],
      "name": "Serology (IgM) Test",
      "description": "A sample of blood will be taken for this test. Blood sample collection will be done by a healthcare professional.",
      "category": "onarrival",
      "active": true,
      "mark": null
    },
    {
      "code": "ONARRIVAL_DTS",
      "testItems": [
        "ONARRIVAL_DTS"
      ],
      "name": "COVID-19 PCR Test",
      "description": "For Raffles Medical - International Airport:\nFor bookings on Monday to Friday, patients may opt for either a Deep Throat Saliva (DTS) Test or a Nasal Swab Test.\nFor bookings on Saturday, Sunday and Public Holiday, only the Nasal Swab Test will be offered.\n\nFor Raffles Medical - Central:\nOnly DTS test will be offered.\n\nRegardless of test selected, results may take up to 48 hours to be ready after test administration.",
      "category": "onarrival",
      "active": true,
      "mark": "Available in Hong Kong only"
    },
    {
      "code": "NONTRAVEL_PCR",
      "testItems": [
        "NONTRAVEL_PCR"
      ],
      "name": "PCR Nasal Swab Test",
      "description": "A long nasal swab will be inserted into the nostril to collect fluid from the back of the nose. Swabbing will be done by a healthcare professional.",
      "category": "nontravel",
      "active": true,
      "mark": null
    },
    {
      "code": "NONTRAVEL_IGM",
      "testItems": [
        "NONTRAVEL_IGM"
      ],
      "name": "Serology (IgM) Test",
      "description": "A sample of blood will be taken for this test. Blood sample collection will be done by a healthcare professional.",
      "category": "nontravel",
      "active": true,
      "mark": null
    },
    {
      "code": "NONTRAVEL_DTS",
      "testItems": [
        "NONTRAVEL_DTS"
      ],
      "name": "COVID-19 PCR Test",
      "description": "For Raffles Medical - International Airport:\nFor bookings on Monday to Friday, patients may opt for either a Deep Throat Saliva (DTS) Test or a Nasal Swab Test.\nFor bookings on Saturday, Sunday and Public Holiday, only the Nasal Swab Test will be offered.\n\nFor Raffles Medical - Central:\nOnly DTS test will be offered.\n\nRegardless of test selected, results may take up to 48 hours to be ready after test administration.",
      "category": "nontravel",
      "active": true,
      "mark": "Available in Hong Kong only"
    },
    {
      "code": "CHINA_PREDPT_BUNDLE",
      "testItems": [
        "CHINA_PREDPT_PCR",
        "CHINA_PREDPT_IGM"
      ],
      "name": "PCR and IgM Test Bundle (China)",
      "description": "Required for travelers departing from Singapore to China. The bundle comprises two tests: a PCR nasal swab test and a Serology (IgM) test.",
      "category": "predeparture",
      "active": true,
      "mark": "Available for travellers flying to China only."
    }
  ]
}
]
```

List all available Covid-19 test types.

The optional query parameter 'category' allows you to get only tests that are available for 'predeparture', 'onarrival', 'nontravel'.

### HTTP Request

`GET /test-types`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
none | no | none

<aside class="success">
This endpoint is performing real requests towards our backend.
</aside>
