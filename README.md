# TAPANCSC Website

A responsive, static website for **TAPANCSC — Digital Service Center**. It is built with plain HTML, CSS and JavaScript and does not require a framework, database or build tool.

## Files

- `index.html` — website structure, metadata and content
- `styles.css` — responsive styling and visual design
- `script.js` — searchable/filterable services, detailed service records, local admin password flow, add/edit/delete controls, browser storage, backup import/export, service dialog, mobile menu, FAQs and enquiry form behavior

## Preview locally

1. Extract the ZIP file (if you received the ZIP).
2. Open the `TAPANCSC-Website` folder.
3. Double-click `index.html` to open it in a browser.
4. For a better developer preview, open the folder in VS Code and use the Live Server extension.

## Important: configure contact details before publishing

Open `script.js` and edit the configuration at the top:

```js
const TAPANCSC_CONFIG = {
  phone: "",       // Example: +919876543210
  whatsapp: "",    // Digits only, including country code: 919876543210
  email: ""        // Your public enquiry email
};
```

Use your real contact information only. If WhatsApp is configured, the form prepares an enquiry in WhatsApp. Otherwise, if an email is configured, it opens an email draft. If neither is configured, the form attempts to copy the enquiry text and explains what is missing. The form is not connected to a server and does not save enquiries to a database.

## Admin panel: edit services and prices

1. Open the website and click **Admin** in the top navigation or **Admin login** in the footer.
2. On first use in that browser, create an admin password of at least 8 characters and confirm it. On later visits, enter that password to unlock the panel.
3. Use the editor to add or edit a service, including the card title, category, short label, icon, description, displayed price, TAPANCSC assistance charge details, official/portal fee details, document checklist, process steps, estimated time, notes, and official link.
4. Use **Delete** to remove a service. Changes update the public service cards immediately in this browser.
5. Click **Export backup** regularly to download a JSON backup. Use **Import backup** to restore a backup or copy service data into another browser.
6. Use **Change password** to set a new admin password and **Lock** to return to the password screen.

### Important admin limitations

This project is a static HTML/CSS/JavaScript site. The admin password hash and service edits are saved in the **current browser's local storage only**. They do not update the hosted website's files or automatically appear for visitors on other devices. Each browser/device has its own service copy unless a backup is exported and imported.

The password screen is a convenience barrier, **not production-grade server authentication**. A technically capable visitor can inspect or modify client-side code/storage. Do not use this local-only mode to protect sensitive information or to operate a public shared admin dashboard. To securely update the live public site for all visitors, connect the website to a backend such as Supabase with server-side authentication and database access rules (RLS), or another trusted server. The site currently has no such backend configured.

If you forget the local admin password, open the browser's developer console on the same website origin and run `localStorage.removeItem('tapancsc_admin_password_hash_v1'); location.reload();` to create a new password. This does not remove saved service edits, but export a backup first as a precaution.

## Edit the address or service list

- Find the contact address in `index.html` and update it if needed.
- The default service records live in `script.js`; you can also edit them through Admin instead of changing code.
- Every `priceTag`/`centerFee` entry is a sample or guidance unless it specifically describes an official tariff. Replace suggested shop prices with your actual approved rates before publishing. Do not label sample prices as government fees.
- Official references used in the guide include UIDAI (Aadhaar), Income Tax Department (PAN), and Odisha e-District (certificates). Re-check live pages before publishing because fee schedules and document requirements can change.
- The website deliberately does not include product listings or a shopping cart.

## Publish

You can upload these static files to Netlify, GitHub Pages, Cloudflare Pages or another static host. Upload `index.html`, `styles.css` and `script.js` together, keeping their filenames and folder relationship intact.

## Notes

- Service descriptions and checklists are general examples. Confirm the current official requirements, fees and center authorization before offering a listed service.
- The website does not claim government affiliation, guaranteed approvals or a live connection to government portals.
- Never collect or ask a visitor to submit passwords, OTPs, PINs or payment credentials through this form.
