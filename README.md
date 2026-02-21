# Nodemailer API for Vercel

This is a simple Node.js API built with Express and Nodemailer, designed to be deployed on Vercel and used as a microservice for sending emails.

## Features

- **Express.js**: Fast and minimalist web framework.
- **Nodemailer**: Easy email sending for Node.js.
- **CORS Enabled**: Can be called from any frontend project.
- **Vercel Ready**: Pre-configured for deployment as Serverless Functions.

## Setup

1. **Install Dependencies**:
   ```bash
   npm install
   ```

2. **Environment Variables**:
   Create a `.env` file in the root directory (use `.env.example` as a template):
   - `EMAIL_SERVICE`: The email service you're using (e.g., `gmail`, `outlook`).
   - `EMAIL_USER`: your full email address.
   - `EMAIL_PASS`: your email password or [App-specific password](https://support.google.com/accounts/answer/185833?hl=en) (highly recommended for Gmail).

## Local Development

Run the API locally:
```bash
npm run dev
```
The API will be available at `http://localhost:3000`.

## API Endpoints

### POST `/api/send-email`

Sends an email using the configured SMTP settings.

**Request Body**:
```json
{
  "to": "recipient@example.com",
  "subject": "Hello from Nodemailer",
  "text": "This is a plain text body",
  "html": "<h1>This is an HTML body</h1>"
}
```

**Success Response**:
- Status: `200 OK`
- Body: `{ "message": "Email sent successfully", "info": "..." }`

## Deployment to Vercel

1. Install the Vercel CLI: `npm i -g vercel`
2. Run `vercel` in the project root.
3. Follow the prompts to deploy.
4. Add your environment variables (`EMAIL_USER`, `EMAIL_PASS`) in the Vercel Dashboard under **Settings > Environment Variables**.

## Usage in Another Project

You can call this API from your frontend or another backend:

```javascript
fetch('https://your-vercel-app.vercel.app/api/send-email', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    to: 'user@example.com',
    subject: 'Welcome!',
    text: 'Thanks for joining our platform.',
  }),
})
.then(res => res.json())
.then(data => console.log(data));
```
