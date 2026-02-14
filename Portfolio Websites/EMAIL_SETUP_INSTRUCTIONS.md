# Email Setup Guide - EmailJS Integration

Aapke portfolio mein email functionality add kar di gayi hai! Ab sirf ye 3 simple steps follow karte ho:

## Step 1: EmailJS Account Banao (FREE)
1. [emailjs.com](https://www.emailjs.com/) pe jao
2. **Sign Up** karo (Google/GitHub se bhi kar sakte ho)
3. Email verify kro

## Step 2: Email Service Connect Karo
1. Dashboard mein **Add Service** click karo
2. **Gmail** select karo
3. Aapka Gmail account connect karo (ek popup aayega, allow karo)
4. Service ID copy karo (kuch iss tarah: `gmail_xxxxx`)

## Step 3: Email Template Banao
1. **Email Templates** section mein jao
2. **Create New Template** click karo
3. Ye details fill karo:

### Template Details:
```
Template Name: Contact Form
Service: Gmail (jo abhi add kiya)

TO_EMAIL: {{to_email}}
SUBJECT: New Message from {{user_name}}

EMAIL BODY (Body part mein):
---
Name: {{user_name}}
Email: {{user_email}}
Message: {{message}}
---
```

4. Template ID copy karo (kuch iss tarah: `template_xxxxx`)

## Step 4: Index.html Update Karo
Aapke `index.html` file mein lines 694 aur 696 ko update karo:

```javascript
emailjs.init('YOUR_PUBLIC_KEY');  // Line 694
// Replace YOUR_PUBLIC_KEY with your actual public key

await emailjs.sendForm(
    'YOUR_SERVICE_ID',      // Replace with your Service ID - Line 699
    'YOUR_TEMPLATE_ID',     // Replace with your Template ID - Line 700
    this
);
```

### Kaun si keys/IDs kahan se milti hain:

1. **YOUR_PUBLIC_KEY**: 
   - EmailJS Dashboard > Account tab > Public Key

2. **YOUR_SERVICE_ID**: 
   - EmailJS Dashboard > Email Services > Gmail service ka ID

3. **YOUR_TEMPLATE_ID**: 
   - EmailJS Dashboard > Email Templates > Jo template banaya usका ID

## Done! ✓
Ab form submit karke test kro. Message directly aapke email par aa jaayega!

---

### Troubleshooting:

❌ **"Error sending message"?**
- Public Key, Service ID, Template ID sahi copy kiye ho?
- Gmail account EmailJS ko allow kiya ho?

❌ **Email nahi aa raha?**
- Spam folder check kro
- Gmail security settings check kro (Less secure apps may be disabled)

✓ **Sab theek hai?**
- Congratulations! 🎉 Aapka contact form fully functional hai!

---

### Pricing:
- **Free Plan**: 200 emails/month ✓ (Portfolio ke liye kaafi hai)
- Baad mein upgrade kar sakte ho agar zyada emails chaiye

Kisi aur help ke liye mujhe puchhna! 😊
