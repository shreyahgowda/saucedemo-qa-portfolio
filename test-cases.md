# Test Cases — Swag Labs (SauceDemo)

**Application URL:** https://www.saucedemo.com  
**Tester:** Shreya  
**Browser / OS:** Google Chrome / Windows  

| Test ID | Module | Test Scenario | Test Steps | Test Data | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-01** | Login | Valid login with standard user | 1. Open URL<br>2. Enter valid username & password<br>3. Click Login | `standard_user` / `secret_sauce` | User is redirected to `/inventory.html` and product catalog loads | Redirected to `/inventory.html` cleanly | **Pass** |
| **TC-02** | Login | Login blocked for locked-out user | 1. Open URL<br>2. Enter locked username & password<br>3. Click Login | `locked_out_user` / `secret_sauce` | Login fails with locked-out error message | Displayed exact locked-out error message | **Pass** |
| **TC-03** | Login | Login with invalid username | 1. Open URL<br>2. Enter misspelled username & password<br>3. Click Login | `roblem_user` / `secret_sauce` | Login fails with username/password mismatch error | Error message displayed; user stays on login page (`screenshots/bug-01-invalid-login.png`) | **Pass** |
| **TC-04** | Login | Login with empty credentials | 1. Open URL<br>2. Leave fields blank<br>3. Click Login | `""` / `""` | Validation error: *"Epic sadface: Username is required"* | Displayed username required error | **Pass** |
| **TC-05** | Inventory | Verify product images for problem user | 1. Log in as `problem_user`<br>2. Inspect product catalog thumbnails | `problem_user` / `secret_sauce` | Each product displays its matching product image | All products display the same dog image (`sl-404`) | **Fail** |
| **TC-06** | Inventory | Sort products by Price (Low to High) | 1. Log in as `problem_user`<br>2. Select **Price (low to high)** from sort dropdown | `problem_user` | Products reorder from lowest (`$7.99`) to highest (`$49.99`) | Dropdown does not change product order | **Fail** |
| **TC-07** | Cart | Add all catalog items to cart (`problem_user`) | 1. Log in as `problem_user`<br>2. Click **Add to cart** on all 6 items | `problem_user` | All 6 items are added to the cart | Only 3 items add; Bolt T-Shirt, Fleece Jacket, and Red T-Shirt fail to add | **Fail** |
| **TC-08** | Cart | Remove added items from Inventory page (`problem_user`) | 1. Log in as `problem_user`<br>2. Click **Remove** on an added item on `/inventory.html` | `problem_user` | Item is removed from cart and button reverts to **Add to cart** | **Remove** button does nothing on `/inventory.html` (works only inside `/cart.html`) | **Fail** |
| **TC-09** | Checkout | Enter Last Name on checkout form (`problem_user`) | 1. Log in as `problem_user`<br>2. Add item & go to Checkout Step One<br>3. Type in **Last Name** field | `problem_user` | Text appears in Last Name field while First Name remains intact | Typing in Last Name overwrites First Name and blocks checkout | **Fail** |
| **TC-10** | Checkout | Complete checkout with valid user info | 1. Log in as `standard_user`<br>2. Add item to cart & click Checkout<br>3. Enter First Name, Last Name, Zip & Continue<br>4. Click Finish | `standard_user` | Order confirmation screen displays *"Thank you for your order!"* | Order completed successfully | **Pass** |