# FC 26 Player Auction — GitHub Pages (No Firebase)

This is the simple, no-backend edition of the FC 26 auction website.

## Files
- `index.html` — complete website

## Before uploading to GitHub
1. Open `index.html` in Notepad or another text editor.
2. Search for `const ADMIN_PASSWORD =`.
3. Replace `CHANGE-THIS-PASSWORD` with a password you choose.
4. Save the file.
5. Upload `index.html` to the root of your GitHub repository.

**Important security limitation:** this password only hides the admin controls in the browser interface. Because GitHub Pages is a static public website, the password is included in the page's public source code and can be discovered by someone who knows how to inspect it. This does not provide real authentication or secure server-side permissions. Do not use this version for confidential data or if you need tamper-proof admin-only access.

## Publish with GitHub Pages
1. Create a repository on GitHub (for example, `fc26-player-auction`).
2. Upload `index.html` to the repository's top/root level.
3. Open the repository's **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then click **Save**.
6. Wait for GitHub Pages to publish your site. Open the URL shown there.

## How to use
### Admin (you)
1. Open the website and click **Admin login**.
2. Enter the password you set in `index.html`.
3. Add players, import a CSV/Excel list, draw players, record SOLD/UNSOLD results, and undo the last result.
4. Use **Export auction snapshot** regularly to download a JSON backup.

### Managers
1. Open the website.
2. They can view the player pool, teams, and auction history.
3. To see your latest data on their own devices, send them the latest JSON snapshot you exported. They click **Load shared snapshot** on the dashboard and select that file.
4. Managers remain in read-only mode in the interface.

## Data and sharing limitations
- Auction data is saved in the browser's local storage on the device where the admin operates the auction.
- It does **not** sync automatically between different devices or browsers.
- Managers need a fresh JSON snapshot from the admin to see updated data on their own devices.
- If you clear browser data or switch devices, restore your latest JSON snapshot.
- The Excel import feature uses the SheetJS CDN and needs an internet connection for `.xlsx`; CSV import is built in.
- The password lock is a convenience only, not a secure access-control system. Anyone can bypass front-end restrictions or modify their own browser copy.

## Default auction setup
- Team 1: 2295 points, 3 retained
- Team 2: 1990 points, 3 retained
- Team 3: 1968 points, 3 retained
- Team 4: 1978 points, 3 retained
- New Team: 3000 points, 0 retained
- Squad minimum: 18; maximum: 20
- Tier starting prices: A 100, B 75, C 50, D 30, E 18
