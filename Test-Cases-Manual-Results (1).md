# SauceDemo – Test Cases

**Author:** Aya Mohammed
**Last updated:** 2026-10-16
**Application Under Test (AUT):** [SauceDemo](https://www.saucedemo.com) – a public demo e-commerce site built for QA practice (not owned by me)
**Test type:** Functional testing (manual test execution + automation with Java, Selenium and TestNG)

---

## 1. Scope

**In scope:** Login, Inventory (products page), Cart, Checkout, Logout.
**Out of scope:** Performance, security, cross-browser and mobile testing.

## 2. Test Environment

| Item | Value |
|---|---|
| Browser | Google Chrome (latest) |
| OS | Windows 11 |
| URL | https://www.saucedemo.com |
| Automation | Java, Selenium WebDriver 4, TestNG 7.9, Maven |

## 3. Test Data

Credentials are published on the SauceDemo login page for practice.

| Username | Password | Purpose |
|---|---|---|
| `standard_user` | `secret_sauce` | Valid user |
| `locked_out_user` | `secret_sauce` | Blocked user |
| `wrong_password` (as password) | – | Invalid credentials scenario |

Checkout data: First name `Aya`, Last name `Mohammed`, Postal code `11118`.

## 4. Legend

| Field | Values |
|---|---|
| **Priority / Group** | Priority: High / Medium / Low. Group: `smoke` = critical path, quick check after each build. `regression` = full verification. |
| **Actual Result** | What really happened when the test was executed manually. |
| **Status** | **Pass** = actual result matches expected. **Fail** = it does not match (add the bug ID, e.g. Fail – BUG-001). **Blocked** = could not be executed. **Not Run** = not executed yet. |
| **Automation** | Name of the TestNG test that covers the case (`Class.method`), or **Planned** if it is not automated yet. |

---

## 5. Test Cases

### 5.1 Login

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-LOGIN-001 | Login with valid credentials | 1. Open the site<br>2. Enter username `standard_user`<br>3. Enter password `secret_sauce`<br>4. Click **Login** | User is redirected to the inventory page (URL contains `inventory`) and the products list is displayed | User is redirected to the inventory page (URL contains `inventory`) and the products list is displayed | Pass | High / smoke | `LoginTests.validLogin` |
| TC-LOGIN-002 | Login with wrong password | 1. Open the site<br>2. Enter username `standard_user`<br>3. Enter password `wrong_password`<br>4. Click **Login** | Error message: "Username and password do not match any user in this service". User stays on the login page | Error message: "Username and password do not match any user in this service". User stays on the login page | Pass | High / regression | `LoginTests.wrongPassword` |
| TC-LOGIN-003 | Login with locked-out user | 1. Open the site<br>2. Enter username `locked_out_user`<br>3. Enter password `secret_sauce`<br>4. Click **Login** | Error message: "Sorry, this user has been locked out." User stays on the login page | Error message: "Sorry, this user has been locked out." User stays on the login page | Pass | Medium / regression | `LoginTests.lockedUser` |
| TC-LOGIN-004 | Login with empty username and password | 1. Open the site<br>2. Leave both fields empty<br>3. Click **Login** | Error message: "Username is required" | | Not Run | Medium / regression | Planned |
| TC-LOGIN-005 | Login with empty password | 1. Open the site<br>2. Enter username `standard_user`<br>3. Leave password empty<br>4. Click **Login** | Error message: "Password is required" | Error message: "Password is required" | Pass | Medium / regression | Planned |
| TC-LOGIN-006 | Access inventory page without logging in | 1. Open a new session<br>2. Go directly to `/inventory.html` | User is redirected to the login page with an error saying the page can only be accessed when logged in | User is redirected to the login page with an error saying the page can only be accessed when logged in | Pass | Medium / regression | Planned |

### 5.2 Inventory

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-INV-001 | Products are displayed after login | 1. Login as `standard_user`<br>2. Observe the products page | 6 products are displayed, each with image, name, description, price and an **Add to cart** button | 6 products are displayed, each with image, name, description, price and an **Add to cart** button | Pass | High / smoke | Planned |
| TC-INV-002 | Sort products by price (low to high) | 1. Login as `standard_user`<br>2. Select **Price (low to high)** from the sort dropdown | Products are listed in ascending price order | Products are listed in ascending price order | Pass | Medium / regression | Planned |
| TC-INV-003 | Open product details page | 1. Login as `standard_user`<br>2. Click on a product name | Details page opens and shows the same name and price as the products list | Details page opens and shows the same name and price as the products list | Pass | Medium / regression | Planned |

### 5.3 Cart

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-CART-001 | Add one product to the cart | 1. Login as `standard_user`<br>2. Click **Add to cart** on a product | Cart badge shows `1` and the button changes to **Remove** | Cart badge shows `1` and the button changes to **Remove** | Pass | High / smoke | Planned |
| TC-CART-002 | Add multiple products to the cart | 1. Login as `standard_user`<br>2. Add two different products<br>3. Open the cart | Cart badge shows `2` and both products are listed in the cart | Cart badge shows `2` and both products are listed in the cart | Pass | High / regression | Planned |
| TC-CART-003 | Remove a product from the cart | 1. Login and add a product<br>2. Open the cart<br>3. Click **Remove** | Product is removed from the list and the cart badge disappears | Product is removed from the list and the cart badge disappears | Pass | Medium / regression | Planned |

### 5.4 Checkout

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-CHK-001 | Complete a purchase with valid information | 1. Login and add a product<br>2. Open the cart and click **Checkout**<br>3. Enter first name, last name and postal code<br>4. Click **Continue**<br>5. Click **Finish** | Overview page shows the item and total. Confirmation page displays "Thank you for your order!" | Overview page shows the item and total. Confirmation page displays "Thank you for your order!" | Pass | High / smoke | Planned |
| TC-CHK-002 | Checkout with missing first name | 1. Login, add a product, click **Checkout**<br>2. Leave first name empty, fill the other fields<br>3. Click **Continue** | Error message: "First Name is required". User stays on the same step | Error message: "First Name is required". User stays on the same step | Pass | Medium / regression | Planned |
| TC-CHK-003 | Checkout with missing postal code | 1. Login, add a product, click **Checkout**<br>2. Leave postal code empty, fill the other fields<br>3. Click **Continue** | Error message: "Postal Code is required". User stays on the same step | Error message: "Postal Code is required". User stays on the same step | Pass | Medium / regression | Planned |

### 5.5 Logout

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-OUT-001 | Logout from the application | 1. Login as `standard_user`<br>2. Open the menu (top left)<br>3. Click **Logout** | User is returned to the login page and the username and password fields are empty | User is returned to the login page and the username and password fields are empty | Pass | Medium / smoke | Planned |

---

## 6. Bug-Related Test Cases

These cases correspond to the bug reports in `Bug-Reports.md`. The matching BUG ID is included in each test case. BUG-009 needs response-time measurements; BUG-015 needs requirements confirmation.

### TC-BUG-001 — Product sorting displays an error

- **Test Case ID:** `TC-BUG-001`
- **Related Bug:** `BUG-001`
- **Account:** `error_user`
- **Module:** Products / Sort
- **Severity:** Major (proposed; confirm impact)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-001
- **Automation:** Planned

#### Test Steps

1. Log in using the `error_user` test account.
2. Open the Products page.
3. Use the product sort/filter dropdown.
4. Observe the result.

#### Expected Result

Selecting a sort option should reorder the product list according to the selected option, without displaying an application error.

#### Actual Result

Sorting does not work as expected. The page displays the message: `Sorting is broken! This error has been reported to Backtrace.`

#### Evidence

Refer to `BUG-001` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-002 — Remove button does not work on the Products page

- **Test Case ID:** `TC-BUG-002`
- **Related Bug:** `BUG-002`
- **Account:** `error_user`
- **Module:** Products / Cart
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-002
- **Automation:** Planned

#### Test Steps

1. Log in using `error_user`.
2. On the Products page, add a product to the cart.
3. Click the product's Remove button.
4. Observe the button and cart count.

#### Expected Result

Clicking Remove on the Products page should remove that product from the cart and update the cart count.

#### Actual Result

The Remove button does not work on the Products page. The user reported that Remove works on the Cart page.

#### Evidence

Refer to `BUG-002` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-003 — Finish button does not respond during checkout

- **Test Case ID:** `TC-BUG-003`
- **Related Bug:** `BUG-003`
- **Account:** `error_user`
- **Module:** Checkout Overview
- **Severity:** Blocker (proposed; confirm whether all checkout completion is prevented)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-003
- **Automation:** Planned

#### Test Steps

1. Log in using `error_user`.
2. Add a product to the cart.
3. Proceed through checkout and fill in the required information.
4. On the Checkout Overview page, click Finish.
5. Observe the result.

#### Expected Result

Clicking Finish with valid checkout information should complete the demo order and show the order confirmation page.

#### Actual Result

The Finish button does not respond when clicked.

#### Evidence

Refer to `BUG-003` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-004 — Continue proceeds when Last Name is blank

- **Test Case ID:** `TC-BUG-004`
- **Related Bug:** `BUG-004`
- **Account:** `error_user`
- **Module:** Checkout Information
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-004
- **Automation:** Planned

#### Test Steps

1. Log in using `error_user`.
2. Add a product to the cart and open checkout.
3. Enter the other checkout information but leave Last Name blank.
4. Click Continue.

#### Expected Result

If Last Name is required, the form should remain on the Checkout Information page and display a clear validation message.

#### Actual Result

The user reports that Continue proceeds even though Last Name is blank.

#### Evidence

Refer to `BUG-004` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-005 — Checkout button is incorrectly positioned

- **Test Case ID:** `TC-BUG-005`
- **Related Bug:** `BUG-005`
- **Account:** `visual_user`
- **Module:** Cart / UI layout
- **Severity:** Minor (proposed)
- **Priority:** Medium (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-005
- **Automation:** Planned

#### Test Steps

1. Log in using `visual_user`.
2. Add a product to the cart.
3. Open the Cart page.
4. Observe the Checkout button placement.

#### Expected Result

The Checkout button should be aligned consistently with the intended cart page layout and nearby controls.

#### Actual Result

The Checkout button appears higher on the page than expected.

#### Evidence

Refer to `BUG-005` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-006 — Cart is incorrectly positioned

- **Test Case ID:** `TC-BUG-006`
- **Related Bug:** `BUG-006`
- **Account:** `visual_user`
- **Module:** Products / UI layout
- **Severity:** Minor (proposed)
- **Priority:** Medium (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-006
- **Automation:** Planned

#### Test Steps

1. Log in using `visual_user`.
2. Open the Products page.
3. Observe the shopping cart icon/location.

#### Expected Result

The cart should be positioned consistently with the intended page layout and header alignment.

#### Actual Result

The cart appears at the edge of the page rather than in its expected position.

#### Evidence

Refer to `BUG-006` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-007 — Product image does not match its description

- **Test Case ID:** `TC-BUG-007`
- **Related Bug:** `BUG-007`
- **Account:** `visual_user`
- **Module:** Products / Product content
- **Severity:** Major (proposed)
- **Priority:** Medium
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-007
- **Automation:** Planned

#### Test Steps

1. Log in using `visual_user`.
2. Open the Products page.
3. Compare product names/descriptions with their displayed images.

#### Expected Result

Each product image should correspond to the displayed product name and description.

#### Actual Result

A product described as a bag appears with a dog image instead of the expected bag image.

#### Evidence

Refer to `BUG-007` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-008 — Product prices change after sorting

- **Test Case ID:** `TC-BUG-008`
- **Related Bug:** `BUG-008`
- **Account:** `visual_user`
- **Module:** Products / Sorting and pricing
- **Severity:** Major (proposed; verify whether displayed prices actually change)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-008
- **Automation:** Planned

#### Test Steps

1. Log in using `visual_user`.
2. Record the name and price of at least two products.
3. Select a different sort option.
4. Compare each product's price before and after sorting.

#### Expected Result

Sorting should change product order only. Each product's price should remain associated with the same product.

#### Actual Result

The user reports that prices change when sorting products.

#### Evidence

Refer to `BUG-008` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-009 — Product interactions have a long response time

- **Test Case ID:** `TC-BUG-009`
- **Related Bug:** `BUG-009`
- **Account:** `performance_glitch_user`
- **Module:** Products / Performance
- **Severity:** Major (proposed; measure before final classification)
- **Priority:** Medium
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-009 (timing not measured)
- **Automation:** Planned

#### Test Steps

1. Log in using `performance_glitch_user`.
2. Click a product interaction, such as Add to cart.
3. Measure the time until the interface responds.
4. Repeat with the same action and record the timings.

#### Expected Result

The interface should respond within the team's agreed performance threshold.

#### Actual Result

The site responds slowly after interactions; there is a noticeable delay before the click action takes effect.

**Evidence note:** Record response times before finalizing severity.

#### Evidence

Refer to `BUG-009` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-010 — Some Add to cart buttons do not work

- **Test Case ID:** `TC-BUG-010`
- **Related Bug:** `BUG-010`
- **Account:** `problem_user`
- **Module:** Products / Cart
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-010
- **Automation:** Planned

#### Test Steps

1. Log in using `problem_user`.
2. On the Products page, click Add to cart for the affected product(s).
3. Check the button state and cart count.
4. Open the Cart page and verify whether the selected product was added.

#### Expected Result

Clicking Add to cart should add the selected product and update the cart count and button state.

#### Actual Result

Some Add to cart buttons do not work as expected.

#### Evidence

Refer to `BUG-010` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-011 — Product sorting does not work and displays an error

- **Test Case ID:** `TC-BUG-011`
- **Related Bug:** `BUG-011`
- **Account:** `problem_user`
- **Module:** Products / Sort
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-011
- **Automation:** Planned

#### Test Steps

1. Log in using `problem_user`.
2. Open the product sort dropdown.
3. Select a sort option.
4. Observe the product list and any error message.

#### Expected Result

Products should be reordered according to the selected sort option without an application error.

#### Actual Result

Sorting does not work as expected. The user reports the message: `Sorting is broken! This error has been reported to Backtrace.`

#### Evidence

Refer to `BUG-011` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-012 — Last Name is not entered or retained in checkout

- **Test Case ID:** `TC-BUG-012`
- **Related Bug:** `BUG-012`
- **Account:** `problem_user`
- **Module:** Checkout Information
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-012
- **Automation:** Planned

#### Test Steps

1. Log in using `problem_user`.
2. Add a product to the cart and open checkout.
3. Enter First Name, Postal Code, and Last Name.
4. Observe the Last Name field and click Continue.
5. Record whether the field retains the entered value and whether navigation succeeds.

#### Expected Result

The Last Name field should accept and retain valid input. If it is empty and required, Continue should show a validation message and prevent progression.

#### Actual Result

The user reports that Last Name does not get entered/saved correctly, while Continue can still proceed.

#### Evidence

Refer to `BUG-012` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-013 — Finish button does not respond during checkout

- **Test Case ID:** `TC-BUG-013`
- **Related Bug:** `BUG-013`
- **Account:** `problem_user`
- **Module:** Checkout Overview
- **Severity:** Blocker (proposed; confirm whether checkout completion is prevented)
- **Priority:** High (proposed)
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-013
- **Automation:** Planned

#### Test Steps

1. Log in using `problem_user`.
2. Add a product to the cart.
3. Proceed through checkout.
4. Fill the required information and reach Checkout Overview.
5. Click Finish.

#### Expected Result

Clicking Finish with valid checkout information should complete the demo order and display the confirmation page.

#### Actual Result

The Finish button does not respond.

#### Evidence

Refer to `BUG-013` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-014 — The same dog image appears for multiple products

- **Test Case ID:** `TC-BUG-014`
- **Related Bug:** `BUG-014`
- **Account:** `problem_user`
- **Module:** Products / Product images
- **Severity:** Major (proposed)
- **Priority:** Medium
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Fail — BUG-014
- **Automation:** Planned

#### Test Steps

1. Log in using `problem_user`.
2. Open the Products page.
3. Compare images across several different products.

#### Expected Result

Each product should display its correct, corresponding image.

#### Actual Result

The same dog image appears for multiple products.

#### Evidence

Refer to `BUG-014` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


### TC-BUG-015 — Cart quantity cannot be increased

- **Test Case ID:** `TC-BUG-015`
- **Related Bug:** `BUG-015`
- **Account:** `problem_user` (account association needs confirmation)`
- **Module:** Cart / Quantity
- **Severity:** Suggestion or potential usability limitation — not yet confirmed as a defect
- **Priority:** Low until requirements are checked
- **Preconditions:** SauceDemo is accessible; log in with the account listed above.
- **Status:** Needs requirements confirmation
- **Automation:** Planned

#### Test Steps

1. There is no visible option to increase the quantity of a product in the cart.

#### Expected Result

If multiple quantities per product are supported, the cart should provide a way to change quantity; otherwise, this behavior may be intentional.

#### Actual Result

No visible option to increase a product's quantity was observed. Confirm whether multiple quantities per product are required before classifying this as a confirmed defect.

#### Evidence

Refer to `BUG-015` in `Bug-Reports.md`; attach screenshots or measured results where applicable.


---

## 7. Coverage Summary

| Module | Test cases | Automated |
|---|---|---|
| Login | 6 | 3 |
| Inventory | 3 | 0 |
| Cart | 3 | 0 |
| Checkout | 3 | 0 |
| Logout | 1 | 0 |
| **Total** | **31** | **3** |

**Smoke suite (5):** TC-LOGIN-001, TC-INV-001, TC-CART-001, TC-CHK-001, TC-OUT-001

**Execution summary (update after each run):** Based on the user-reported manual execution, 15 original test cases were executed manually and marked Pass; their actual results match their expected results. TC-LOGIN-004 remains Not Run. The 15 bug-related cases are unchanged: 14 marked Fail based on reported observations and 1 needs requirements confirmation. Overall: 31 test cases — 15 Pass, 14 Fail, 1 Not Run, and 1 needs requirements confirmation.

## 8. Notes

- Expected results are based on the application's behavior at the time of writing and should be re-verified on each execution.
- Test case IDs map directly to automated tests (see the **Automation** column), so every automated test can be traced back to a documented test case.
- The **Automation** column is updated as new TestNG tests are added to the project.

---

## 9. Defect Report Template

Use this format when a test fails.

| Field | Description |
|---|---|
| **Bug ID** | BUG-001 |
| **Title** | Short, specific summary of the problem |
| **Related test case** | e.g., TC-LOGIN-002 |
| **Environment** | Browser, OS, URL |
| **Steps to reproduce** | 1. … 2. … 3. … |
| **Expected result** | What should happen |
| **Actual result** | What happened instead |
| **Severity** | Critical / Major / Minor / Trivial |
| **Attachments** | Screenshot, log file |
