# Privacy Policy Deployment Guide

## Files

- **`app-store-privacy-policy.html`** - Complete, App Store-ready privacy policy page
- **`privacy.html`** - Marketing-focused privacy page (for landing page)
- **`index.html`** - App landing page

## App Store Submission Requirements

For App Store Connect, you need to provide a **publicly accessible URL** for your privacy policy.

### Recommended: GitHub Pages (Free & Fast)

#### Step 1: Push to GitHub
```bash
cd my-daily-memory
git add web/
git commit -m "Add App Store privacy policy"
git push origin main
```

#### Step 2: Enable GitHub Pages
1. Go to your repository: https://github.com/ericlinyi1/my-daily-memory
2. Click **Settings** → **Pages**
3. Under **Source**, select:
   - Branch: `main`
   - Folder: `/` (root)
4. Click **Save**

#### Step 3: Access Your Privacy Policy
After GitHub Pages builds (2-5 minutes), your privacy policy will be available at:

```
https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html
```

**✅ Use this URL in App Store Connect**

---

## Alternative Deployment Options

### Option 2: Hostinger VPS

If you prefer your own domain:

```bash
# Upload files to VPS
scp -r web/* user@your-vps:/var/www/mydailymemory/

# Configure nginx
sudo nano /etc/nginx/sites-available/mydailymemory
```

```nginx
server {
    listen 80;
    server_name mydailymemory.app www.mydailymemory.app;
    
    root /var/www/mydailymemory;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
    
    # Ensure privacy policy is accessible
    location = /privacy {
        rewrite ^ /app-store-privacy-policy.html permanent;
    }
}
```

```bash
# Enable site and restart nginx
sudo ln -s /etc/nginx/sites-available/mydailymemory /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx

# Get SSL certificate (required for App Store)
sudo certbot --nginx -d mydailymemory.app -d www.mydailymemory.app
```

**Privacy Policy URL:** `https://mydailymemory.app/app-store-privacy-policy.html`

---

### Option 3: Netlify (Drag & Drop)

1. Go to https://app.netlify.com/drop
2. Drag the `web/` folder
3. Get instant URL: `https://random-name.netlify.app/app-store-privacy-policy.html`
4. (Optional) Add custom domain in Netlify settings

---

## App Store Connect Setup

When submitting your app:

### 1. App Information Section
- **Privacy Policy URL:** Enter your deployed URL
  - Example: `https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html`

### 2. App Privacy Section
Answer the questionnaire based on the privacy policy:

| Question | Answer |
|----------|--------|
| Does your app collect data? | **No** |
| Does your app use data for tracking? | **No** |
| Does your app link data to users? | **No** |

### 3. Privacy Labels Summary
- **Data Used to Track You:** None
- **Data Linked to You:** None
- **Data Not Linked to You:** None

---

## Verification Checklist

Before submitting to App Store:

- [ ] Privacy policy URL is publicly accessible (not behind login)
- [ ] URL uses HTTPS (required for production)
- [ ] Page loads correctly on iOS Safari
- [ ] Contact email is valid and monitored
- [ ] "Last Updated" date is current
- [ ] Policy matches actual app behavior (v1.0 features)
- [ ] App Store privacy labels match the policy

---

## Custom Domain Setup (Optional)

If you want `https://mydailymemory.app/privacy` instead of GitHub Pages:

### Buy Domain (Recommended Registrars)
- **Namecheap**: ~$10/year
- **Google Domains**: ~$12/year
- **Cloudflare**: ~$10/year

### Point Domain to GitHub Pages
1. In your domain registrar, add DNS records:
   ```
   Type: CNAME
   Name: www
   Value: ericlinyi1.github.io
   
   Type: A (× 4)
   Name: @
   Values:
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

2. In your GitHub repo, create file `CNAME`:
   ```
   mydailymemory.app
   ```

3. Commit and push. GitHub Pages will auto-provision SSL.

**Privacy URL:** `https://mydailymemory.app/web/app-store-privacy-policy.html`

---

## Testing Your Privacy Policy

### Accessibility Test
```bash
curl -I https://your-url/app-store-privacy-policy.html
# Should return: HTTP/2 200
```

### Mobile Test
1. Open URL in iOS Safari
2. Verify page loads and is readable
3. Test on different screen sizes
4. Check that all links work

### Apple Review Test
- Ensure URL works in **private/incognito mode**
- Verify no login or authentication required
- Confirm HTTPS (padlock icon in browser)

---

## Support

If you need help with deployment:
- GitHub Pages issues: https://docs.github.com/pages
- Netlify support: https://docs.netlify.com
- VPS nginx: https://nginx.org/en/docs/

---

**Quick Start (Recommended):**
```bash
# Option 1: GitHub Pages (Free, Fast, Reliable)
git push origin main
# Enable Pages in repo settings
# Use: https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html
```
