# Scheduly

A mobile-friendly, self-contained booking calendar with email notifications.  
No build tools. No server. One HTML file.

---

## 🚀 Deploy to GitHub Pages

1. Go to [github.com/new](https://github.com/new) → create a **public** repo named `scheduly`
2. Upload `index.html` to the repo
3. Go to **Settings → Pages → Branch: main → Save**
4. Your URL: `https://yourusername.github.io/scheduly`

---

## ✉️ Set Up Email Notifications (free)

When someone books, you'll get an email to your inbox. Uses **EmailJS** (free for 200 emails/month).

### Step 1 — Create EmailJS account
Go to [emailjs.com](https://www.emailjs.com) → Sign up free

### Step 2 — Add an Email Service
- Dashboard → **Email Services** → Add Service
- Choose Gmail (or any provider) and connect your account
- Copy the **Service ID** (e.g. `service_abc123`)

### Step 3 — Create an Email Template
- Dashboard → **Email Templates** → Create New Template
- Set **To Email** to: `{{to_email}}`
- Paste this as the template body:

```
New booking on {{app_title}}!

Name:  {{booker_name}}
Email: {{booker_email}}
Date:  {{booking_date}}
Time:  {{booking_time}}
Note:  {{booking_note}}
```

- Save and copy the **Template ID** (e.g. `template_xyz789`)

### Step 4 — Get your Public Key
- Dashboard → **Account** → **API Keys**
- Copy your **Public Key**

### Step 5 — Update index.html
Open `index.html` in a text editor and fill in the config section at the top:

```js
const ADMIN_PASSWORD    = "your-secure-password";
const APP_TITLE         = "Your Name";
const ORGANIZER_EMAIL   = "you@gmail.com";       // ← your inbox

const EMAILJS_PUBLIC_KEY  = "abc123...";          // ← from Step 4
const EMAILJS_SERVICE_ID  = "service_abc123";     // ← from Step 2
const EMAILJS_TEMPLATE_ID = "template_xyz789";    // ← from Step 3
```

Save and re-upload to GitHub. Done!

---

## 🔗 Embed on a Website

```html
<iframe
  src="https://yourusername.github.io/scheduly"
  width="100%"
  height="700px"
  style="border:none; border-radius:12px;"
  title="Book a time"
></iframe>
```

Works in Squarespace, Wix, Webflow, WordPress (Custom HTML block), and any website that allows iframes.

---

## ⚙️ Customise Time Slots

Open `index.html`, find the `TIME_SLOTS` array and edit:

```js
const TIME_SLOTS = ["9:00 AM","10:00 AM","11:00 AM","2:00 PM","3:00 PM","4:00 PM"];
```

---

## 💾 Storage

Bookings are saved to `localStorage` in the browser where the admin panel is accessed.  
They persist across refreshes on the same device and browser.

---

## 📁 Files

```
scheduly/
├── index.html   ← everything is here
└── README.md
```
