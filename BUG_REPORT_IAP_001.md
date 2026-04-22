# BUG REPORT: IAP-001
**Title:** IAP Plan Stuck in "Owned" state after Network Interruption (Consumption Failure)

**Severity:** High (Blocks Revenue/User Progress)
**Status:** Open

**Description:**
When a network interruption occurs exactly during the "Confirm Payment" phase, the transaction enters a pending state. Upon reconnecting, the user does not receive credits, and subsequent attempts to purchase the same plan result in a Google Play error: "You already own this item."

**Steps to Reproduce:**
1. Open the App -> Go to "Get Credit".
2. Select a plan and trigger the Google Play payment sheet.
3. Tap "Confirm" and immediately toggle Airplane Mode (Offline).
4. Wait for the error, then toggle Airplane Mode off (Online).
5. Attempt to purchase the same plan again.

**Actual Result:**
Google Play displays: "You already own this item." No credits are added to the user account. The transaction is stuck and the plan is unpurchasable.

**Expected Result:**
The app should detect the unconsumed purchase upon reconnecting, consume the item, grant the credits, and clear the "Owned" state so the user can purchase again.

**Notes:**
- Developer needs to verify `consumeAsync` logic and ensure it runs on app resume for any pending/unconsumed purchases.
