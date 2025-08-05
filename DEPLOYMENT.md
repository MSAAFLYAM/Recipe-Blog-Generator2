# Deployment Guide

This guide provides step-by-step instructions for deploying the Recipe Blog Generator to various platforms.

## 🚀 Quick Deployment Options

### Option 1: Vercel (Recommended - Free Tier Available)

Vercel offers the easiest deployment with automatic builds and global CDN.

#### Prerequisites
- GitHub account
- Vercel account (free)

#### Steps

1. **Push to GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/recipe-blog-generator.git
   git push -u origin main
   ```

2. **Deploy to Vercel**
   - Visit [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository
   - Vercel auto-detects Vite configuration
   - Click "Deploy"

3. **Configure Environment Variables** (Optional)
   - Go to Project Settings → Environment Variables
   - Add any API keys if needed:
     ```
     VITE_OPENAI_API_KEY=your_key_here
     VITE_REPLICATE_API_TOKEN=your_token_here
     ```

4. **Custom Domain** (Optional)
   - Go to Project Settings → Domains
   - Add your custom domain
   - Follow DNS configuration instructions

**Result**: Your app will be live at `https://your-project.vercel.app`

### Option 2: Netlify (Free Tier Available)

Netlify provides excellent static site hosting with form handling and serverless functions.

#### Prerequisites
- Netlify account (free)

#### Method A: Git Integration

1. **Connect Repository**
   - Visit [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Connect your GitHub repository

2. **Configure Build Settings**
   ```
   Build command: npm run build
   Publish directory: dist
   ```

3. **Deploy**
   - Click "Deploy site"
   - Netlify automatically builds and deploys

#### Method B: Manual Upload

1. **Build Locally**
   ```bash
   npm run build
   ```

2. **Upload to Netlify**
   - Visit [netlify.com](https://netlify.com)
   - Drag and drop the `dist` folder to the deploy area

**Result**: Your app will be live at `https://random-name.netlify.app`

### Option 3: GitHub Pages (Free)

Deploy directly from your GitHub repository.

#### Prerequisites
- GitHub repository

#### Steps

1. **Install gh-pages**
   ```bash
   npm install --save-dev gh-pages
   ```

2. **Update package.json**
   ```json
   {
     "homepage": "https://yourusername.github.io/recipe-blog-generator",
     "scripts": {
       "predeploy": "npm run build",
       "deploy": "gh-pages -d dist"
     }
   }
   ```

3. **Deploy**
   ```bash
   npm run deploy
   ```

4. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Select "gh-pages" branch as source

**Result**: Your app will be live at `https://yourusername.github.io/recipe-blog-generator`

## 🐳 Docker Deployment

For containerized deployment on any platform that supports Docker.

### Prerequisites
- Docker installed
- Docker Hub account (optional)

### Local Docker Deployment

1. **Build Image**
   ```bash
   docker build -t recipe-blog-generator .
   ```

2. **Run Container**
   ```bash
   docker run -p 3000:80 recipe-blog-generator
   ```

3. **Access Application**
   ```
   http://localhost:3000
   ```

### Docker Hub Deployment

1. **Tag Image**
   ```bash
   docker tag recipe-blog-generator yourusername/recipe-blog-generator:latest
   ```

2. **Push to Docker Hub**
   ```bash
   docker push yourusername/recipe-blog-generator:latest
   ```

3. **Deploy on Server**
   ```bash
   docker pull yourusername/recipe-blog-generator:latest
   docker run -d -p 80:80 yourusername/recipe-blog-generator:latest
   ```

## ☁️ Cloud Platform Deployment

### AWS S3 + CloudFront

1. **Build Application**
   ```bash
   npm run build
   ```

2. **Create S3 Bucket**
   - Enable static website hosting
   - Upload `dist` folder contents

3. **Configure CloudFront**
   - Create distribution pointing to S3 bucket
   - Configure custom error pages for SPA routing

### Google Cloud Storage

1. **Build Application**
   ```bash
   npm run build
   ```

2. **Create Storage Bucket**
   ```bash
   gsutil mb gs://your-bucket-name
   ```

3. **Upload Files**
   ```bash
   gsutil -m cp -r dist/* gs://your-bucket-name
   ```

4. **Enable Website Configuration**
   ```bash
   gsutil web set -m index.html -e index.html gs://your-bucket-name
   ```

### Azure Static Web Apps

1. **Create Static Web App**
   - Use Azure portal or CLI
   - Connect to GitHub repository

2. **Configure Build**
   ```yaml
   # .github/workflows/azure-static-web-apps.yml
   app_location: "/"
   api_location: ""
   output_location: "dist"
   ```

## 🔧 Advanced Configuration

### Environment Variables

For enhanced functionality, configure these environment variables:

```env
# OpenAI API for improved content generation
VITE_OPENAI_API_KEY=sk-...

# Replicate API for image generation
VITE_REPLICATE_API_TOKEN=r8_...

# Custom API endpoints
VITE_API_BASE_URL=https://your-api.com

# Analytics
VITE_GA_TRACKING_ID=G-...
```

### Custom Domain Setup

#### Vercel
1. Go to Project Settings → Domains
2. Add your domain
3. Configure DNS records as instructed

#### Netlify
1. Go to Site Settings → Domain management
2. Add custom domain
3. Configure DNS or use Netlify DNS

#### Cloudflare (Recommended for performance)
1. Add your domain to Cloudflare
2. Configure DNS to point to your hosting provider
3. Enable Cloudflare proxy for performance and security

### SSL/HTTPS Configuration

Most modern hosting platforms (Vercel, Netlify, GitHub Pages) provide automatic HTTPS. For custom deployments:

1. **Let's Encrypt** (Free)
   ```bash
   certbot --nginx -d yourdomain.com
   ```

2. **Cloudflare** (Free)
   - Enable "Always Use HTTPS" in SSL/TLS settings

## 📊 Performance Optimization

### Build Optimization

1. **Analyze Bundle Size**
   ```bash
   npm run build -- --analyze
   ```

2. **Enable Compression**
   - Gzip compression is configured in nginx.conf
   - Most hosting platforms enable this automatically

3. **Optimize Images**
   - Use WebP format when possible
   - Implement lazy loading for images

### CDN Configuration

1. **Vercel**: Automatic global CDN
2. **Netlify**: Automatic global CDN
3. **Custom**: Use Cloudflare or AWS CloudFront

## 🔍 Monitoring and Analytics

### Error Tracking

1. **Sentry Integration**
   ```bash
   npm install @sentry/react
   ```

2. **Configure in main.jsx**
   ```javascript
   import * as Sentry from "@sentry/react";
   
   Sentry.init({
     dsn: "YOUR_SENTRY_DSN",
   });
   ```

### Analytics

1. **Google Analytics**
   ```javascript
   // Add to index.html
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
   ```

2. **Plausible Analytics** (Privacy-friendly)
   ```javascript
   // Add to index.html
   <script defer data-domain="yourdomain.com" src="https://plausible.io/js/plausible.js"></script>
   ```

## 🛠️ Troubleshooting

### Common Issues

1. **Build Fails**
   - Check Node.js version (requires 18+)
   - Clear node_modules and reinstall: `rm -rf node_modules package-lock.json && npm install`

2. **Routing Issues on Deployment**
   - Configure server to serve index.html for all routes
   - Check nginx.conf for SPA routing configuration

3. **Environment Variables Not Working**
   - Ensure variables start with `VITE_`
   - Restart development server after adding variables

4. **Large Bundle Size**
   - Implement code splitting
   - Use dynamic imports for heavy components

### Performance Issues

1. **Slow Loading**
   - Enable compression (gzip/brotli)
   - Optimize images and assets
   - Use CDN for static assets

2. **Memory Issues**
   - Implement virtual scrolling for large lists
   - Use React.memo for expensive components
   - Optimize re-renders with useCallback/useMemo

## 📞 Support

If you encounter issues during deployment:

1. Check the [GitHub Issues](https://github.com/yourusername/recipe-blog-generator/issues)
2. Review platform-specific documentation
3. Contact support for your hosting platform

## 🔄 Continuous Deployment

### GitHub Actions (Recommended)

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Production

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        cache: 'npm'
    
    - name: Install dependencies
      run: npm ci
    
    - name: Build
      run: npm run build
    
    - name: Deploy to Vercel
      uses: vercel/action@v1
      with:
        vercel-token: ${{ secrets.VERCEL_TOKEN }}
        vercel-org-id: ${{ secrets.ORG_ID }}
        vercel-project-id: ${{ secrets.PROJECT_ID }}
```

This ensures automatic deployment whenever you push to the main branch.

---

**Happy Deploying! 🚀**

