OK MOBILITY CAR RENTALS & HIRE — Web app + admin portal
========================================================

WHAT THIS IS
------------
A single web app that works as:
  • A public website where customers browse cars and book/hire online.
  • An admin portal to add/remove cars, set prices, manage bookings,
    view customers, see reports, and manage user accounts.
It is a PWA (Progressive Web App), so on a phone it can be installed to the
home screen and used "like an app / APK".


FILES
-----
  index.html                 The whole app (site + portal).
  manifest.json              Makes it installable as an app.
  sw.js                      Service worker (offline + install support).
  icon-192.png / icon-512.png / icon-512-maskable.png / apple-touch-icon.png / favicon.png
  README.txt                 This file.

Keep all files together in one folder.


DEPLOY TO NETLIFY (easiest way)
-------------------------------
1. Go to https://app.netlify.com  and sign in.
2. Click "Add new site" -> "Deploy manually".
3. Drag the WHOLE folder (all files above) into the upload box.
4. Netlify gives you a live https link, e.g. https://ok-mobility.netlify.app
   Share that link with customers. HTTPS is required for install to work.

To update later: change the files, then drag the folder in again
(or connect a GitHub repo for automatic deploys).


THE FLEET & CAR PHOTOS
----------------------
The app comes pre-loaded with common Kenyan self-drive cars (Vitz, Axio,
Fielder, Noah, X-Trail, Harrier, CX-5, Forester, Prado, Land Cruiser V8,
Hilux, Hiace) at sample KES prices. Change any price under
Admin -> Fleet & prices -> Edit.

Photos: each car now shows a REAL photo from Unsplash (free for commercial
use, no attribution required). Important points, stated plainly:
  1. The photos are matched by BODY TYPE, not the exact model — e.g. a real
     wagon for the Fielder, a real minivan for the Noah, a Mazda SUV for the
     CX-5. They are representative, not the specific car you own.
  2. They load from the internet, so the site needs a connection to show them.
     If a photo ever fails to load, the built-in car illustration shows instead.
  3. I could not guarantee every photo is free of a number plate — I can't see
     the images. Open any car (Admin -> Fleet & prices -> Edit) to check, and
     tap "Upload photo" to replace it with your own plate-free shot.

Best practice for a real business: replace these with photos of your OWN cars
(front 3/4 angle hides the plate). Upload takes one tap and auto-resizes.

If you already opened an OLDER version: the new photos are added automatically
the next time you open the app (your own uploaded photos are never overwritten).
To reload the full updated fleet from scratch instead, use
Admin -> Settings -> "Reset everything" (this clears cars/bookings you added).


ADMIN LOGIN (Firebase version)
------------------------------
There is no fixed default password anymore. Sign-in uses Firebase
Authentication (email + password). To become the admin:
  1. Do the one-time setup in FIREBASE-SETUP.txt.
  2. Register your owner account on the site (email + password).
  3. In the Firebase console, set your user's "role" to "admin"
     (exact steps in FIREBASE-SETUP.txt, step 4c).
Add more admins later under Admin -> Users -> "Make admin".


HOW CUSTOMERS USE IT
--------------------
  • Open the link, browse the fleet, tap "Book this car".
  • Fill name, phone, dates, etc. and either "Confirm booking"
    (saved to the shared database for the admin) or "Send booking via
    WhatsApp" (also saves, and opens WhatsApp to the owner's number).
  • They can optionally create an account to track their own bookings.


HOW THE ADMIN MANAGES EVERYTHING
--------------------------------
Sign in as admin, then use the tabs:
  Fleet & prices  Add / edit / hide / delete cars and set daily prices.
  Bookings        Change status (pending/confirmed/completed/cancelled),
                  view details, WhatsApp the customer, delete, export CSV.
  Customers       All customers with booking counts and totals.
  Reports         Revenue, pending requests, revenue-by-car, CSV export.
  Users           Promote to admin, send password-reset emails, remove access.
  Settings        Business name, phone, WhatsApp number, location;
                  plus download a JSON snapshot / bookings CSV.


HOW DATA IS STORED (Firebase)
-----------------------------
All data (cars, bookings, accounts) lives in ONE shared cloud database
(Firestore). A booking made on a customer's phone appears in your admin on
any device, in real time. This fixes the old per-device limitation.

Notes:
  • The site now needs an internet connection.
  • The firebaseConfig in index.html is NOT secret — it only identifies the
    project. Protection comes from the Firestore security rules
    (firestore.rules), which you paste in during setup.
  • Full setup instructions: see FIREBASE-SETUP.txt.


SUPPORT / OWNER
---------------
  OK Mobility Car Rentals & Hire
  Phone / WhatsApp: 0726049772
  Kenya
