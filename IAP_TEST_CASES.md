# IAP Module - Comprehensive Test Plan

## 1. Positive Test Cases (Happy Path)
| ID | Title | Description | Expected Result |
|:---|:---|:---|:---|
| TC-01 | Successful Purchase | Select a plan and complete payment with valid test credentials. | ✅ **PASSED** |
| TC-02 | Signup to Purchase | Complete signup -> Dashboard -> Get Credit -> Purchase. | ✅ **PASSED** |
| TC-03 | Receipt Verification | Check for Google Play receipt in the linked email account. | ➖ **N/A** (Confirmed by Dev) |
| TC-04 | Plan UI Update | Verify "Buy" button changes to "Active" or similar after purchase. | ✅ **PASSED** |

## 2. Negative Test Cases
| ID | Title | Description | Expected Result | Result |
|:---|:---|:---|:---|:---|
| TC-05 | Payment Cancellation | Trigger payment sheet then click "Back" or "Cancel". | No charge; App remains stable on the plan screen. | ✅ **PASSED** |
| TC-06 | Declined Transaction | Use a "Declined" test card in the Play Store. | Clear error message: "Payment Declined". | ✅ **PASSED** |
| TC-07 | Insufficient Funds | Use a test card with insufficient balance. | Error message: "Insufficient balance". | ✅ **PASSED** |
| TC-08 | Duplicate Purchase | Attempt to buy a non-consumable item already owned. | Play Store should block the transaction. | ✅ **PASSED** |

## 5. Compatibility & Responsiveness
| ID | Title | Observation | Result |
|:---|:---|:---|:---|
| CP-01 | Android Versioning | Tested on Android 11, 12, 13, and 14. | ✅ **PASSED** |
| CP-02 | Viewport/UI | Tested on various screen sizes (Small, Medium, Large/Tablets). | ✅ **PASSED** |

## 3. Edge Cases (Critical)
| ID | Title | Description | Result |
|:---|:---|:---|:---|
| TC-09 | Network Loss (Mid-Pay) | Turn off Wi-Fi/Data exactly when clicking "Confirm Payment". | ❌ **FAILED** (See IAP-001) |
| TC-10 | App Crash/Kill | Force-close the app during the payment processing spinner. | ❌ **FAILED** (See IAP-002) |
| TC-11 | Device Switching | Purchase on Device A; Log into the same account on Device B. | ✅ **PASSED** (Evidence: TC_11.mp4) |
| TC-13 | Currency/Region | Change Play Store region (VPN) and check plan pricing. | ✅ **PASSED** (Evidence: TC_13.mp4) |
