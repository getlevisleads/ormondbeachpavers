# Ormond Beach Pavers

Static referral site for ormondbeachpavers.com. Plain HTML, no build step, hosted on Cloudflare Pages.

## Cloudflare setup

1. Pages: connect this repo, framework preset "None", build command empty, output directory `/`.
2. D1: create a database `ormond-pavers-leads`, run `schema.sql` in its console, and bind it to the Pages project as `DB`.
3. Variables (Production): `RESEND_API_KEY` (secret), `LEAD_TO`, `LEAD_FROM` (e.g. `Ormond Beach Pavers <leads@ormondbeachpavers.com>`).
4. Custom domain: add ormondbeachpavers.com and www.

The form posts to `functions/api/lead.js`, which saves each lead to D1 and emails it through Resend.

Taps on Call and Text buttons are logged to the `clicks` table by `functions/api/click.js` (created automatically on first tap).
