# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: api.spec.js >> POST Order
- Location: tests\api.spec.js:28:5

# Error details

```
Error: expect(received).toBe(expected) // Object.is equality

Expected: 201
Received: 401
```

# Test source

```ts
  1  | import { test, expect, request } from '@playwright/test';
  2  | 
  3  | let token;
  4  | 
  5  | test('Create Token', async () => {
  6  |   const api = await request.newContext();
  7  | 
  8  |   const res = await api.post('/api-clients/', {
  9  |     baseURL: 'https://simple-books-api.glitch.me',
  10 |     data: {
  11 |       clientName: 'PlaywrightUser',
  12 |       clientEmail: `user${Date.now()}@mail.com`
  13 |     }
  14 |   });
  15 | 
  16 |   const body = await res.json();
  17 |   token = body.accessToken;
  18 | 
  19 |   expect(res.status()).toBe(201);
  20 | });
  21 | 
  22 | test('GET Books', async ({ request }) => {
  23 |   const res = await request.get('https://simple-books-api.glitch.me/books');
  24 | 
  25 |   expect(res.status()).toBe(200);
  26 | });
  27 | 
  28 | test('POST Order', async ({ request }) => {
  29 |   const res = await request.post('https://simple-books-api.glitch.me/orders', {
  30 |     headers: {
  31 |       Authorization: `Bearer ${token}`
  32 |     },
  33 |     data: {
  34 |       bookId: 1,
  35 |       customerName: 'Venkat'
  36 |     }
  37 |   });
  38 | 
> 39 |   expect(res.status()).toBe(201);
     |                        ^ Error: expect(received).toBe(expected) // Object.is equality
  40 | });
```