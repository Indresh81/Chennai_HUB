# Chennai Mobile Hub

Chennai Mobile Hub is a responsive mobile-shopping demo with a dependency-free Node.js server. The repository contains the complete storefront, locally stored product images, account registration and sign-in, checkout, and order confirmation flow.

## Features

- Chennai Mobile Hub branding across every page
- Nine-product catalogue using local images in `assets/products/`
- Account registration and sign-in
- Password hashing with Node.js `crypto.scrypt`
- HTTP-only, same-site session cookies
- Product-aware checkout with live quantity totals
- Server-side request validation
- JSON persistence for users and orders
- Order confirmation with a generated order ID
- Responsive, accessible frontend styles
- No third-party runtime dependencies

## Requirements

- Node.js 18 or newer

## Run locally

```bash
npm start
```

Open [http://localhost:3000](http://localhost:3000).

For development with Node's built-in file watcher:

```bash
npm run dev
```

The server binds to `0.0.0.0` by default. Set another host or port with environment variables:

```bash
HOST=0.0.0.0 PORT=4000 npm start
```

## Project structure

```text
.
├── assets/
│   └── products/             # Local catalogue product images
├── app.css                   # Shared responsive styles
├── app.js                    # Frontend session, catalogue, and checkout logic
├── server.js                 # Node.js static server and JSON API
├── index.html                # Sign-in page
├── registration.html         # Account creation page
├── phone.html                # Product catalogue
├── Booking.html              # Checkout page
├── finalpage.html            # Order confirmation page
├── package.json              # npm scripts and Node.js requirement
└── README.md
```

Compatibility redirect pages are also included for the project's earlier filenames: `registeration form.html`, `products.html`, `checkout.html`, and `confirmation.html`.

## Main pages

| Route | Purpose |
| --- | --- |
| `/` or `/index.html` | Sign in |
| `/registration.html` | Create an account |
| `/phone.html` | Browse products |
| `/Booking.html?product=...` | Complete checkout |
| `/finalpage.html?order=...` | View an order confirmation |

## API routes

| Method | Route | Purpose |
| --- | --- | --- |
| `GET` | `/api/products` | Return the product catalogue |
| `GET` | `/api/session` | Return the current signed-in user |
| `POST` | `/api/register` | Create an account and session |
| `POST` | `/api/login` | Sign in |
| `POST` | `/api/logout` | Sign out |
| `POST` | `/api/orders` | Validate and create an order |
| `GET` | `/api/orders/:id` | Return an order belonging to the current user |

## Data and security notes

- Runtime data is saved to `.data/db.json`; `.data/` is ignored by Git.
- Sessions are held in memory and expire after seven days. Restarting the server signs users out.
- Passwords are stored only as a scrypt hash and unique salt.
- The server sets content-security, frame, referrer, and content-type headers.
- This is a demo. A production deployment should use HTTPS, a managed database and session store, email verification, rate limiting, backups, structured logging, and a payment provider.

## Checks

```bash
npm run check
```

This validates the syntax of the server and browser JavaScript.
