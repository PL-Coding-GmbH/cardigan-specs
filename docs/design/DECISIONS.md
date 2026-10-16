# Cardigan — UI decisions (design interview, 2026-10-16)

Source of truth for the mockups in `screens.html`. Anything not listed here is a layout choice made in the mockups, not a product requirement.

## Visual direction
- **Graphite**: cool blue-grey neutrals, one cobalt accent, hairline borders, compact density.
- Type: Geist (UI, headings), Geist Mono (card IDs, counts, metadata).
- Light and dark theme. **No in-app theme setting**: the app always follows the system theme.
- One shared look across web, Android and iOS (no Material/Cupertino-specific UI). One shared device frame in mockups; platform differences are only noted.
- Audience: developers. Tool-like, no "cozy" branding.

## Cards
- Fields: title, description (**plain text, no Markdown**), labels, created time, updated time (read-only).
- Card ID: **board key + number**, e.g. `CRD-109`.
- Create: **inline quick add** (title only) at the bottom of a column.
- Detail: **side panel** on tablet/desktop widths, **full screen** on phones.
- Editing: **explicit Save** button; warn about unsaved changes on close.
- Moving between columns: **drag & drop only** (no column picker).

## Boards
- Board has a name and a **key**: 2–5 uppercase letters, entered by the user at creation (prefilled from name), **not editable afterwards**, **unique per user**.
- New boards start with **default columns**: To do / In progress / Done.
- Board list: **grid of tiles** (list on phone). Each tile shows name, key, card count, last updated time.
- Web navigation on tablet/desktop: **persistent sidebar** (board list page remains the home).
- App navigation mirrors web by size: phone = board list home with a menu (Labels, Log out); tablet = persistent sidebar.

## Board view & columns
- Phone: **horizontal scroll** of columns (next column peeks in).
- Column actions (move left, move right, rename, delete) **all in a … menu**.
- Deleting a column with cards: **confirm dialog that names the card count; cards are deleted too**.
- All deletions (board, column, card, label) use a **confirmation dialog**.

## Labels
- Scope: **per user, shared across all boards**.
- Color: **fixed palette of 20 colors** tuned to the theme.
- Managed on an **own Labels page** (sidebar on wide screens, menu on phones).
- **No inline label creation** in the card's label picker.

## Search & filter (client-side, open board only)
- Text search matches **title, description and card ID**.
- Multiple label filters combine with **OR** (any selected label).

## Auth & account
- Register: **email + password + repeat password**.
- Password rule: **at least 12 characters, with one lowercase letter, one uppercase letter and one digit**.
- **No account/settings screen**; Log out lives in a menu.

## Import / export
- Export: from the **board view … menu** only.
- Web import: **button opening a dialog with a drop zone** (or browse). App import: system file picker.
- Max file size: **5 MB**.
- Key clash on import: **dialog asks for a different key**.
- After import: **stay on the board list**, new board highlighted, toast confirms.

## Mockup scope
- Sizes: web phone (390), web tablet (834), web desktop (1440); app phone, app tablet portrait, app tablet landscape.
- States: loading, empty, error (load failed, validation), dialogs and menus open.
