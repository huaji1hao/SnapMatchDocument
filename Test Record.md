# Testing Summary

## Unit Testing

| Test ID | Description                                                                 | Module         | Status | Comments                                                           |
| ------- | --------------------------------------------------------------------------- | -------------- | ------ | ------------------------------------------------------------------ |
| UT-001  | Test login function for valid input                                         | Authentication | Pass   |                                                                    |
| UT-002  | Test response for invalid input                                             | Authentication | Pass   |                                                                    |
| UT-003  | Test whether two images have the same object can successfully match         | Response       | Pass   | given two images both have a glass cup, match successfully         |
| UT-004  | Test whether two images don't have the same object can't successfully match | Response       | Pass   | one image has a dog, one image has a cat, can't successfully match |

## System Testing

| Test ID | Description                                                                             | Component                    | Status | Comments                                                     |
| ------- | --------------------------------------------------------------------------------------- | ---------------------------- | ------ | ------------------------------------------------------------ |
| ST-001  | Tests the identifyObjectInPhoto endpoint to see if it gives of the objects in the photo | Upload Challenges & Response | Pass   | Check if certain values are present in the 'data' array      |
| ST-002  | Tests the uploadChallenge endpoint to see if the image gets uploaded                    | Upload Challenges            | Pass   | Check if the request was successful (i.e. status_code = 200) |

## Integration Testing

| Test ID | Description                                  | Components Integrated | Status | Comments     |
| ------- | -------------------------------------------- | --------------------- | ------ | ------------ |
| IT-001  | Test integration User Interface and Database | UI/DB                 | Pass   |              |
| IT-002  | Test integration of Payment Gateway          | Payment/Network       | Fail   | See bug #124 |

# Alpha/Beta Testing

| Test ID | Scenario                                       | Expected Outcome        | Actual Outcome        | Status | Comments     |
| ------- | ---------------------------------------------- | ----------------------- | --------------------- | ------ | ------------ |
| AB-001  | User can complete a purchase using credit card | Transaction completes   | Transaction completes | Pass   |              |
| AB-002  | User receives error message for expired card   | Error message displayed | Incorrect error shown | Fail   | See bug #125 |
