# AURA CAFE — Full-stack restaurant ordering

Traditional Indian cafe website built with React + Vite, Express/Node.js and MongoDB.

## Features
- Responsive traditional Indian cafe menu with categories and prices
- Cart and table-number ordering (QR codes can point to `/?table=05`)
- Server-side order totals and Razorpay checkout/signature verification
- Admin sign-in, order status management and menu item creation
- Customer reviews and ratings
- Helmet, rate limiting, input validation and JWT-protected admin routes

## Run locally
1. Install Node.js 18+ and MongoDB (or create a MongoDB Atlas database).
2. From the project root run `npm install`.
3. Run `npm install --prefix server`.
4. Copy `server/.env.example` to `server/.env` and fill in your MongoDB URI, a long random JWT secret, and admin credentials.
5. In one terminal run `npm run server`.
6. In another terminal run `npm run dev` and open the Vite URL.

## Payment setup
Create a Razorpay account and use **test mode** keys first. Add the test Key ID and Key Secret to `server/.env`; set `VITE_RAZORPAY_KEY_ID` in a root `.env` file. Never put the Razorpay secret in frontend code. Test a payment before enabling live mode. Live payments require the restaurant owner's verified merchant account and applicable compliance checks.

## Deploy
- MongoDB: MongoDB Atlas
- API: Render, Railway or another Node.js host. Set all variables from `server/.env.example`.
- Frontend: Vercel or Netlify. Set `VITE_API_URL` to the deployed API base URL ending in `/api`, and `VITE_RAZORPAY_KEY_ID` to the public Razorpay Key ID.
- Set `CLIENT_ORIGIN` on the API to the deployed frontend origin.
- Deploy frontend and backend separately; GitHub Pages cannot run the Node.js API.

## Important before going live
This is a starter implementation, not a finished production payment/restaurant operation system. Add HTTPS, verified Razorpay webhooks, delivery zones/tax configuration, stock handling, staff roles, backups, monitoring, privacy/terms pages and owner-approved business details. Use a strong unique admin password and keep all secrets out of Git.
