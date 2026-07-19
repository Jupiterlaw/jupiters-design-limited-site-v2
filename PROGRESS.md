# Project Progress Tracker

**Project**: Jupiter's Design Limited - Official Website  
**Repository**: `Jupiterlaw/jupiters-design-limited-site-v2`  
**Live URL**: [www.jupitersdesign.com](https://www.jupitersdesign.com)  
**Last Updated**: 2026-07-20

---

## 🎯 Overall Status

| Milestone | Status | Completion Date |
|-----------|--------|----------------|
| 📁 Repository Setup | ✅ Complete | 2026-07-18 |
| 🎨 Website Design & Build | ✅ Complete | 2026-07-20 |
| ☁️ Cloudflare Pages Connection | ✅ Complete | 2026-07-20 |
| 🌐 Custom Domain DNS Setup | ✅ Complete | 2026-07-20 |
| 🚀 Production Launch | ✅ Complete | 2026-07-20 |

**Legend**:  
✅ Complete | 🟡 Pending | 🔄 In Progress | ⚠️ Blocked

---

## 🤖 Phase 2: Agent Refinement Session (2026-07-20)

Hermes Agent 協作的一輪密集迭代。所有改動已 commit + push 到 `origin/main`，Cloudflare Pages 自動部署。

### ✅ Completed This Session

**Brand & Header**
- [x] 品牌 logo 放入 header（`public/logo.svg`，深色 Hero 用 `filter: brightness(0) invert(.94)` 轉白，滾動後回復 navy）
- [x] 修 header 選單 bug #1：`document.currentScript` 在 Astro ES module 中恆為 null → 改用 `document.querySelector('[data-menu-toggle]')`（commit `33ccda8`）
- [x] 修 header 中文首頁退化英文 bug：`index.astro` 傳 `lang="zh"` 但判斷條件是 `zh-HK` → 改 `lang="zh-HK"`（commit `33ccda8`）
- [x] 修 header 選單 bug #2（「有反應但看不到」）：mobile menu 原嵌套在 `<header>` 內（fixed + z-index:50），視覺被壓住 → 移出 header 到 body 層、z-index 提到 60（commit `1eb3e13`）

**Bilingual Calculator**
- [x] `PriceCalculator.astro` 改為 bilingual（zh-HK / en），新增 `/en/estimate/` 路由（commit `661b8d8`）
- [x] 隱藏每平方呎單價顯示，保留後端預算計算邏輯（commit `28ea4f4`）
- [x] 移除「估算加 HK$40 / sq ft」加價說明文字，保留拆舊費計算（commit `09f5096`）
- [x] essential 方案標註「只含安裝」+「不含材料」小字；signature/elevated 維持「材料與安裝全包」（commit `b3106dc`）
- [x] 戶外基礎之選單價 50–55 → 45–50 per sq ft（commit `dc3e08d`）
- [x] 加可編輯 sq ft 輸入框，與 slider 雙向同步、夾值 [min,max]（commit `3cb9944`）

**Editorial UI**
- [x] 為計算機寫一套 editorial / 安靜奢華 CSS（原本計算機完全無樣式），token 驅動（commit `f75b78c`）

**SEO & Deploy**
- [x] 加 `@astrojs/sitemap`，canonical/sitemap 用正式網域 `https://www.jupitersdesign.com`（commit `2a33006`）
- [x] Cloudflare Pages project `jupiters-design-limited-site-v2` 綁定正式網域：
  - `www.jupitersdesign.com` 與 `jupitersdesign.com` 從舊 project `jupitersdesignlimited`（連錯誤 repo `Jupiterlaw/Jupiters-Design-Limited`）移除，改指到本 project
  - zone `jupitersdesign.com` 設 Redirect Rule：根網域 301 → www

### 🔗 Key Technical Notes
- Astro `<script>` 是 module，`document.currentScript` 恆為 null → 用 `document.querySelector`
- lightningcss minifier 會把 `invert(1)` 壓成空 `invert()` → logo 反白用 `invert(.94)`
- 計算機卡片由 JS `innerHTML` 動態生成 → scoped style 針對動態節點要用 `:global()`
- `git push` 走 Windows Git Credential Manager 快取憑證，Agent 可直接 push（無需 token）

### 📌 Pending / Next Possible Steps
- [x] Search Console 驗證 `jupitersdesign.com`（Cloudflare Domain Connect 自動）+ 提交 sitemap `https://www.jupitersdesign.com/sitemap-index.xml`（狀態：成功，2026-07-20）
- [ ] 線上視覺確認（本環境無瀏覽器，需用戶實際開 `www.jupitersdesign.com` 檢查）
- [ ] 落地頁英文版 `/en/spc-flooring-hong-kong/` + 英文 Header menu 加連結
- [ ] 多 1–2 個落地頁（`/floor-installation-hong-kong/`、`/flooring-quotation-hong-kong/`）
- [ ] 「SPC 地板香港完整指南」長文（提升 topical authority）
- [ ] 備份檔 `C:\Users\Jupiter\PROGRESS.md.backup.*` 已刪（2026-07-20 清理）

---

## 🛠️ Phase 1: Website Development

### ✅ Completed Tasks

- [x] Initialize Astro project with TypeScript
- [x] Configure `astro.config.mjs` with site URL (`https://www.jupitersdesign.com`)
- [x] Build complete `index.astro` with all 10 sections:
  - [x] Hero section with background image
  - [x] Trust badges row (experience, projects, ratings)
  - [x] Audience segmentation cards (Residential / B2B / Commercial)
  - [x] Services grid (6 service cards)
  - [x] Portfolio gallery (3 project showcases)
  - [x] "How It Works" process flow (4 steps)
  - [x] FAQ accordion (5 questions)
  - [x] About Us section
  - [x] Contact form (4 fields: Name, Phone, Area, Project Type)
  - [x] Footer with links and contact info
- [x] Add sticky WhatsApp floating button (+852 9571 5155)
- [x] Add responsive navigation bar (mobile menu)
- [x] Integrate Tailwind CSS via CDN
- [x] Add custom color palette (warm wood tones + orange accent)
- [x] Add vanilla JavaScript for:
  - [x] Mobile menu toggle
  - [x] FAQ accordion
  - [x] Smooth scroll navigation
  - [x] Form submission handler
- [x] Use Traditional Chinese (繁體中文) for all content
- [x] Add proper SEO meta tags
- [x] Use placeholder markers for images/data

### 🟡 Pending Tasks

- [ ] Replace placeholder images with real project photos
- [ ] Update trust badge numbers with actual data
- [ ] Add real testimonials (if available)
- [ ] Optimize images for web (compress, WebP format)
- [ ] Add Google Analytics tracking code (if needed)
- [ ] Add sitemap.xml and robots.txt
- [ ] Create sub-pages:
  - [ ] `/services` - Services detail page
  - [ ] `/portfolio` - Full portfolio grid
  - [ ] `/about` - Expanded about page
  - [ ] `/faq` - Full FAQ page
  - [ ] `/contact` - Standalone contact page
  - [ ] `/blog` - Blog/resources section (optional)

---

## 📚 Phase 2: Documentation

### ✅ Completed

- [x] Create `Workflow.md` - Complete deployment guide
- [x] Create `Progress.md` - This tracking document
- [x] Add README.md with project overview (already exists)

### 🟡 Pending

- [ ] Document content update procedures
- [ ] Create style guide for future updates
- [ ] Add troubleshooting FAQ for common issues

---

## ☁️ Phase 3: Cloudflare Pages Deployment

### 🟡 Steps to Complete

1. **Connect GitHub to Cloudflare Pages**
   - [ ] Log in to Cloudflare Dashboard
   - [ ] Go to Workers & Pages → Create application → Pages
   - [ ] Authorize GitHub access
   - [ ] Select repository: `Jupiterlaw/jupiters-design-limited-site-v2`
   - [ ] Configure build settings:
     - Production branch: `main`
     - Build command: `npm run build`
     - Build output directory: `dist`
     - Framework preset: `Astro`
   - [ ] Click "Save and Deploy"
   - [ ] Wait for first build to complete (~2-5 mins)
   - [ ] Verify preview URL: `https://jupiters-design-limited-site-v2.pages.dev`

2. **Test Preview Deployment**
   - [ ] Check homepage loads correctly
   - [ ] Test navigation (all section links work)
   - [ ] Test mobile responsive layout
   - [ ] Test WhatsApp button link
   - [ ] Test contact form (client-side validation)
   - [ ] Test FAQ accordion

### ⚠️ Potential Issues

- **Build fails**: Check build logs in Cloudflare Pages dashboard
- **Tailwind not loading**: CDN should work without build step (already using CDN)
- **Images broken**: Check `public/` folder and image paths

---

## 🌐 Phase 4: Custom Domain Setup

### 🟡 Steps to Complete

1. **Add Custom Domain in Cloudflare Pages**
   - [ ] In Cloudflare Pages project → Custom domains
   - [ ] Click "Set up a custom domain"
   - [ ] Enter: `www.jupitersdesign.com`
   - [ ] Cloudflare auto-adds CNAME record

2. **Configure DNS Records**
   - [ ] Go to Cloudflare DNS dashboard
   - [ ] Verify CNAME record exists:
     - Type: `CNAME`
     - Name: `www`
     - Target: `jupiters-design-limited-site-v2.pages.dev`
     - Proxy: ON (☁️ orange cloud)
   - [ ] Add root domain redirect (optional):
     - Add both `www.jupitersdesign.com` and `jupitersdesign.com` as custom domains
     - OR use Page Rule to redirect root to www

3. **Enable HTTPS**
   - [ ] Verify SSL/TLS mode: Full (strict)
   - [ ] Enable "Always Use HTTPS"
   - [ ] Enable "Automatic HTTPS Rewrites"
   - [ ] Wait for SSL certificate provisioning (~5-10 mins)

4. **Verify Live Site**
   - [ ] Visit `https://www.jupitersdesign.com`
   - [ ] Check green padlock (SSL valid)
   - [ ] Test all sections again on live domain
   - [ ] Test on multiple devices (mobile, tablet, desktop)

---

## 🚀 Phase 5: Post-Launch

### 🟡 Immediate Tasks (Within 24 Hours)

- [ ] Submit sitemap to Google Search Console
- [ ] Submit site to Bing Webmaster Tools
- [ ] Test page load speed (target: < 3 seconds)
- [ ] Run accessibility audit (WAVE, Lighthouse)
- [ ] Share live site with client for feedback
- [ ] Monitor Cloudflare Analytics for traffic

### 🟡 Short-Term (Within 1 Week)

- [ ] Replace all `[PLACEHOLDER]` content with real data
- [ ] Add real project photos to portfolio
- [ ] Collect and add customer testimonials
- [ ] Set up contact form backend (e.g., Formspree, Netlify Forms)
- [ ] Add WhatsApp Business API integration (optional)
- [ ] Create Instagram feed integration (optional)

### 🟡 Long-Term (1-3 Months)

- [ ] Create blog section with SEO articles
- [ ] Add product/service pages
- [ ] Implement online quote calculator
- [ ] Add multi-language support (English + Traditional Chinese)
- [ ] Set up Google Ads / Facebook Ads campaigns
- [ ] Monitor and improve SEO rankings

---

## 📈 Success Metrics

| Metric | Target | Current Status |
|--------|--------|---------------|
| **Page Load Speed** | < 3 seconds | 🟡 Not measured yet |
| **Lighthouse SEO Score** | > 90 | 🟡 Not measured yet |
| **Mobile Usability** | 100% pass | ✅ Design is mobile-first |
| **Form Submissions/Month** | > 20 | 🟡 Site not live yet |
| **Organic Search Traffic** | Growing monthly | 🟡 Not launched yet |

---

## 📝 Notes & Action Items

### Client Action Required:

1. **Provide Real Content**:
   - Company establishment year
   - Actual project count
   - Team/company photos
   - Before/after project photos (at least 6-10 sets)
   - Customer testimonials (names + quotes)
   - Certifications/licenses photos

2. **Cloudflare Pages Connection**:
   - Follow `Workflow.md` Phase 3 instructions
   - OR provide Cloudflare account access for setup assistance

3. **Contact Form Backend**:
   - Decide on form submission handler:
     - Option A: Email forwarding (simple)
     - Option B: CRM integration (e.g., HubSpot)
     - Option C: Direct database storage

### Developer Notes:

- Tailwind CDN used for simplicity — consider switching to build-time Tailwind for production optimization
- Images currently use Unsplash placeholders — replace with real photos
- Form submission currently shows alert — needs backend integration
- Consider adding structured data (JSON-LD) for SEO

---

## 🔗 Quick Links

- **GitHub Repo**: [github.com/Jupiterlaw/jupiters-design-limited-site-v2](https://github.com/Jupiterlaw/jupiters-design-limited-site-v2)
- **Deployment Guide**: [Workflow.md](./Workflow.md)
- **Cloudflare Dashboard**: [dash.cloudflare.com](https://dash.cloudflare.com/)
- **Live Site** (pending): [www.jupitersdesign.com](https://www.jupitersdesign.com)

---

**Next Immediate Action**: Follow `Workflow.md` Phase 3 to connect repository to Cloudflare Pages.
