# EventPass EmailJS setup

## Email Template
Create a new EmailJS template. Do NOT use the default Password Reset template.

### Subject
Your EventPass QR Invitation - {{event_name}}

### To Email
{{to_email}}

### From Name
{{owner_name}}

### Reply To
{{owner_email}}

### Content
Copy all HTML from `EMAILJS_TEMPLATE.html` into the template's code editor.

## Attachments
In the template's **Attachments** tab add a **Dynamic / Variable Attachment**:

- Filename: `eventpass-qr.png`
- Content type: `image/png`
- Parameter name: `qr_code`

The website sends `qr_code` as a QR-image URL. The template embeds it with `src="cid:qr_code"`.

## EventPass settings
Enter:

- Public Key: your EmailJS Account public key
- Service ID: your Gmail service ID
- Template ID: the new EventPass template ID

The existing Password Reset template ID should not be used for EventPass.


### WhatsApp delivery note
WhatsApp messages use the `inviteMessage(u)` content. It includes guest number, Guest ID, Entry Code, phone, email, event name/date/venue, and the `qrImageUrl(u)` API link. The link is clickable in WhatsApp and opens the QR image.
