# Bug List Document

## Introduction

This document lists all identified bugs and issues found during unit testing, system testing, integration testing and alpha/beta testing of the SnapMatch app.

## Bug List

| Bug ID  | Description                                                                            | Severity | Status | Identified By     | Identified Date | Fixed By                       | Fixed Date   | Comments                                                                       |
| ------- | -------------------------------------------------------------------------------------- | -------- | ------ | ----------------- | --------------- | ------------------------------ | ------------ | ------------------------------------------------------------------------------ |
| BUG-001 | Login/Register Error windows fix                                                       | Minor    | Fixed  | Junfeng Zhu       | 2024-2-14       | Yongkang WANG, Kian Surani     | 2024-3-7     | NA                                                                             |
| BUG-002 | Some back buttons cannot be clicked in others challenges                               | Minor    | Fixed  | Junfeng Zhu       | 2024-3-18       | Shuli Wang                     | 2024-3-24    | Because of the error when invoking other components                            |
| BUG-003 | After click take photo in response, cannot go back                                     | Minor    | Fixed  | Junfeng Zhu       | 2024-3-18       | Shuli Wang                     | 2024-3-28    | Added some parameters in the components relative to taking photos for response |
| BUG-004 | Camera won't be switched off after logging out / navigating to page without video feed | Minor    | Open   | Eleanor McCartney | 2024-3-27       | [Name]                         | [YYYY-MM-DD] | [Any relevant comments]                                                        |
| BUG-005 | Useless back button in my challenge detail page                                        | Minor    | Fixed  | Eleanor McCartney | 2024-4-1        | Eleanor McCartney & Shuli Wang | 2024-4-16    | Added a new propriery MyChallengeDetail component                              |
| BUG-006 | After click View Response button, the responses cannot be shown correctly              | Minor    | Fixed  | Yongkang WANG     | 2024-3-26       | Yongkang WANG                  | 2024-3-28    | Unable to locate the corresponding ID due to incorrect or inconsistent reference parameter names |
| BUG-007 | Menu bar navigation error                                                              | Minor    | Fixed  | Yongkang WANG     | 2024-2-17       | Yongkang WANG                  | 2024-2-27    | NA                                                                             |
|  |  |  |  |  |  |  |  |  |
| BUG-ID | [Brief description of the bug] | [Critical/Major/Minor] | [Open/Fixed/Rejected] | [Name] | [YYYY-MM-DD] | [Name] | [YYYY-MM-DD] | [Any relevant comments] |

## Summary

- **Total Identified Bugs**: 7
- **Fixed Bugs**: 6
- **Open Bugs**: 1
- **Rejected Bugs**: 0

