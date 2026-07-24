# Cloudflare Pages Deployment Guide

This folder is prepared as a simple static website for Cloudflare Pages. It contains one main HTML file and references two image files in an `assets/` folder.

## Folder layout

Your final project should look exactly like this:

```text
cloudflare-naf-letter/
├── index.html
├── README.md
└── assets/
    ├── Claudia_de_Luna_signature-2.jpg
    └── TheGratuitousArpSummary.jpg
```

Do not rename these two image files. The HTML already references them exactly as uploaded.

## What this site does

- Shows a closed letter with a wax seal.
- Opens when the wax seal is clicked.
- Displays the NAF Advisory Board essay.
- Shows the signature image and The Gratuitous Arp summary image.
- Includes blog, LinkedIn, and BlueSky links.

## Before you deploy

Make sure these files are together in the same folder:

- `index.html`
- `README.md`
- `assets/Claudia_de_Luna_signature-2.jpg`
- `assets/TheGratuitousArpSummary.jpg`

If the images are missing or in the wrong folder, the page will load but those images will not appear.

## Option 1: Easiest method, drag and drop to Cloudflare Pages

This is the easiest way if you are new to Cloudflare.

### Step 1: Create a Cloudflare account

1. Go to [https://dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up)
2. Create an account.
3. Verify your email if Cloudflare asks you to.

### Step 2: Open Cloudflare Pages

1. Sign in to the Cloudflare dashboard.
2. In the left menu, click **Workers & Pages**.
3. Click **Create**.
4. Choose **Pages**.
5. Choose **Upload assets** if that option appears, or choose the direct upload option for a static site.

### Step 3: Prepare your local folder

1. Create a folder on your computer named `cloudflare-naf-letter`.
2. Put `index.html` inside it.
3. Create a subfolder named `assets`.
4. Put these uploaded image files inside `assets`:
   - `Claudia_de_Luna_signature-2.jpg`
   - `TheGratuitousArpSummary.jpg`
5. Put `README.md` in the top-level folder beside `index.html`.

### Step 4: Upload the folder

Depending on the Cloudflare screen you see:

- If Cloudflare lets you upload a folder, upload the whole `cloudflare-naf-letter` folder.
- If Cloudflare wants files, upload `index.html` plus the `assets` folder contents in the correct structure.

### Step 5: Deploy

1. Give the project a name such as `naf-letter` or `claudia-naf-letter`.
2. Click **Deploy site**.
3. Wait for Cloudflare to finish publishing.
4. Cloudflare will give you a URL that looks something like:
   - `https://naf-letter.pages.dev`

That URL is the shareable link you can send to someone.

## Option 2: GitHub and Cloudflare Pages

Use this method if you want version control and easy future updates.

### Step 1: Create a GitHub repository

1. Sign in to GitHub.
2. Create a new repository, for example `cloudflare-naf-letter`.
3. Upload:
   - `index.html`
   - `README.md`
   - `assets/Claudia_de_Luna_signature-2.jpg`
   - `assets/TheGratuitousArpSummary.jpg`

### Step 2: Connect GitHub to Cloudflare

1. In Cloudflare, go to **Workers & Pages**.
2. Click **Create**.
3. Choose **Pages**.
4. Choose **Connect to Git**.
5. Authorize GitHub if prompted.
6. Select the repository you created.

### Step 3: Configure the project

Use these settings:

- **Project name:** any name you like.
- **Production branch:** `main`.
- **Framework preset:** `None`.
- **Build command:** leave blank.
- **Build output directory:** leave blank, use `/`, or use the root depending on what Cloudflare shows.

This project is plain static HTML, so it does not need npm, a framework, or a build step.

### Step 4: Deploy

1. Click **Save and Deploy**.
2. Wait for the first deployment to finish.
3. Open the generated `pages.dev` URL.

## Testing after deploy

After deployment, test these things:

1. The site loads without errors.
2. The letter starts fully closed.
3. Clicking the wax seal opens the letter.
4. The signature image displays.
5. The Gratuitous Arp summary image displays.
6. The blog and LinkedIn links open correctly.
7. The page looks good on desktop and mobile.

## Troubleshooting

### The images do not appear

Usually this means one of these is wrong:

- The images are not inside the `assets` folder.
- The filenames do not exactly match.
- The case of the letters changed.

The correct filenames are:

- `Claudia_de_Luna_signature-2.jpg`
- `TheGratuitousArpSummary.jpg`

### The page opens but looks broken

Check that `index.html` is in the top-level folder, not inside another nested folder.

### The link works but shows an older version

Cloudflare may still be serving the previous deploy. Wait a minute and refresh. If needed, redeploy from the dashboard.

## Updating later

If you want to change the essay, colors, initials, or links later:

1. Edit `index.html` locally.
2. Upload again through Cloudflare, or push changes to GitHub.
3. Cloudflare will publish the update.

## Suggested project name

A clean project name would be:

- `claudia-naf-letter`

That would usually produce a URL similar to:

- `https://claudia-naf-letter.pages.dev`

## Final checklist

Before sending the link, confirm:

- The site opens at the Cloudflare URL.
- The wax seal opens the letter.
- The letter content is final.
- The images display properly.
- The links open in new tabs.
- Mobile view still looks good.

## GitHub first workflow

Since the site will be stored in GitHub, this is the cleanest approach.

### Create the repository

1. In GitHub, create a new repository named something like `claudia-naf-letter`.
2. On your computer, create this exact folder structure:

```text
claudia-naf-letter/
├── index.html
├── README.md
└── assets/
    ├── Claudia_de_Luna_signature-2.jpg
    └── TheGratuitousArpSummary.jpg
```

3. Copy the shared `index.html` and `README.md` into the top-level folder.
4. Copy your two image files into the `assets/` folder.

### Upload to GitHub using the web UI

If you do not want to use git on the command line yet:

1. Open your new GitHub repository.
2. Click **Add file**.
3. Choose **Upload files**.
4. Upload `index.html` and `README.md`.
5. Create an `assets` folder in the repository.
6. Upload:
   - `Claudia_de_Luna_signature-2.jpg`
   - `TheGratuitousArpSummary.jpg`
7. Commit the changes.

### Upload to GitHub using git on the command line

If you want to do it locally with git:

```bash
git init
git add .
git commit -m "Initial NAF interactive letter site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/claudia-naf-letter.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

### Connect GitHub repo to Cloudflare Pages

1. Log in to Cloudflare.
2. Open **Workers & Pages**.
3. Click **Create**.
4. Choose **Pages**.
5. Choose **Connect to Git**.
6. Select GitHub.
7. Authorize Cloudflare to access your repositories if prompted.
8. Choose the `claudia-naf-letter` repository.

### Cloudflare Pages settings

Use these values:

- **Project name:** `claudia-naf-letter`
- **Production branch:** `main`
- **Framework preset:** `None`
- **Build command:** leave blank
- **Build output directory:** leave blank, `/`, or the root depending on the prompt

Then click **Save and Deploy**.

### How updates work later

Once GitHub is connected to Cloudflare Pages:

1. Edit `index.html` or replace images in your repository.
2. Commit and push the changes to `main`.
3. Cloudflare automatically detects the update.
4. Cloudflare redeploys the site.
5. Refresh the `pages.dev` URL to see the new version.

This is the nicest long-term setup because GitHub becomes your source of truth and Cloudflare republishes automatically after each update.
