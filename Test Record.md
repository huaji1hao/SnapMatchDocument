# Testing Summary

## Integration Testing

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

## Alpha/Beta Testing

| Test ID | Scenario                       | Expected Outcome  | Actual Outcome                                         | Status | Comments |
| ------- | ------------------------------ | ----------------- | ------------------------------------------------------ | ------ | -------- |
| AB-001  | Ask friend Emma to use our app | few bugs to fixed | We fix the bug and she get a high score in leaderboard | Pass   |          |
|         |                                |                   |                                                        |        |          |
