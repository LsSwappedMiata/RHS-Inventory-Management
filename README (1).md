# RHS Inventory Management

Truck inventory for Reynolds Home Services. Plain HTML, CSS and JavaScript on Firebase
(Authentication, Firestore, Hosting). Project: `rhs-inventory-management-360b7`.

## One-time setup (Firebase console)

1. **Authentication** > Sign-in method > turn on **Email/Password**.
2. **Authentication** > Users > **Add user** for each person (email and a temporary password).
3. **Firestore Database** > start a collection named `staff`. Add one document per person.
   The **document ID is that person's User UID** (copy it from the Users table). Add any field,
   for example `name` = `Mike`. Only people with a staff document can read or change anything.
   A new person who signs in before they are listed sees a screen with their ID to send to you.
4. **Firestore Database** > Rules > paste in `firestore.rules` > Publish.
   (Or deploy it with the command below.)
5. **Authentication** > Settings > Authorized domains. The two Hosting addresses
   (`...web.app` and `...firebaseapp.com`) are already there. Add a custom domain here if you use one.

## Deploy

Install Node.js once, then from this folder:

    npm install -g firebase-tools
    firebase login
    firebase deploy

That publishes the site to Hosting and the rules to Firestore.
The app will be at https://rhs-inventory-management-360b7.web.app

## Day to day

- **Add a tech:** add the user in Authentication, have them sign in once, then add their
  UID to `staff` (they will see the UID on screen).
- **Remove a tech:** delete their `staff` document. They are locked out right away.
  Disable the user in Authentication too.
- **Move old data in:** in the old version, open a truck > Import / export > Export stock.
  In this version, add the truck, open it, then Import / export > Choose CSV.
  Truck photos are not in the CSV, so add those again in Truck settings.

## Files

- `index.html`, `style.css`, the logo: the app.
- `firestore.rules`: who can read and write.
- `firebase.json`, `.firebaserc`: Hosting and rules deploy settings.
