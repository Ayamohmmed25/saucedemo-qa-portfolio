# SauceDemo – Bug Reports

**Application Under Test:** [SauceDemo](https://www.saucedemo.com)
**Related test cases:** `Test-Cases.md`, section **Bug-Related Test Cases** (`TC-BUG-001` to `TC-BUG-015`).

> **Execution note:** Reports reflect the behaviors described during manual testing. BUG-009 needs measured response-time evidence; BUG-015 needs requirements confirmation before it can be classified as a confirmed defect. Severity and priority are proposed and should be reviewed against impact.

---

## BUG-001 — Product sorting displays an error

- **Account:** `error_user`
- **Area:** Products / Sort
- **Related Test Case:** `TC-BUG-001`
- **Severity:** Major (proposed; confirm impact)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using the `error_user` test account.
2. Open the Products page.
3. Use the product sort/filter dropdown.
4. Observe the result.

### Actual result

Sorting does not work as expected. The page displays the message: `Sorting is broken! This error has been reported to Backtrace.`

### Expected result

Selecting a sort option should reorder the product list according to the selected option, without displaying an application error.

### Evidence

- Capture a screenshot showing the selected sort option and the error message.
- Record the selected sort option.

---

## BUG-002 — Remove button does not work on the Products page

- **Account:** `error_user`
- **Area:** Products / Cart
- **Related Test Case:** `TC-BUG-002`
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `error_user`.
2. On the Products page, add a product to the cart.
3. Click the product's Remove button.
4. Observe the button and cart count.

### Actual result

The Remove button does not work on the Products page. The user reported that Remove works on the Cart page.

### Expected result

Clicking Remove on the Products page should remove that product from the cart and update the cart count.

### Evidence

- Capture the product button and cart count before and after clicking Remove.

---

## BUG-003 — Finish button does not respond during checkout

- **Account:** `error_user`
- **Area:** Checkout Overview
- **Related Test Case:** `TC-BUG-003`
- **Severity:** Blocker (proposed; confirm whether all checkout completion is prevented)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `error_user`.
2. Add a product to the cart.
3. Proceed through checkout and fill in the required information.
4. On the Checkout Overview page, click Finish.
5. Observe the result.

### Actual result

The Finish button does not respond when clicked.

### Expected result

Clicking Finish with valid checkout information should complete the demo order and show the order confirmation page.

### Evidence

- Capture the Checkout Overview page and the result after clicking Finish.
- Note whether any error message appears.

---

## BUG-004 — Continue proceeds when Last Name is blank

- **Account:** `error_user`
- **Area:** Checkout Information
- **Related Test Case:** `TC-BUG-004`
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `error_user`.
2. Add a product to the cart and open checkout.
3. Enter the other checkout information but leave Last Name blank.
4. Click Continue.

### Actual result

The user reports that Continue proceeds even though Last Name is blank.

### Expected result

If Last Name is required, the form should remain on the Checkout Information page and display a clear validation message.

### Evidence

- Capture the form with Last Name blank and the page shown after clicking Continue.

---

## BUG-005 — Checkout button is incorrectly positioned

- **Account:** `visual_user`
- **Area:** Cart / UI layout
- **Related Test Case:** `TC-BUG-005`
- **Severity:** Minor (proposed)
- **Priority:** Medium (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `visual_user`.
2. Add a product to the cart.
3. Open the Cart page.
4. Observe the Checkout button placement.

### Actual result

The Checkout button appears higher on the page than expected.

### Expected result

The Checkout button should be aligned consistently with the intended cart page layout and nearby controls.

### Evidence

- Capture a screenshot of the full Cart page.

---

## BUG-006 — Cart is incorrectly positioned

- **Account:** `visual_user`
- **Area:** Products / UI layout
- **Related Test Case:** `TC-BUG-006`
- **Severity:** Minor (proposed)
- **Priority:** Medium (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `visual_user`.
2. Open the Products page.
3. Observe the shopping cart icon/location.

### Actual result

The cart appears at the edge of the page rather than in its expected position.

### Expected result

The cart should be positioned consistently with the intended page layout and header alignment.

### Evidence

- Capture a screenshot showing the header and cart position.

---

## BUG-007 — Product image does not match its description

- **Account:** `visual_user`
- **Area:** Products / Product content
- **Related Test Case:** `TC-BUG-007`
- **Severity:** Major (proposed)
- **Priority:** Medium
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `visual_user`.
2. Open the Products page.
3. Compare product names/descriptions with their displayed images.

### Actual result

A product described as a bag appears with a dog image instead of the expected bag image.

### Expected result

Each product image should correspond to the displayed product name and description.

### Evidence

- Capture the product name/description and mismatched image in the same screenshot.

---

## BUG-008 — Product prices change after sorting

- **Account:** `visual_user`
- **Area:** Products / Sorting and pricing
- **Related Test Case:** `TC-BUG-008`
- **Severity:** Major (proposed; verify whether displayed prices actually change)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `visual_user`.
2. Record the name and price of at least two products.
3. Select a different sort option.
4. Compare each product's price before and after sorting.

### Actual result

The user reports that prices change when sorting products.

### Expected result

Sorting should change product order only. Each product's price should remain associated with the same product.

### Evidence

- Record product names and prices before and after sorting.
- Capture screenshots if the same product's displayed price changes.

---

## BUG-009 — Product interactions have a long response time

- **Account:** `performance_glitch_user`
- **Area:** Products / Performance
- **Related Test Case:** `TC-BUG-009`
- **Severity:** Major (proposed; measure before final classification)
- **Priority:** Medium
- **Status:** Reported — needs measurement

### Steps to reproduce

1. Log in using `performance_glitch_user`.
2. Click a product interaction, such as Add to cart.
3. Measure the time until the interface responds.
4. Repeat with the same action and record the timings.

### Actual result

The site responds slowly after interactions; there is a noticeable delay before the click action takes effect.

### Expected result

The interface should respond within the team's agreed performance threshold.

### Evidence

- Record the action, number of repetitions, and observed response times.
- Include a screen recording if possible.

**Note:** No response-time threshold or measured timings were provided, so this is an initial performance observation rather than a quantified performance defect.

---

## BUG-010 — Some Add to cart buttons do not work

- **Account:** `problem_user`
- **Area:** Products / Cart
- **Related Test Case:** `TC-BUG-010`
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `problem_user`.
2. On the Products page, click Add to cart for the affected product(s).
3. Check the button state and cart count.
4. Open the Cart page and verify whether the selected product was added.

### Actual result

Some Add to cart buttons do not work as expected.

### Expected result

Clicking Add to cart should add the selected product and update the cart count and button state.

### Evidence

- Record the affected product name(s).
- Capture the button and cart count before and after clicking.

---

## BUG-011 — Product sorting does not work and displays an error

- **Account:** `problem_user`
- **Area:** Products / Sort
- **Related Test Case:** `TC-BUG-011`
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `problem_user`.
2. Open the product sort dropdown.
3. Select a sort option.
4. Observe the product list and any error message.

### Actual result

Sorting does not work as expected. The user reports the message: `Sorting is broken! This error has been reported to Backtrace.`

### Expected result

Products should be reordered according to the selected sort option without an application error.

### Evidence

- Capture the selected sort option, product order, and error message.

---

## BUG-012 — Last Name is not entered or retained in checkout

- **Account:** `problem_user`
- **Area:** Checkout Information
- **Related Test Case:** `TC-BUG-012`
- **Severity:** Major (proposed)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `problem_user`.
2. Add a product to the cart and open checkout.
3. Enter First Name, Postal Code, and Last Name.
4. Observe the Last Name field and click Continue.
5. Record whether the field retains the entered value and whether navigation succeeds.

### Actual result

The user reports that Last Name does not get entered/saved correctly, while Continue can still proceed.

### Expected result

The Last Name field should accept and retain valid input. If it is empty and required, Continue should show a validation message and prevent progression.

### Evidence

- Capture the filled form immediately before clicking Continue and the page immediately after.

---

## BUG-013 — Finish button does not respond during checkout

- **Account:** `problem_user`
- **Area:** Checkout Overview
- **Related Test Case:** `TC-BUG-013`
- **Severity:** Blocker (proposed; confirm whether checkout completion is prevented)
- **Priority:** High (proposed)
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `problem_user`.
2. Add a product to the cart.
3. Proceed through checkout.
4. Fill the required information and reach Checkout Overview.
5. Click Finish.

### Actual result

The Finish button does not respond.

### Expected result

Clicking Finish with valid checkout information should complete the demo order and display the confirmation page.

### Evidence

- Capture the Checkout Overview page and the result after clicking Finish.

---

## BUG-014 — The same dog image appears for multiple products

- **Account:** `problem_user`
- **Area:** Products / Product images
- **Related Test Case:** `TC-BUG-014`
- **Severity:** Major (proposed)
- **Priority:** Medium
- **Status:** Reported — needs retest

### Steps to reproduce

1. Log in using `problem_user`.
2. Open the Products page.
3. Compare images across several different products.

### Actual result

The same dog image appears for multiple products.

### Expected result

Each product should display its correct, corresponding image.

### Evidence

- Capture multiple product cards showing the repeated dog image and their different product names.

---

## BUG-015 — Cart quantity cannot be increased

- **Account:** `problem_user` (account association needs confirmation)
- **Area:** Cart / Quantity
- **Related Test Case:** `TC-BUG-015`
- **Severity:** Suggestion or potential usability limitation — not yet confirmed as a defect
- **Priority:** Low until requirements are checked
- **Status:** Needs requirements review

### Observation

There is no visible option to increase the quantity of a product in the cart.

### Expected result

This depends on the application's requirements. If multiple quantities per product are supported, the user should be able to increase quantity. If the demo intentionally allows only one unit per cart item, the missing quantity control is not necessarily a bug.

### Evidence

- Capture the Cart page and inspect the available quantity controls.