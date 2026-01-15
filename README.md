# Turas Website (Static)

This folder contains a calm, brand-aligned static website based on:
- Turas Homepage Copy
- 1-Page Designer Brief
- Turas Brand Style Guide (colors, typography, spacing principles)

## Files
- `index.html` — Homepage
- `designer-brief.html` — Designer brief page
- `styles.css` — Brand styling
- `assets/turas-logo.png` — Logo file
- `assets/turas-travel-image.png` — Hero image
- `CNAME` — Custom domain configuration (turas.world)
- `.nojekyll` — Ensures all files are served correctly

## Quick start
Open `index.html` in a browser.

## GitHub Pages Deployment

### Setup Steps:

1. **Push to GitHub Repository**
   - Push all files to your GitHub repository
   - Ensure files are in the root directory or a `docs` folder

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Select source branch (usually `main` or `master`)
   - Select folder (usually `/ (root)`)
   - Click Save

3. **Configure DNS for Custom Domain (turas.world)**
   
   **Important:** For root domains (apex domains like `turas.world`), you must use **A records**, not CNAME records. CNAME records cannot be used at the root domain level.
   
   At your domain registrar (where you purchased turas.world), add these DNS records:
   
   **Use A Records (Required for root domain):**
   - Type: `A`
   - Name: `@` (or leave blank/root, or `turas.world`)
   - Value: Add **all four** GitHub Pages IP addresses as separate A records:
     1. `185.199.108.153`
     2. `185.199.109.153`
     3. `185.199.110.153`
     4. `185.199.111.153`
   - TTL: `3600` (1 Hour) or default
   
   **Note:** You need to create **four separate A records**, one for each IP address above. Some registrars let you add multiple values in one record, while others require separate records for each IP.
   
   **Alternative (if your registrar supports it):**
   - Some registrars support ALIAS/ANAME records for root domains
   - If available, use: Type `ALIAS` or `ANAME`, Name `@`, Value `turas2023.github.io`

4. **Wait for DNS Propagation**
   - DNS changes can take 24-48 hours to propagate
   - Use GitHub's "Check again" button in Settings → Pages
   - Once DNS resolves, HTTPS will become available

5. **Enable HTTPS**
   - After DNS is verified (green checkmark), the "Enforce HTTPS" checkbox will become available
   - **Important:** Check the "Enforce HTTPS" checkbox in Settings → Pages
   - Wait a few minutes after enabling for SSL certificate to be provisioned
   - Once enabled, your site will be accessible at `https://turas.world`
   - **Note:** If HTTPS is not enforced, you must use `http://turas.world` (without 's')

### Troubleshooting Common Errors

#### ERR_SSL_PROTOCOL_ERROR or "This site can't provide a secure connection"

**Problem:** You're trying to access `https://turas.world` but HTTPS isn't enabled yet.

**Solution:**
1. **Immediate fix:** Use `http://turas.world` (without the 's') - this will work right away
2. **Permanent fix:** 
   - Go to GitHub repository → Settings → Pages
   - Check the "Enforce HTTPS" checkbox
   - Wait 5-10 minutes for GitHub to provision the SSL certificate
   - Then `https://turas.world` will work

#### 404 Errors

If you're getting a 404 error when visiting `turas.world`, check the following:

1. **Use HTTP (not HTTPS) if HTTPS is Not Enforced**
   - If "Enforce HTTPS" is unchecked in GitHub Pages settings, use: `http://turas.world` (without the 's')
   - HTTPS won't work until you enable "Enforce HTTPS" in Settings → Pages
   - After enabling HTTPS enforcement, wait a few minutes, then try `https://turas.world`

2. **Clear Browser Cache**
   - Clear your browser cache or try an incognito/private window
   - Sometimes browsers cache 404 errors
   - Try a different browser to rule out cache issues

3. **Verify GitHub Pages is Enabled**
   - Go to your repository on GitHub
   - Navigate to Settings → Pages
   - Ensure "Source" is set to a branch (usually `main` or `master`)
   - Ensure the folder is set to `/ (root)`
   - You should see "Your site is live at http://turas.world/"

2. **Test the GitHub Pages URL First**
   - Before the custom domain works, test with: `https://[your-username].github.io/[repository-name]/`
   - For example: `https://turas2023.github.io/Turas.com/` (adjust based on your actual repo name)
   - If this works but `turas.world` doesn't, it's a DNS issue
   - If this also gives 404, GitHub Pages isn't set up correctly

3. **Check Repository Name**
   - The repository name affects the GitHub Pages URL
   - If your repo is named `Turas.com`, the URL would be `[username].github.io/Turas.com/`
   - Consider renaming the repo to match your username for a cleaner URL (e.g., `turas2023.github.io`)

4. **Verify Files are Committed and Pushed**
   - Ensure `index.html` is in the root of the repository
   - Ensure `CNAME` file is committed and pushed
   - Ensure `.nojekyll` file is committed and pushed
   - All files should be on the branch you selected in Pages settings

5. **DNS Configuration**
   - If DNS is configured but you still get 404, wait 24-48 hours for full propagation
   - Use `dig turas.world` or `nslookup turas.world` to verify DNS is pointing to GitHub IPs
   - The domain should resolve to one of the GitHub Pages IP addresses
   - **Important:** If `turas.world` redirects to `turas.com`, check your domain registrar:
     - Look for "Domain Forwarding" or "URL Redirect" settings and disable them
     - Ensure `turas.world` DNS A records point to GitHub Pages IPs (185.199.108.153, etc.), NOT to the same server as `turas.com`
     - Remove any CNAME records that point `turas.world` to `turas.com` or its server

6. **Check GitHub Pages Build Status**
   - Go to Actions tab in your repository
   - Look for any failed builds or errors
   - GitHub Pages should show "published" status in Settings → Pages

### Verification
- The `CNAME` file is already configured with `turas.world`
- The `.nojekyll` file ensures all files are served correctly
- All asset paths are relative and will work on GitHub Pages

## Next steps (optional)
- Connect the contact form to Formspree, HubSpot, Webflow, or your backend.
- Add a mobile nav (hamburger) if needed.
