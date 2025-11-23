# 🚀 Hướng Dẫn Deploy Lên Vercel

## 📋 Yêu Cầu

- Tài khoản GitHub
- Tài khoản Vercel (free tier)
- Git đã cài đặt trên máy

---

## 🎯 Phương Pháp 1: Deploy Trực Tiếp Từ GitHub (Khuyến Nghị)

### Bước 1: Push Code Lên GitHub

```bash
# 1. Khởi tạo git repository (nếu chưa có)
git init

# 2. Add tất cả files
git add .

# 3. Commit
git commit -m "feat: complete ISTQB Foundation curriculum"

# 4. Add remote repository
git remote add origin https://github.com/your-username/istqb-foundation.git

# 5. Push lên GitHub
git branch -M main
git push -u origin main
```

### Bước 2: Import Project Từ GitHub Vào Vercel

1. **Truy cập Vercel**: https://vercel.com
2. **Đăng nhập** bằng tài khoản GitHub
3. **Click "Add New..."** → **Project**
4. **Import Git Repository**:
   - Chọn repository `istqb-foundation`
   - Click **Import**

5. **Configure Project**:
   ```
   Framework Preset: Other
   Build Command: npm run build
   Output Directory: _book
   Install Command: npm install
   ```

6. **Click Deploy** 🚀

### Bước 3: Đợi Deploy Hoàn Thành

- Vercel sẽ tự động:
  - Install dependencies (`npm install`)
  - Build GitBook (`npm run build`)
  - Deploy static site
- Thời gian: 2-5 phút

### Bước 4: Truy Cập Website

Vercel sẽ cung cấp URL:
- **Production**: `https://istqb-foundation.vercel.app`
- **Custom Domain** (optional): Thêm domain của bạn

---

## 🎯 Phương Pháp 2: Deploy Bằng Vercel CLI

### Bước 1: Cài Đặt Vercel CLI

```bash
npm install -g vercel
```

### Bước 2: Login Vào Vercel

```bash
vercel login
```

### Bước 3: Deploy

```bash
# Deploy lần đầu
vercel

# Vercel sẽ hỏi:
# Set up and deploy "~/istqb-foundation"? [Y/n] → y
# Which scope? → Chọn account của bạn
# Link to existing project? [y/N] → n
# What's your project's name? → istqb-foundation
# In which directory is your code located? → ./
# Want to override the settings? [y/N] → y

# Override settings:
# Build Command: npm run build
# Output Directory: _book
# Development Command: npm run dev
```

### Bước 4: Deploy Production

```bash
vercel --prod
```

---

## ⚙️ Configuration Files Giải Thích

### `vercel.json`

```json
{
  "version": 2,
  "buildCommand": "npm run build",
  "outputDirectory": "_book",
  "framework": null
}
```

- **buildCommand**: Lệnh build GitBook
- **outputDirectory**: Thư mục chứa static files sau khi build
- **framework**: null (không dùng framework cụ thể)

### `package.json`

```json
{
  "scripts": {
    "dev": "honkit serve",      // Development server
    "build": "honkit build",    // Build static site
    "clean": "rm -rf _book"     // Clean build folder
  }
}
```

### `book.json`

Cấu hình GitBook plugins và theme:
- `search-plus`: Tìm kiếm nâng cao
- `github`: Link đến GitHub repo
- `copy-code-button`: Copy code dễ dàng
- `prism`: Syntax highlighting

---

## 🔧 Troubleshooting

### Lỗi: "Build failed"

**Nguyên nhân**: Dependencies không được install đúng

**Giải pháp**:
```bash
# Clean và rebuild locally
rm -rf node_modules _book
npm install
npm run build

# Nếu build local thành công → commit và push lại
git add .
git commit -m "fix: rebuild dependencies"
git push
```

### Lỗi: "404 Not Found" trên Vercel

**Nguyên nhân**: Output directory không đúng

**Giải pháp**:
1. Check `vercel.json` → `outputDirectory` phải là `_book`
2. Check `package.json` → `build` script phải tạo folder `_book`

### Lỗi: "Module not found: honkit"

**Nguyên nhân**: Honkit chưa được install

**Giải pháp**:
```bash
npm install honkit --save-dev
```

### Build Timeout trên Vercel

**Nguyên nhân**: Project quá lớn, build lâu

**Giải pháp**:
1. Upgrade Vercel plan (nếu cần)
2. Optimize build:
   ```json
   // book.json
   {
     "plugins": [
       // Giảm số lượng plugins
       "search-plus",
       "github"
     ]
   }
   ```

---

## 🌐 Custom Domain Setup

### Bước 1: Mua Domain

Mua domain tại:
- **Namecheap**: https://namecheap.com
- **GoDaddy**: https://godaddy.com
- **Google Domains**: https://domains.google

### Bước 2: Add Domain Vào Vercel

1. Truy cập Vercel Dashboard
2. Chọn project **istqb-foundation**
3. **Settings** → **Domains**
4. **Add Domain**: `your-domain.com`

### Bước 3: Configure DNS

**Option A: Vercel Nameservers (Khuyến nghị)**
```
ns1.vercel-dns.com
ns2.vercel-dns.com
```

**Option B: CNAME Record**
```
Type: CNAME
Name: @
Value: cname.vercel-dns.com
```

### Bước 4: Verify Domain

- Vercel sẽ tự động verify
- SSL certificate tự động được cấp (Let's Encrypt)
- Thời gian: 10-30 phút

---

## 🔄 Auto Deploy on Push

Vercel tự động deploy khi:
- ✅ Push lên `main` branch → Production deploy
- ✅ Push lên branch khác → Preview deploy
- ✅ Pull Request → Preview deploy với unique URL

### Preview Deployment

Mỗi PR sẽ có unique URL:
```
https://istqb-foundation-git-feature-branch.vercel.app
```

---

## 📊 Monitoring & Analytics

### Vercel Dashboard

1. **Analytics**: Xem traffic, page views
2. **Logs**: Check build logs và runtime logs
3. **Speed Insights**: Đo performance

### Setup Analytics

```json
// vercel.json
{
  "analytics": {
    "enable": true
  }
}
```

---

## 🎉 Sau Khi Deploy Thành Công

Website của bạn đã live tại:
- **Vercel URL**: `https://istqb-foundation.vercel.app`
- **Custom Domain** (nếu có): `https://your-domain.com`

### Chia Sẻ Với Cộng Đồng

Share link đến:
- Facebook groups: "ISTQB Vietnam", "Software Testing Vietnam"
- LinkedIn
- GitHub README.md

### Update Nội Dung

```bash
# 1. Chỉnh sửa files markdown
vim giai-doan-1-nen-tang/module-1.1-testing-la-gi.md

# 2. Commit và push
git add .
git commit -m "docs: update module 1.1"
git push

# 3. Vercel tự động deploy (1-2 phút)
```

---

## 🆘 Support

**Gặp vấn đề?**
- Vercel Docs: https://vercel.com/docs
- Honkit Docs: https://github.com/honkit/honkit
- Issues: https://github.com/your-username/istqb-foundation/issues

---

**Chúc mừng! Website ISTQB của bạn đã online! 🎊**
