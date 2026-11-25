# Defect / Bug Reports — Swag Labs (SauceDemo)

---

### BUG-01: Last Name Input Overwrites First Name and Blocks Checkout (`problem_user`)
- **Severity:** High | **Priority:** High
- **Environment:** Google Chrome, Desktop Web (`https://www.saucedemo.com/checkout-step-one.html`)
- **Preconditions:** Logged in as `problem_user` with at least 1 item in the cart
- **Steps to Reproduce:**
  1. Click the **Cart** icon and click **Checkout**.
  2. Enter a First Name in the **First Name** field.
  3. Click the **Last Name** field and type a Last Name.
  4. Enter a Zip/Postal Code and click **Continue**.
- **Expected Result:** First Name remains intact, Last Name accepts input, and clicking Continue navigates to `checkout-step-two.html`.
- **Actual Result:** Typing in the Last Name field overwrites the First Name field, leaving Last Name blank and triggering *"Error: Last Name is required"*, blocking checkout.
- **Evidence:** `screenshots/bug-04-checkout-lastname.png`

---

### BUG-02: "Add to cart" Unresponsive for 3 Specific Products (`problem_user`)
- **Severity:** High | **Priority:** High
- **Environment:** Google Chrome, Desktop Web (`https://www.saucedemo.com/inventory.html`)
- **Preconditions:** Logged in with `problem_user` / `secret_sauce`
- **Steps to Reproduce:**
  1. Navigate to the Inventory page (`/inventory.html`).
  2. Immediately click **Add to cart** on **Sauce Labs Bolt T-Shirt**, **Sauce Labs Fleece Jacket**, and **Test.allTheThings() T-Shirt (Red)**.
- **Expected Result:** All 6 products on the catalog page can be added to the shopping cart, toggling each button to **Remove** and incrementing the cart badge.
- **Actual Result:** Only 3 products (Backpack, Bike Light, Onesie) can be added immediately; the **Add to cart** buttons for the remaining 3 products are unresponsive.
- **Reproducibility & Timing Notes:** Fails consistently immediately after logging in as `problem_user`. However, if the session sits idle on `/inventory.html` for a period before interacting, all 6 **Add to cart** controls become responsive—indicating a client-side timing or session-state bug.
- **Evidence:** `screenshots/bug-05-add-to-cart-broken.png`

---

### BUG-03: "Remove" Button Unresponsive on Inventory Page for Added Items (`problem_user`)
- **Severity:** Medium | **Priority:** Medium
- **Environment:** Google Chrome, Desktop Web (`https://www.saucedemo.com/inventory.html`)
- **Preconditions:** Logged in as `problem_user` with items added to the cart (`Sauce Labs Backpack`, `Sauce Labs Bike Light`, `Sauce Labs Onesie`)
- **Steps to Reproduce:**
  1. On the Inventory (home) page (`/inventory.html`), locate an added item displaying the red **Remove** button.
  2. Click **Remove** on the Inventory page immediately after adding.
  3. *(Workaround Verification)* Click the **Cart** icon in the top-right corner (`/cart.html`) and click **Remove** there.
- **Expected Result:** Clicking **Remove** on the Inventory page removes the item from the cart, decrements the cart badge count, and reverts the button to **Add to cart**.
- **Actual Result:** Clicking **Remove** on the Inventory page does nothing initially; items can only be removed after navigating to the Cart page (`/cart.html`).
- **Reproducibility & Timing Notes:** Fails immediately upon initial interaction under `problem_user`, whereas waiting for an idle period allows the Inventory page **Remove** buttons to respond normally.
- **Evidence:** `screenshots/bug-05-add-to-cart-broken.png`

---

### BUG-04: Incorrect Product Images Displayed Across Catalog (`problem_user`)
- **Severity:** Medium | **Priority:** Medium
- **Environment:** Google Chrome, Desktop Web (`https://www.saucedemo.com/inventory.html`)
- **Preconditions:** Logged in with `problem_user` / `secret_sauce`
- **Steps to Reproduce:**
  1. Navigate to `https://www.saucedemo.com`.
  2. Enter username `problem_user` and password `secret_sauce`.
  3. Click **Login** and observe the product catalog images.
- **Expected Result:** Each product card should display its respective product photograph (Backpack, Bike Light, Bolt T-Shirt, etc.).
- **Actual Result:** All 6 product cards display an identical placeholder dog image (`sl-404`).
- **Evidence:** `screenshots/bug-02-wrong-images.png`

---

### BUG-05: Product Sorting Dropdown Non-Functional (`problem_user`)
- **Severity:** Medium | **Priority:** Low
- **Environment:** Google Chrome, Desktop Web (`https://www.saucedemo.com/inventory.html`)
- **Preconditions:** Logged in with `problem_user` / `secret_sauce`
- **Steps to Reproduce:**
  1. On the Inventory page, click the sort dropdown in the top-right corner (`Name (A to Z)`).
  2. Select **Price (low to high)** or **Name (Z to A)**.
- **Expected Result:** Product cards dynamically reorder according to the selected sort option.
- **Actual Result:** Product order remains frozen in default `A to Z` order regardless of selection.
- **Evidence:** `screenshots/bug-03-sort-broken.png`