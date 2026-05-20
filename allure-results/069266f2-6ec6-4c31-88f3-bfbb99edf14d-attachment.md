# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: order.spec.js >> End-to-End Order
- Location: tests\order.spec.js:7:5

# Error details

```
Test timeout of 30000ms exceeded.
```

```
Error: locator.fill: Target page, context or browser has been closed
```

# Page snapshot

```yaml
- generic [ref=e3]:
  - generic [ref=e4]:
    - generic [ref=e5]:
      - generic [ref=e6]:
        - generic:
          - generic:
            - generic [ref=e7]:
              - button "Open Menu" [ref=e8] [cursor=pointer]
              - img "Open Menu" [ref=e9]
            - generic [ref=e10]:
              - navigation [ref=e12]:
                - link [ref=e13] [cursor=pointer]:
                  - /url: "#"
                  - text: All Items
                - link [ref=e14] [cursor=pointer]:
                  - /url: https://saucelabs.com/
                  - text: About
                - link [ref=e15] [cursor=pointer]:
                  - /url: "#"
                  - text: Logout
                - link [ref=e16] [cursor=pointer]:
                  - /url: "#"
                  - text: Reset App State
              - generic [ref=e17]:
                - button [ref=e18] [cursor=pointer]: Close Menu
                - img [ref=e19]
        - generic [ref=e21]: Swag Labs
        - generic [ref=e24]: "1"
      - generic [ref=e26]: Your Cart
    - generic [ref=e28]:
      - generic [ref=e29]:
        - generic [ref=e30]: QTY
        - generic [ref=e31]: Description
        - generic [ref=e32]:
          - generic [ref=e33]: "1"
          - generic [ref=e34]:
            - link "Sauce Labs Backpack" [ref=e35]:
              - /url: "#"
              - generic [ref=e36]: Sauce Labs Backpack
            - generic [ref=e37]: carry.allTheThings() with the sleek, streamlined Sly Pack that melds uncompromising style with unequaled laptop and tablet protection.
            - generic [ref=e38]:
              - generic [ref=e39]: $29.99
              - button "Remove" [ref=e40] [cursor=pointer]
      - generic [ref=e41]:
        - button "Go back Continue Shopping" [ref=e42] [cursor=pointer]:
          - img "Go back" [ref=e43]
          - text: Continue Shopping
        - button "Checkout" [ref=e44] [cursor=pointer]
  - contentinfo [ref=e45]:
    - list [ref=e46]:
      - listitem [ref=e47]:
        - link "Twitter" [ref=e48]:
          - /url: https://twitter.com/saucelabs
      - listitem [ref=e49]:
        - link "Facebook" [ref=e50]:
          - /url: https://www.facebook.com/saucelabs
      - listitem [ref=e51]:
        - link "LinkedIn" [ref=e52]:
          - /url: https://www.linkedin.com/company/sauce-labs/
    - generic [ref=e53]: © 2026 Sauce Labs. All Rights Reserved. Terms of Service | Privacy Policy
```

# Test source

```ts
  1  | export class CheckoutPage {
  2  |   constructor(page) {
  3  |     this.page = page;
  4  |     this.checkoutBtn = page.locator('#checkout');
  5  |     this.firstName = page.locator('#first-name');
  6  |     this.lastName = page.locator('#last-name');
  7  |     this.zip = page.locator('#postal-code');
  8  |     this.continueBtn = page.locator('#continue');
  9  |     this.finishBtn = page.locator('#finish');
  10 |     this.successMsg = page.locator('.complete-header');
  11 |   }
  12 | 
  13 |   async completeCheckout() {
  14 |     await this.checkoutBtn.click();
> 15 |     await this.firstName.fill('Test');
     |                          ^ Error: locator.fill: Target page, context or browser has been closed
  16 |     await this.lastName.fill('User');
  17 |     await this.zip.fill('600001');
  18 |     await this.continueBtn.click();
  19 |     await this.finishBtn.click();
  20 |   }
  21 | 
  22 |   async successText() {
  23 |     return this.successMsg.textContent();
  24 |   }
  25 | }
```