# EmailJS Setup Instructions

To make the contact form work, you need to set up EmailJS (free service for sending emails from client-side JavaScript).

## Step 1: Create EmailJS Account

1. Go to https://www.emailjs.com/
2. Sign up for a free account (allows 200 emails/month)
3. Verify your email address

## Step 2: Create Email Service

1. In EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the connection steps
5. Copy your **Service ID** (you'll need this)

## Step 3: Create Email Template

1. Go to **Email Templates** in EmailJS dashboard
2. Click **Create New Template**
3. Use this template structure:

**Template Name:** Contact Form

**Subject:** New Contact Form Message: {{subject}}

**To Email:** noeljoseph419@gmail.com (set this in the template settings)

**Content:**
```
From: {{from_name}}
Email: {{from_email}}
Reply To: {{reply_to}}
Subject: {{subject}}

Message:
{{message}}

---
This message was sent from your portfolio contact form.
```

**Important:** In the EmailJS template settings, set the "To Email" field to: `noeljoseph419@gmail.com`

4. Save the template and copy your **Template ID**

## Step 4: Get Public Key

1. Go to **Account** → **General**
2. Copy your **Public Key**

## Step 5: Update script.js

Open `script.js` and replace these placeholders:

1. Replace `YOUR_PUBLIC_KEY` with your EmailJS Public Key (line ~87)
2. Replace `YOUR_SERVICE_ID` with your Service ID (line ~108)
3. Replace `YOUR_TEMPLATE_ID` with your Template ID (line ~109)

Example:
```javascript
emailjs.init("abc123xyz"); // Your Public Key

// ...

const response = await emailjs.send(
    'service_abc123',  // Your Service ID
    'template_xyz789', // Your Template ID
    // ...
);
```

## Step 6: Test

1. Open your website
2. Fill out the contact form
3. Submit and check your email inbox

## Troubleshooting

- **"Failed to send"**: Check that all IDs are correct
- **Email not received**: Check spam folder, verify EmailJS service connection
- **CORS errors**: Make sure you're using the correct Public Key

## Alternative: Use Formspree

If you prefer, you can use Formspree instead:
1. Go to https://formspree.io/
2. Sign up and create a form
3. Get your form endpoint
4. Update the form action in `index.html` to use Formspree endpoint

