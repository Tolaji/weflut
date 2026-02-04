# Coming Soon Website - Deployment Guide

## Quick Start

This is a professional "Coming Soon" landing page ready for GitHub Pages deployment.

## Features
- ✅ Email capture for launch notifications
- ✅ Contact form
- ✅ Social media links
- ✅ Background image support
- ✅ Fully responsive design
- ✅ Professional corporate styling

## Setup Instructions

### 1. Form Configuration (Formspree - Recommended)

**Formspree** is free for up to 50 submissions/month and requires no backend setup.

1. Go to [https://formspree.io](https://formspree.io)
2. Sign up for a free account
3. Create two forms:
   - **Email Notifications Form**
   - **Contact Form**
4. Copy the form endpoints (looks like `https://formspree.io/f/xyzabc123`)
5. In `index.html`, replace `YOUR_FORM_ID` in both forms:
   ```html
   <!-- Line ~239 - Email notification form -->
   <form class="email-form" id="notifyForm" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   
   <!-- Line ~253 - Contact form -->
   <form class="contact-form" id="contactForm" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

**Alternative: Web3Forms** (also free, 250 submissions/month)
1. Go to [https://web3forms.com](https://web3forms.com)
2. Get your access key
3. Add hidden input to forms:
   ```html
   <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY">
   ```

### 2. Customize Content

Edit `index.html` to personalize:

```html
<!-- Line 90-92: Company Name/Logo -->
<h1>Your Company</h1>

<!-- Line 96-98: Headline & Description -->
<h2>We're Launching Soon</h2>
<p>Something exciting is coming...</p>

<!-- Line 248-259: Social Media Links -->
<a href="https://linkedin.com/company/yourcompany"...>
<a href="https://twitter.com/yourcompany"...>
<a href="https://facebook.com/yourcompany"...>
<a href="https://instagram.com/yourcompany"...>

<!-- Line 289: Footer -->
<p>&copy; 2025 Your Company. All rights reserved.</p>
```

### 3. Add Background Image

**Option A: Use your own image**
1. Add your image file (e.g., `background.jpg`) to the repository
2. The CSS already references it on line 35:
   ```css
   background-image: url('background.jpg');
   ```

**Option B: Use a free stock image**
- [Unsplash](https://unsplash.com) - High-quality free images
- [Pexels](https://pexels.com) - Free stock photos

**Recommended image specs:**
- Resolution: 1920x1080 or higher
- Format: JPG (optimized) or WebP
- File size: Under 500KB for fast loading

### 4. Deploy to GitHub Pages

#### Method 1: Using GitHub Web Interface (Easiest)

1. **Create a new repository:**
   - Go to [GitHub](https://github.com)
   - Click "New Repository"
   - Name it: `yourcompany-coming-soon` (or any name)
   - Make it Public
   - Click "Create repository"

2. **Upload files:**
   - Click "uploading an existing file"
   - Drag and drop: `index.html` and your background image
   - Commit changes

3. **Enable GitHub Pages:**
   - Go to repository Settings → Pages
   - Source: Deploy from a branch
   - Branch: `main` (or `master`)
   - Folder: `/ (root)`
   - Click Save

4. **Access your site:**
   - Your site will be live at: `https://yourusername.github.io/yourcompany-coming-soon/`
   - It may take 2-5 minutes to deploy

#### Method 2: Using Git (Command Line)

```bash
# Navigate to your project directory
cd /path/to/your/coming-soon-site

# Initialize git repository
git init

# Add files
git add index.html background.jpg README.md

# Commit
git commit -m "Initial commit: Coming soon page"

# Add GitHub remote (replace with your repo URL)
git remote add origin https://github.com/yourusername/yourcompany-coming-soon.git

# Push to GitHub
git branch -M main
git push -u origin main

# Enable GitHub Pages in repository settings (see Method 1, step 3)
```

### 5. Custom Domain (Optional)

To use your own domain (e.g., `www.yourcompany.com`):

1. **In your repository:**
   - Create a file named `CNAME` (no extension)
   - Add your domain: `www.yourcompany.com`
   - Commit and push

2. **In your domain registrar (GoDaddy, Namecheap, etc.):**
   - Add a CNAME record:
     - Name/Host: `www`
     - Value/Points to: `yourusername.github.io`
   - Or add A records for apex domain:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```

3. **GitHub Pages settings:**
   - Enable "Enforce HTTPS" for secure connection

## File Structure

```
yourcompany-coming-soon/
├── index.html          # Main landing page
├── background.jpg      # Background image
├── CNAME              # (Optional) Custom domain
└── README.md          # This file
```

## Testing Locally

Before deploying, test locally:

```bash
# Option 1: Python 3
python3 -m http.server 8000

# Option 2: Python 2
python -m SimpleHTTPServer 8000

# Option 3: Node.js (if you have it)
npx http-server

# Then visit: http://localhost:8000
```

## Performance Optimization

1. **Optimize background image:**
   ```bash
   # Using ImageMagick (install if needed)
   convert background.jpg -resize 1920x1080 -quality 85 background.jpg
   
   # Or use online tools:
   # - TinyPNG (https://tinypng.com)
   # - Squoosh (https://squoosh.app)
   ```

2. **Enable caching** (create `.htaccess` if using Apache):
   ```apache
   <IfModule mod_expires.c>
     ExpiresActive On
     ExpiresByType image/jpg "access plus 1 year"
     ExpiresByType image/jpeg "access plus 1 year"
     ExpiresByType image/webp "access plus 1 year"
   </IfModule>
   ```

## Browser Support

✅ Chrome/Edge (latest)
✅ Firefox (latest)
✅ Safari (latest)
✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Troubleshooting

**Forms not working?**
- Verify Formspree form IDs are correct
- Check browser console for errors
- Test form submission on Formspree dashboard

**Background image not showing?**
- Verify file name matches CSS reference
- Check file is in same directory as index.html
- Try absolute URL for testing: `url('https://...')`

**GitHub Pages not deploying?**
- Ensure repository is public
- Check Actions tab for build errors
- Wait 5-10 minutes for initial deployment

**Custom domain not working?**
- Verify CNAME file contains only the domain (no http://)
- Check DNS propagation: [https://dnschecker.org](https://dnschecker.org)
- DNS changes can take 24-48 hours

## Next Steps

1. ✅ Configure form handlers (Formspree/Web3Forms)
2. ✅ Customize content and branding
3. ✅ Add your background image
4. ✅ Deploy to GitHub Pages
5. ✅ Test all forms and links
6. ✅ (Optional) Set up custom domain
7. ✅ Share your coming soon page!

## Analytics (Optional)

Add Google Analytics to track visitors:

```html
<!-- Add before </head> in index.html -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## Support

For issues or questions:
- GitHub Pages Docs: [https://pages.github.com](https://pages.github.com)
- Formspree Docs: [https://help.formspree.io](https://help.formspree.io)

---

**Built with ❤️ for professionals who ship.**
