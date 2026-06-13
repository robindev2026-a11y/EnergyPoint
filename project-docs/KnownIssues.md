# Known Issues

Known bugs, risks, limitations, and workarounds.

## Active Issues

- **Issue:** All contact details (WhatsApp, address, phone, email) are currently placeholders.
  - **Impact:** Site cannot be used for real lead generation until replaced.
  - **Workaround:** Client must provide real details.
  - **Status:** Awaiting input from client.

- **Issue:** Lead data is only stored in browser localStorage.
  - **Impact:** Leads are lost if user clears browser data or uses a different device/browser.
  - **Workaround:** WhatsApp and email paths deliver the data immediately to the business.
  - **Status:** Acceptable for current phase.

## Risks

- **Risk:** WhatsApp Business API not set up.
  - **Likelihood:** High (we are using wa.me links instead).
  - **Impact:** No fully automatic server-to-WhatsApp push without user action.
  - **Mitigation:** Rich prefilled messages + clear UX in the success panel. Easy to upgrade later.

- **Risk:** Map address and pin are approximate (currently Kochi area).
  - **Likelihood:** Medium until real address given.
  - **Impact:** Visitors may get wrong directions.
  - **Mitigation:** Easy to update coordinates and text in code.

## Other Limitations

- No real images of batteries or the physical Experience Center yet (using stylized CSS visuals).
- Form does not perform server-side validation or spam protection.
- Site is not yet optimized for production SEO or analytics.
