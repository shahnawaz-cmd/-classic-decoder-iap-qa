# IAP QA Execution Checklist

Use this checklist for rapid manual testing of the In-App Purchase module.

## Phase 1: Authentication & Setup
- [x] Account Signup: Create a new user account. (✅ **PASSED** - Evidence: TC_01.webm)
- [x] Profile Verification: User is logged in and redirected to the dashboard. (✅ **PASSED** - Evidence: TC_01.webm)
- [x] Navigation: Clicking "Get Credit" opens the pricing/plans screen. (✅ **PASSED** - Evidence: TC_02.mp4)

## Phase 2: Purchase Flow (Google Play)
- [x] Plan Selection: Tapping a plan opens the Google Play payment sheet. (✅ **PASSED** - Evidence: TC_02.mp4)
- [x] Purchase Success: Credits are added immediately after a successful test payment. (✅ **PASSED** - Evidence: TC_02.mp4)
- [ ] Receipt Verification: (N/A - Confirmed by Dev)
- [x] UI Feedback: "Success" message/toast is displayed after purchase. (✅ **PASSED** - Evidence: TC_04.mp4)
- [x] Balance Update: The credit balance in the app UI updates without a manual refresh. (✅ **PASSED** - Evidence: TC_04.mp4)

## Phase 3: Error & Cancellation Handling
- [x] User Cancel: Cancel the payment sheet; app returns to plans screen. (✅ **PASSED** - Evidence: TC_05.webm)
- [x] Payment Decline: Use a "Declined" test card; verify error message. (✅ **PASSED** - Evidence: TC_06.mp4)
- [x] Network Loss: Kill internet during "Processing"; verify app handles the timeout. (✅ **PASSED** - Resolved: Payment cancels & Email received)
- [x] Insufficient Funds/Other Errors: (✅ **PASSED** - TC-07/TC-08)

- [x] Account Sync: Log in on a different device; verify credits are available. (✅ **PASSED** - Evidence: TC_11.mp4)
- [x] App Crash/Kill: Force-close during payment; verify sync on restart. (✅ **PASSED** - Resolved: Payment cancels & Email received)

## Phase 5: Compatibility (Cross-Platform/UI)
- [x] Android OS Versioning: Tested on Android 11, 12, 13, 14. (✅ **PASSED**)
- [x] Viewport/Responsive UI: Layout holds across different screen sizes. (✅ **PASSED**)
- [x] Currency/Region: Verify plan pricing for different regions. (✅ **PASSED** - Evidence: TC_13.mp4)

---
**Total Passed:** 16/17 (1 N/A)  
**Bugs Found:** 0 (All resolved)
**Evidence:** All videos stored in `Desktop/IAP_Test_Suite/Evidence/`
