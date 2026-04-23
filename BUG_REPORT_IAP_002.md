# BUG REPORT: IAP-002
**Title:** Credits Not Synced After App Restart (Failed Acknowledgment/Sync)

**Severity:** Critical (Loss of Entitlement)
**Status:** Closed

**Resolution:**
Fixed. If the app is killed during the payment process, the transaction is cancelled on the backend/Google Play side. The user receives an email notification for the payment cancellation or refund. Upon reopening the app, the state is clean, and the user can initiate a new purchase without issues.

**Steps to Reproduce:**
1. Navigate to "Get Credit" and select a plan.
2. Complete the purchase successfully on the Google Play sheet.
3. Immediately force-close (kill) the app before the "Success" popup appears.
4. Reopen the app and check the credit balance.

**Actual Result:**
Credit balance is not updated. The transaction is not synced, and the app does not "consume" or "acknowledge" the successful purchase from the Play Store queue.

**Expected Result:**
Upon startup, the app should query the Google Play Billing Library for any `purchased` but `unacknowledged` items, sync them with the backend, and grant the user their credits.

**Notes:**
- This suggests a missing `queryPurchasesAsync` check in the app's `onResume` or `onCreate` lifecycle.
