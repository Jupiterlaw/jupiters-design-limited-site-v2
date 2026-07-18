# Deployment Workflow: GitHub → Cloudflare Pages

## Overview
This document outlines the complete workflow for deploying **Jupiter's Design Limited** website from GitHub to Cloudflare Pages and connecting it to the production domain `jupitersdesign.com`.

---

## ✅ Prerequisites

1. **GitHub Repository**: `Jupiterlaw/jupiters-design-limited-site-v2` (this repo)
2. **Cloudflare Account**: Logged in and ready
3. **Domain Ownership**: `jupitersdesign.com` added to Cloudflare DNS
4. **Local Development Environment** (optional): Node.js 18+ for testing

---

## 📋 Phase 1: Local Development & Testing (Optional)

If you want to test locally before pushing:

```bash
# Clone the repository
git clone https://github.com/Jupiterlaw/jupiters-design-limited-site-v2.git
cd jupiters-design-limited-site-v2

# Install dependencies
npm install

# Start development server
npm run dev
# Site will be available at http://localhost:4321

# Build for production (test build)
npm run build
```

---

## 🚀 Phase 2: Push Changes to GitHub

All changes must be committed and pushed to the `main` branch:

```bash
# Check status
git status

# Add all changes
git add .

# Commit with descriptive message
git commit -m "feat: add new section / fix: update content"

# Push to main branch
git push origin main
```

**Important**: Cloudflare Pages automatically builds from the `main` branch. Every push triggers a new deployment.

---

## ☁️ Phase 3: Connect GitHub Repo to Cloudflare Pages

### Step 1: Create Cloudflare Pages Project

1. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Go to **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**
3. Authorize GitHub access (if first time)
4. Select repository: `Jupiterlaw/jupiters-design-limited-site-v2`
5. Click **Begin setup**

### Step 2: Configure Build Settings

Use these exact settings:

| Setting | Value |
|---------|-------|
| **Production branch** | `main` |
| **Build command** | `npm run build` |
| **Build output directory** | `dist` |
| **Root directory** | `/` (leave empty) |
| **Framework preset** | `Astro` |
| **Node.js version** | `18` or `20` (use environment variable `NODE_VERSION=20`) |

#### Environment Variables (if needed):
Add these in **Settings** → **Environment variables**:

```
NODE_VERSION=20
```

### Step 3: Deploy

1. Click **Save and Deploy**
2. Cloudflare will:
   - Clone the repo
   - Run `npm install`
   - Run `npm run build`
   - Deploy the `dist` folder to a `*.pages.dev` URL

3. Wait ~2-5 minutes for first build
4. You'll get a URL like: `https://jupiters-design-limited-site-v2.pages.dev`

---

## 🌐 Phase 4: Connect Custom Domain

### Step 1: Add Custom Domain in Cloudflare Pages

1. In your Cloudflare Pages project → **Custom domains**
2. Click **Set up a custom domain**
3. Enter: `www.jupitersdesign.com`
4. Cloudflare will automatically add DNS records (CNAME)

### Step 2: Configure DNS Records

Go to **Cloudflare Dashboard** → **DNS** → **Records**

Ensure these records exist:

| Type | Name | Target | Proxy status |
|------|------|--------|-------------|
| **CNAME** | `www` | `jupiters-design-limited-site-v2.pages.dev` | Proxied ☁️ |
| **A** or **CNAME** | `@` (root) | Point to `www` (redirect) | Proxied ☁️ |

**For root domain (`jupitersdesign.com`):**

Option A: Use **Page Rules** to redirect `jupitersdesign.com` → `www.jupitersdesign.com`

Option B: Add both `www.jupitersdesign.com` and `jupitersdesign.com` as custom domains in Cloudflare Pages

### Step 3: Enable HTTPS

Cloudflare auto-provisions SSL certificates. Ensure:

- **SSL/TLS encryption mode**: Full (strict)
- **Always Use HTTPS**: ON
- **Automatic HTTPS Rewrites**: ON

---

## 🔄 Phase 5: Continuous Deployment

Once connected, every `git push origin main` triggers:

1. ✅ GitHub receives commit
2. ✅ Cloudflare Pages webhook fires
3. ✅ Automatic build starts
4. ✅ New version deployed to production
5. ✅ Live at `www.jupitersdesign.com` within ~2-3 minutes

### View Build Logs

- Go to **Cloudflare Pages** → Your project → **Deployments**
- Click any deployment to see build logs
- Check for errors if build fails

---

## 🐛 Troubleshooting

### Build Fails

**Error**: `Command not found: astro`

**Fix**: Check `package.json` has `"astro": "^X.X.X"` in `dependencies`

**Error**: `Build exceeded time limit`

**Fix**: Check for infinite loops or large image processing

### Site Not Updating

1. Check **Deployments** tab — is latest commit deployed?
2. Clear browser cache (Cmd+Shift+R)
3. Check Cloudflare DNS propagation: https://dnschecker.org

### Custom Domain Not Working

1. Verify DNS records are **Proxied** (orange cloud)
2. Check SSL/TLS mode is **Full (strict)**
3. Wait up to 24 hours for DNS propagation (usually <10 minutes)

---

## 🔐 Rollback Procedure

### Method 1: Via Cloudflare Dashboard

1. Go to **Pages** → **Deployments**
2. Find the last working deployment
3. Click **⋯** → **Rollback to this deployment**
4. Confirm rollback

### Method 2: Via Git

```bash
# Revert to a previous commit
git log --oneline  # Find commit hash
git revert <commit-hash>
git push origin main
```

---

## 📊 Post-Deployment Checks

After each deployment, verify:

- ✅ Homepage loads: `https://www.jupitersdesign.com`
- ✅ Navigation works (all section links)
- ✅ Contact form appears correctly
- ✅ WhatsApp button links to `wa.me/85295715155`
- ✅ Mobile responsive (test on phone)
- ✅ Page load speed < 3 seconds ([PageSpeed Insights](https://pagespeed.web.dev/))
- ✅ SSL certificate valid (green padlock in browser)

---

## 🎯 Quick Reference Commands

```bash
# Local development
npm run dev

# Build locally
npm run build

# Preview production build
npm run preview

# Push to production
git add .
git commit -m "your message"
git push origin main
```

---

## 📞 Support Resources

- **Cloudflare Pages Docs**: https://developers.cloudflare.com/pages/
- **Astro Docs**: https://docs.astro.build/
- **GitHub Docs**: https://docs.github.com/

---

## 🚨 Important Notes

1. **Never commit sensitive data**: API keys, passwords, etc. (use environment variables)
2. **Test locally first**: Run `npm run build` before pushing large changes
3. **Monitor deployments**: Check **Deployments** tab after each push
4. **DNS propagation**: Allow up to 24 hours for domain changes (usually much faster)
5. **Build time**: Each deployment takes 2-5 minutes

---

**Last Updated**: 2026-07-18  
**Maintained By**: Jupiterlaw
