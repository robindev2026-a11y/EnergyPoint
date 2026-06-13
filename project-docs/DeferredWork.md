# Deferred Work

Postponed work, technical debt, and future cleanup.

## Deferred Items

- Item: Add real product photography and possibly a "Gallery" section.
  - Reason deferred: No assets provided yet by client.
  - Risk: Low (current stylized visuals are strong).
  - Suggested timing: As soon as client supplies images.

- Item: Create a small README or quick-start guide for the client inside the project root.
  - Reason deferred: Current focus is on building the interactive experience.
  - Risk: Low.
  - Suggested timing: Before final handoff.

## Refactoring Opportunities

- Area: Form submission and lead formatting logic (form.html).
  - Problem: The WhatsApp message construction is duplicated in a few places (main submit + re-open from history).
  - Suggested improvement: Extract a `formatLeadForWhatsApp(lead)` helper function.

- Area: Interactive battery visuals.
  - Problem: Some visual state is managed via inline styles and multiple DOM updates.
  - Suggested improvement: Centralize battery state in a small JS object or data attributes for easier maintenance.

- Area: Map initialization.
  - Problem: Coordinates and address are hardcoded in JS + HTML.
  - Suggested improvement: Move to a small config object at the top of the script for easy updates.
