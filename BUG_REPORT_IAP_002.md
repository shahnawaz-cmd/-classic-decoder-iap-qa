# BUG REPORT: IAP-002
**Title:** Credits Not Synced After App Restart (Failed Acknowledgment/Sync)

**Severity:** Critical (Loss of Entitlement)
**Status:** Open

**Description:**
If the app is closed (killed) immediately after a successful Google Play purchase but before the app UI updates, the credits are not granted upon reopening the app. The order remains in a "Pending" state within the app logic, even though the payment was successful in Google Play.

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
