# GitHub Pages Setup for Status App Legal Documents

## Quick Setup Guide

Your legal documents (Privacy Policy, Terms of Service, Support) are ready to be hosted on GitHub Pages!

### Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `status-legal` (or any name you prefer)
3. Description: "Legal documents for Status app"
4. Choose **Public** (required for free GitHub Pages)
5. Click "Create repository"

### Step 2: Push Your Code

Run these commands in the `/Users/noelasfaha/Status` directory:

```bash
# Add all files
git add .

# Create initial commit
git commit -m "Initial commit with legal documents"

# Add your GitHub repository as remote (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/status-legal.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top right)
3. Scroll down to **Pages** (left sidebar)
4. Under "Source", select:
   - Source: **Deploy from a branch**
   - Branch: **main**
   - Folder: **/docs**
5. Click **Save**

### Step 4: Access Your Live URLs

After 2-3 minutes, your pages will be live at:

- **Home:** `https://YOUR_USERNAME.github.io/status-legal/`
- **Privacy Policy:** `https://YOUR_USERNAME.github.io/status-legal/privacy.html`
- **Terms of Service:** `https://YOUR_USERNAME.github.io/status-legal/terms.html`
- **Support:** `https://YOUR_USERNAME.github.io/status-legal/support.html`

### Step 5: Add URLs to App Store Connect

Use these URLs when submitting to App Store:

1. **Privacy Policy URL:** `https://YOUR_USERNAME.github.io/status-legal/privacy.html`
2. **Terms of Service URL:** `https://YOUR_USERNAME.github.io/status-legal/terms.html`
3. **Support URL:** `https://YOUR_USERNAME.github.io/status-legal/support.html`

---

## Alternative: Use Your Own Domain (Optional)

If you have a custom domain:

1. Add a file named `CNAME` to the `/docs` folder with your domain:
   ```
   legal.yourdomain.com
   ```

2. Add DNS records at your domain provider:
   - Type: CNAME
   - Name: legal (or your subdomain)
   - Value: YOUR_USERNAME.github.io

3. Your URLs become:
   - `https://legal.yourdomain.com/privacy.html`
   - `https://legal.yourdomain.com/terms.html`
   - `https://legal.yourdomain.com/support.html`

---

## Update Contact Email

**IMPORTANT:** Before going live, update the support email in all documents:

1. Search for `support@statusapp.com` in:
   - `docs/privacy.html`
   - `docs/terms.html`
   - `docs/support.html`

2. Replace with your actual support email address

---

## Testing Your URLs

After GitHub Pages is live:

1. Visit each URL in your browser
2. Verify all pages load correctly
3. Check that all internal links work
4. Test on mobile to ensure responsive design works

---

## Troubleshooting

**Pages not showing up?**
- Wait 5-10 minutes for GitHub Pages to build
- Check repository is **Public** (not Private)
- Verify `/docs` folder is selected in Settings → Pages
- Check the "Actions" tab for build status

**404 Error?**
- Ensure branch is `main` (not `master`)
- Verify files are in `/docs` folder
- Check file names are exactly `privacy.html`, `terms.html`, `support.html`

**Need to make changes?**
- Edit files locally
- Commit and push changes: `git add . && git commit -m "Update legal docs" && git push`
- Changes will appear in 1-2 minutes

---

## Files Structure

```
Status/
├── docs/                    # GitHub Pages serves from here
│   ├── index.html          # Home page with links
│   ├── privacy.html        # Privacy Policy
│   ├── terms.html          # Terms of Service
│   └── support.html        # Support page
├── privacy.html            # Original (for reference)
└── DEPLOYMENT_GUIDE.md     # Main deployment guide
```

---

## Next Steps After Hosting

1. ✅ Verify all URLs are live
2. ✅ Update support email addresses
3. ✅ Add URLs to App Store Connect
4. ✅ Test all pages on mobile
5. ✅ Continue with app submission

Good luck with your launch! 🚀
