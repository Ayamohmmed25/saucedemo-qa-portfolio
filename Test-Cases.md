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
| TC-LOGIN-001 | Login with valid credentials | 1. Open the site<br>2. Enter username `standard_user`<br>3. Enter password `secret_sauce`<br>4. Click **Login** | User is redirected to the inventory page (URL contains `inventory`) and the products list is displayed | | Not Run | High / smoke | `LoginTests.validLogin` |
| TC-LOGIN-002 | Login with wrong password | 1. Open the site<br>2. Enter username `standard_user`<br>3. Enter password `wrong_password`<br>4. Click **Login** | Error message: "Username and password do not match any user in this service". User stays on the login page | | Not Run | High / regression | `LoginTests.wrongPassword` |
| TC-LOGIN-003 | Login with locked-out user | 1. Open the site<br>2. Enter username `locked_out_user`<br>3. Enter password `secret_sauce`<br>4. Click **Login** | Error message: "Sorry, this user has been locked out." User stays on the login page | | Not Run | Medium / regression | `LoginTests.lockedUser` |
| TC-LOGIN-004 | Login with empty username and password | 1. Open the site<br>2. Leave both fields empty<br>3. Click **Login** | Error message: "Username is required" | | Not Run | Medium / regression | Planned |
| TC-LOGIN-005 | Login with empty password | 1. Open the site<br>2. Enter username `standard_user`<br>3. Leave password empty<br>4. Click **Login** | Error message: "Password is required" | | Not Run | Medium / regression | Planned |
| TC-LOGIN-006 | Access inventory page without logging in | 1. Open a new session<br>2. Go directly to `/inventory.html` | User is redirected to the login page with an error saying the page can only be accessed when logged in | | Not Run | Medium / regression | Planned |

### 5.2 Inventory

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-INV-001 | Products are displayed after login | 1. Login as `standard_user`<br>2. Observe the products page | 6 products are displayed, each with image, name, description, price and an **Add to cart** button | | Not Run | High / smoke | Planned |
| TC-INV-002 | Sort products by price (low to high) | 1. Login as `standard_user`<br>2. Select **Price (low to high)** from the sort dropdown | Products are listed in ascending price order | | Not Run | Medium / regression | Planned |
| TC-INV-003 | Open product details page | 1. Login as `standard_user`<br>2. Click on a product name | Details page opens and shows the same name and price as the products list | | Not Run | Medium / regression | Planned |

### 5.3 Cart

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-CART-001 | Add one product to the cart | 1. Login as `standard_user`<br>2. Click **Add to cart** on a product | Cart badge shows `1` and the button changes to **Remove** | | Not Run | High / smoke | Planned |
| TC-CART-002 | Add multiple products to the cart | 1. Login as `standard_user`<br>2. Add two different products<br>3. Open the cart | Cart badge shows `2` and both products are listed in the cart | | Not Run | High / regression | Planned |
| TC-CART-003 | Remove a product from the cart | 1. Login and add a product<br>2. Open the cart<br>3. Click **Remove** | Product is removed from the list and the cart badge disappears | | Not Run | Medium / regression | Planned |

### 5.4 Checkout

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-CHK-001 | Complete a purchase with valid information | 1. Login and add a product<br>2. Open the cart and click **Checkout**<br>3. Enter first name, last name and postal code<br>4. Click **Continue**<br>5. Click **Finish** | Overview page shows the item and total. Confirmation page displays "Thank you for your order!" | | Not Run | High / smoke | Planned |
| TC-CHK-002 | Checkout with missing first name | 1. Login, add a product, click **Checkout**<br>2. Leave first name empty, fill the other fields<br>3. Click **Continue** | Error message: "First Name is required". User stays on the same step | | Not Run | Medium / regression | Planned |
| TC-CHK-003 | Checkout with missing postal code | 1. Login, add a product, click **Checkout**<br>2. Leave postal code empty, fill the other fields<br>3. Click **Continue** | Error message: "Postal Code is required". User stays on the same step | | Not Run | Medium / regression | Planned |

### 5.5 Logout

| ID | Title | Steps | Expected Result | Actual Result | Status | Priority / Group | Automation |
|---|---|---|---|---|---|---|---|
| TC-OUT-001 | Logout from the application | 1. Login as `standard_user`<br>2. Open the menu (top left)<br>3. Click **Logout** | User is returned to the login page and the username and password fields are empty | | Not Run | Medium / smoke | Planned |

---

## 6. Coverage Summary

| Module | Test cases | Automated |
|---|---|---|
| Login | 6 | 3 |
| Inventory | 3 | 0 |
| Cart | 3 | 0 |
| Checkout | 3 | 0 |
| Logout | 1 | 0 |
| **Total** | **16** | **3** |

**Smoke suite (5):** TC-LOGIN-001, TC-INV-001, TC-CART-001, TC-CHK-001, TC-OUT-001

**Execution summary (update after each run):** Pass 0 | Fail 0 | Blocked 0 | Not Run 16

## 7. Notes

- Expected results are based on the application's behavior at the time of writing and should be re-verified on each execution.
- Test case IDs map directly to automated tests (see the **Automation** column), so every automated test can be traced back to a documented test case.
- The **Automation** column is updated as new TestNG tests are added to the project.

---

## 8. Defect Report Template

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
