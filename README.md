# Golf Getaway 2027

Sign-up and voting page for the Jacksonville & St. Augustine golf trip. Anyone with the link can sign up, no account needed. Sign-ups save to Firebase (Firestore, anonymous sign-in).

## Setup

1. In Firebase, use a project (Fairway Ledger's is fine) with **Anonymous** sign-in turned on.
2. Add this to the project's Firestore rules, inside `match /databases/{database}/documents { ... }`:

```
match /golfSignups/{uid} {
  allow read: if true;
  allow write: if request.auth != null && request.auth.uid == uid;
}
```

3. Paste the project's web config into `FIREBASE_CONFIG` near the top of the script in `index.html`.
4. Turn on GitHub Pages (Settings → Pages → main / root).

Sign-ups are tied to the browser they were made in. To remove someone's entry, delete their document in the Firebase console under `golfSignups`.
