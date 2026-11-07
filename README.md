# Total Coaching

A website for running a high school baseball program: roster (varsity and JV), schedule, depth chart, practice plans, alumni and fundraising.

It's a single page (`index.html`) hosted on GitHub Pages. Team data is stored in a free Firebase database, and coaches sign in with Google. Only the email addresses on the staff list can see or change anything.

## One-time setup

### 1. Create the Firebase project (free Spark plan)

1. Go to <https://console.firebase.google.com> and click **Create a project**. Name it something like `total-coaching`. You can turn off Google Analytics.
2. On the project home page, click the **Web** icon (`</>`) to add a web app. Name it `Total Coaching`. You don't need Firebase Hosting.
3. Firebase shows a `firebaseConfig` block. Copy its values into [`firebase-config.js`](firebase-config.js), replacing each `YOUR_...` placeholder.

### 2. Create the database

1. In the left menu, open **Build → Firestore Database** and click **Create database**.
2. Choose a location near you, then pick **Start in production mode**.
3. Open the **Rules** tab and replace everything there with the contents of [`firestore.rules`](firestore.rules).
4. Replace the two example emails with your coaches' Google account emails, then click **Publish**.

To add or remove a coach later, edit that list in the **Rules** tab and click **Publish** again.

### 3. Turn on Google sign-in

1. Open **Build → Authentication**, click **Get started**, choose **Google**, turn it on and click **Save**.
2. Go to **Authentication → Settings → Authorized domains** and click **Add domain**. Enter your GitHub Pages address without `https://`, for example `yourname.github.io`.

### 4. Publish on GitHub Pages

1. Push this folder to a GitHub repository.
2. In the repository, go to **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, then pick `main` and `/ (root)`, and click **Save**.
3. After a minute or two, the site is live at `https://yourname.github.io/<repo-name>/`.

The first time a coach signs in, the database is empty. A banner offers to load example data so you can try every page, and **Clear example data** removes it again.

## Updating the site

Edit `index.html`, commit and push. GitHub Pages redeploys on its own.

## Notes

- Until `firebase-config.js` is filled in, the site still works, but it saves to each browser only.
- The Firebase config values are designed to be public. The security rules are what protect your data.
- The free plan allows 50,000 reads and 20,000 writes per day, far more than a coaching staff will use.
