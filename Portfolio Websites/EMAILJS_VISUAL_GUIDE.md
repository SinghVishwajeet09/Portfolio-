# EmailJS Setup - Step-by-Step Visual Guide

## 🎯 Complete Setup Process

### STEP 1: Account Setup (2 minutes)
```
Visit: https://www.emailjs.com/
Click: Sign Up → Free Account
Verify: Email verification complete
```

### STEP 2: Get Your Public Key (1 minute)
```
Dashboard → Account (top right menu)
Copy: Public Key
Example: "abcd1234efgh5678ijkl"
```

### STEP 3: Add Gmail Service (2 minutes)
```
Left Menu → Email Services → Create New Service
Select: Gmail
Click: Connect Account
Browser Popup: Allow EmailJS access
Copy: Service ID (Example: "gmail_123abc")
```

### STEP 4: Create Email Template (3 minutes)

Go to: **Email Templates** → Create New Template

Fill these fields exactly:

**Template Setup:**
| Field | Value |
|-------|-------|
| Template Name | Contact Form |
| Service | Gmail (jo abhi add kiya) |

**TO_EMAIL variable:** (Subject line mein)
```
TO_EMAIL: {{to_email}}
```

**SUBJECT:** (Subject line)
```
New Message from {{user_name}}
```

**Content (Body - Text tab):**
```
Hello,

You have received a new message from your portfolio contact form.

---
Name: {{user_name}}
Email: {{user_email}}

Message:
{{message}}

---

Best regards,
Your Portfolio Website
```

**Copy Template ID** (Example: `template_abc123xyz`)

---

### STEP 5: Update Your Code (2 minutes)

Open: `index.html`
Find: Line 694 - 700

Replace these 3 values:

```javascript
// Line 694
emailjs.init('YOUR_PUBLIC_KEY'); 
// ↓ Replace with actual public key
emailjs.init('abcd1234efgh5678ijkl');

// Line 699
'YOUR_SERVICE_ID',  
// ↓ Replace with actual service ID
'gmail_123abc',

// Line 700
'YOUR_TEMPLATE_ID', 
// ↓ Replace with actual template ID
'template_abc123xyz',
```

---

## ✅ Testing Your Form

1. Open portfolio in browser
2. Go to "Contact Me" section
3. Fill the form:
   - Name: Your name
   - Email: Your email
   - Message: Test message
4. Click: "Send Message"
5. Check: Your email inbox ✓

---

## 📊 What Happens After Submission

```
User fills form
       ↓
Clicks "Send Message"
       ↓
JavaScript sends to EmailJS
       ↓
EmailJS forwards to your Gmail
       ↓
Email appears in your inbox
       ↓
Success message shows on website
```

---

## 🔧 Important Notes

✓ **Gmail Account Required**: Use your personal Gmail
✓ **First Email**: May take 30 seconds (cache building)
✓ **Monthly Limit**: 200 free emails (plenty for portfolio)
✓ **Cost**: Forever free for this usage level
✓ **Security**: EmailJS handles everything securely

---

## ⚠️ Common Issues & Fixes

### Issue 1: "Cannot read property 'init'"
**Solution**: Make sure EmailJS script is loaded (line 13-14)
```html
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/index.min.js"></script>
```

### Issue 2: "Error sending message"
**Check**:
1. Public Key copied correctly?
2. Service ID copied correctly?
3. Template ID copied correctly?
4. Gmail account connected to EmailJS?

### Issue 3: Email not arriving
**Check**:
1. Spam/Promotions folder in Gmail
2. Check: gmail.com account settings (allow less secure apps if disabled)
3. Wait 1 minute (sometimes takes time)

### Issue 4: Form variables not showing in email
**Fix**: Make sure template has correct variable names:
- `{{user_name}}` (not {{name}})
- `{{user_email}}` (not {{email}})
- `{{message}}` (exactly this)

---

## 🎓 Optional: Advanced Setup

### Receive Emails to Different Address
Change in template:
```
TO_EMAIL: your-email@gmail.com
(instead of {{to_email}})
```

### Custom Email Styling
In template Content area, use HTML:
```html
<h2>New Contact Form Submission</h2>
<p><strong>From:</strong> {{user_name}}</p>
<p><strong>Email:</strong> {{user_email}}</p>
<p><strong>Message:</strong></p>
<p>{{message}}</p>
```

---

## 📞 Support
- EmailJS Docs: https://www.emailjs.com/docs/
- Common Issues: https://www.emailjs.com/docs/faqs/

---

**Status**: Ready to use! 🚀
