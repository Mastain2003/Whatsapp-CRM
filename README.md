# Sanchi Dugdh — Dummy Frontend PWA

Frontend-only prototype for validating the file structure, naming conventions, navigation, login/logout behavior and responsive layout. No backend or real WhatsApp/Meta integration is included.

## Run locally

From this folder run `python -m http.server 8080` and open `http://localhost:8080`. Use localhost/HTTPS for PWA and service-worker behavior; opening via `file://` is not a valid PWA test.

## Demo login

Any non-empty username/password works. Login state uses browser localStorage only and is **not real authentication**. Use Logout on the desktop sidebar or mobile bottom bar. Directly opening a protected page while logged out redirects to the login page.

## Pages and naming

- `public/pages/page_<feature>.html`
- `public/js/page_<feature>.js`
- `public/css/page_<feature>.css`
- Shared components in `public/components/`
- Future APIs: `worker/api_<feature>.js`
- Future migrations: `migrations/NNN_description.sql`

Included pages: Dashboard, Orders, Customers, WhatsApp Inbox, Catalog, Broadcasts, Reminders, Reports, Settings. WhatsApp inbox is a single page (`page_whatsapp.html`).

## Test checklist

1. Sign in from the landing page.
2. Test all desktop sidebar links.
3. At mobile width, test bottom navigation and logout.
4. Search/filter the Orders page; search Customers.
5. Type and send a message in the WhatsApp inbox; it appears locally as “not sent”.
6. Click mock actions and verify they clearly say no backend request was made.
7. Logout; verify login appears. Then try opening a page URL directly and verify redirect to login.
8. Test offline/online indicator and app-shell caching on localhost.

## Mock behavior / limits

All records are static sample data. Forms and actions do not persist to a server. No database, APIs, Meta catalog sync, WhatsApp delivery, email, push notifications or secure authentication exists. Offline caching is for app-shell demonstration only. Before backend work, use `WHATSAPP_CLOUD_API_META_CATALOG_SOURCE_OF_TRUTH_README.md` as the project baseline when available; this demo does not override it.
