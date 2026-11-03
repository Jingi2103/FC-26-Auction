# FC 26 Player Auction — GitHub Pages + Firebase

This version stores the auction in a shared Firebase Firestore document. Visitors can view the live board. Only **jin.mj301@gmail.com** can sign in as admin and add/edit/delete/import players or operate the auction. Firebase security rules enforce this on the server; hiding buttons in the page is not the security boundary.

## Files
- `index.html` — website
- `firestore.rules` — database permissions; publish these exactly

## Setup (one-time)

### 1. Create a Firebase project
1. Open https://console.firebase.google.com/ and choose **Create a project**. Name it `fc26-player-auction` (or any name).
2. In **Build → Firestore Database**, click **Create database**. Choose production mode and a region close to India (for example asia-south1 if offered).
3. Open **Build → Authentication → Get started → Sign-in method**. Enable **Email/Password**.
4. In **Authentication → Users → Add user**, create exactly this admin account: `jin.mj301@gmail.com`. Set a password yourself and keep it private. Do not put the password in GitHub or send it to anyone.
5. In **Project settings → General → Your apps**, click the Web `</>` icon, register an app, and copy the `firebaseConfig` values. You do not need Firebase Hosting.

### 2. Add Firebase config to the website
1. Open `index.html` in a text editor (Notepad is fine).
2. Find `const firebaseConfig = {` near the top of the scripts.
3. Replace each `PASTE_...` value with the matching value from Firebase. Keep the quotes and commas. Example shape:

```js
const firebaseConfig = {
  apiKey: "your-api-key",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

These web config values identify your Firebase project; they are not admin passwords. Security is enforced by Firestore rules.

### 3. Publish the Firestore rules
1. In Firebase Console, open **Firestore Database → Rules**.
2. Replace the rules with the full contents of `firestore.rules`.
3. Click **Publish**.
4. Do not leave Firestore in test mode. The supplied rules make the auction board readable to visitors but writable only by the admin account above.

### 4. Deploy on GitHub Pages
1. Create a GitHub repository, e.g. `fc26-player-auction`.
2. Upload `index.html` and `firestore.rules` to the repository root.
3. In GitHub, open **Settings → Pages**. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
4. Wait for the Pages URL to appear.
5. In Firebase Console → **Authentication → Settings → Authorized domains**, add your GitHub Pages hostname (for example `yourusername.github.io`, without `https://` or a path).

### 5. First use
1. Open your GitHub Pages website. The board will show the initial team setup once you sign in for the first time.
2. Click **Admin login** and sign in as `jin.mj301@gmail.com` using the password you created in Firebase.
3. Import your Excel/CSV player list or add players manually. The first admin login creates the shared auction record and seeds the five teams/purses.
4. Share the GitHub Pages link with the managers. They can view the same live board, but cannot edit players, teams, purses or auction results. They can call out bids in person; the admin records the winning bid in the console.

## Important notes
- Keep your Firebase password private. Never commit passwords, service-account keys, or private keys to GitHub.
- The Firebase web config is expected to be visible in a public website. The Firestore rules—not secrecy of that config—protect writes.
- Only the administrator can operate the auction in this version. Managers have read-only access. This prevents unauthorised changes and conflicting edits.
- Download a JSON backup before the auction and after major rounds.
- Excel import uses a SheetJS CDN, so the browser needs internet access for `.xlsx`; CSV import is also supported.
- If you rename the admin email, update it in both `index.html` and `firestore.rules`, then publish the rules again.
