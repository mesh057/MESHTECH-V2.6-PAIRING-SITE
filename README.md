# MESHTECH-V2.6-PAIRING-SITE

Standalone pairing interface for the MESH-TECH MD BOT.

## Configure the bot backend

Before deploying, edit [`config.js`](./config.js) and replace the placeholder with the public URL of the running bot backend. Do not add a trailing slash.

```js
const BOT_API_URL = 'https://your-bot-backend.example.com';
```

The backend must have this Vercel site's exact origin in its environment variables:

```env
PAIRING_SITE_ORIGIN=https://your-project.vercel.app
```

If you later attach a custom domain, allow both origins separated by a comma.

## Deploy on Vercel

1. Import this GitHub repository into Vercel.
2. Select **Other** as the framework preset.
3. Leave the build command and output directory empty.
4. Deploy the project.
5. Copy the generated `vercel.app` URL into the backend's `PAIRING_SITE_ORIGIN` variable.
6. Restart or redeploy the backend.

This is a static site, so Vercel does not need to run Node.js or install dependencies.

## Pairing API used by the interface

The page calls the backend at:

- `GET /api/status`
- `POST /api/request-pairing`
- `GET /api/pairing-code?phoneNumber=<number>`
- `POST /api/request-qr`
- `GET /api/qr-code?phoneNumber=<number>`

Enter the WhatsApp number with its country code and no `+`, spaces, or punctuation.
