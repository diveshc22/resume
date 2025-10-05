# Deployment Guide for cv.divesh.me

This guide will help you set up your resume website with your custom domain cv.divesh.me using Namecheap.

## Option 1: GitHub Pages (Recommended)

### Step 1: Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit: Resume website"
git branch -M main
git remote add origin https://github.com/yourusername/resume.git
git push -u origin main
```

### Step 2: Enable GitHub Pages
1. Go to your repository on GitHub
2. Click **Settings** tab
3. Scroll down to **Pages** section
4. Under **Source**, select "Deploy from a branch"
5. Choose **main** branch and **/ (root)** folder
6. Click **Save**

### Step 3: Configure Custom Domain
1. In the **Pages** settings, enter `cv.divesh.me` in the custom domain field
2. Check **Enforce HTTPS**
3. The CNAME file is already created in this repository

### Step 4: Namecheap DNS Configuration
1. Log into your Namecheap account
2. Go to **Domain List** and click **Manage** next to divesh.me
3. Go to **Advanced DNS** tab
4. Add these DNS records:

```
Type: CNAME Record
Host: cv
Value: yourusername.github.io
TTL: Automatic

Type: A Record  
Host: @
Value: 185.199.108.153
TTL: Automatic

Type: A Record
Host: @  
Value: 185.199.109.153
TTL: Automatic

Type: A Record
Host: @
Value: 185.199.110.153
TTL: Automatic

Type: A Record
Host: @
Value: 185.199.111.153
TTL: Automatic
```

**Wait 24-48 hours** for DNS propagation.

## Option 2: Netlify (Alternative)

### Step 1: Deploy to Netlify
1. Go to [netlify.com](https://netlify.com)
2. Drag and drop your repository folder to deploy
3. Or connect your GitHub repository for auto-deployments

### Step 2: Configure Custom Domain
1. In Netlify dashboard, go to **Domain settings**
2. Add custom domain: `cv.divesh.me`
3. Netlify will provide DNS instructions

### Step 3: Namecheap DNS for Netlify
```
Type: CNAME Record
Host: cv
Value: [your-site-name].netlify.app
TTL: Automatic
```

## Option 3: Vercel (Alternative)

### Step 1: Deploy to Vercel
1. Go to [vercel.com](https://vercel.com)
2. Import your GitHub repository
3. Deploy automatically

### Step 2: Configure Domain
1. In Vercel dashboard, go to **Domains**
2. Add `cv.divesh.me`
3. Follow Vercel's DNS instructions

## Testing Your Setup

Once deployed, test these URLs:
- `https://cv.divesh.me` - Should show your resume
- `https://cv.divesh.me/resume.pdf` - Should download the PDF
- `https://cv.divesh.me/pdf` - Should redirect to PDF

## Troubleshooting

### DNS Not Working
1. Check DNS propagation: [whatsmydns.net](https://whatsmydns.net)
2. Clear browser cache
3. Try incognito/private browsing

### SSL Certificate Issues
- GitHub Pages: Enable "Enforce HTTPS" in settings
- Netlify/Vercel: SSL is automatic

### CNAME File Issues
- Make sure CNAME file contains exactly: `cv.divesh.me`
- No extra spaces or characters

## File Structure
```
├── index.html          # Main resume page
├── resume.pdf          # PDF version
├── redirect.html       # Redirect page
├── CNAME              # Custom domain config
├── .htaccess          # Apache redirects
├── _redirects         # Netlify redirects
└── package.json       # Dependencies
```

## Next Steps
1. Customize the resume content with your real information
2. Generate the actual PDF file
3. Test all functionality
4. Add analytics if desired
