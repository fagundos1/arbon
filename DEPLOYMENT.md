# Deployment Guide for TherapyLogy Website

This guide will help you deploy the TherapyLogy website to various hosting platforms.

## 🚀 Quick Deployment Options

### 1. Netlify (Recommended for beginners)
1. Go to [netlify.com](https://netlify.com)
2. Sign up/Login with your GitHub account
3. Click "New site from Git"
4. Choose your repository
5. Deploy settings:
   - Build command: (leave empty - static site)
   - Publish directory: `.` (root directory)
6. Click "Deploy site"
7. Your site will be live at `https://your-site-name.netlify.app`

### 2. Vercel
1. Go to [vercel.com](https://vercel.com)
2. Sign up/Login with your GitHub account
3. Click "New Project"
4. Import your repository
5. Deploy settings:
   - Framework Preset: Other
   - Build Command: (leave empty)
   - Output Directory: `.`
6. Click "Deploy"
7. Your site will be live at `https://your-project.vercel.app`

### 3. GitHub Pages
1. Go to your GitHub repository
2. Click "Settings"
3. Scroll to "Pages" section
4. Source: "Deploy from a branch"
5. Branch: `main` or `master`
6. Folder: `/ (root)`
7. Click "Save"
8. Your site will be live at `https://username.github.io/repository-name`

## 🌐 Custom Domain Setup

### For therapylogy.com:
1. **Purchase Domain**: Buy `therapylogy.com` from a registrar (Namecheap, GoDaddy, etc.)
2. **DNS Configuration**: Point your domain to your hosting provider
3. **SSL Certificate**: Most hosting providers offer free SSL
4. **Update URLs**: Replace placeholder URLs in the code

### DNS Records Example:
```
Type    Name               Value
A       @                  75.2.60.5 (Netlify IP)
CNAME   www               your-site.netlify.app
```

## 📱 App Store Badges

### Current Placeholders:
The website currently uses placeholder images for app store badges. Replace these with official badges:

1. **App Store Badge**: Download from [Apple Marketing Guidelines](https://developer.apple.com/app-store/marketing/guidelines/)
2. **Google Play Badge**: Download from [Google Play Brand Guidelines](https://play.google.com/intl/en_us/badges/)

### Update HTML:
```html
<!-- Replace these placeholder images -->
<img src="assets/app-store-badge.png" alt="Download on App Store">
<img src="assets/google-play-badge.png" alt="Get it on Google Play">
```

## 🖼️ Image Assets

### Current Placeholders:
The website uses HTML files as image placeholders. For production:

1. **Convert to Images**: Use browser dev tools to screenshot the HTML placeholders
2. **Optimize Images**: Compress using tools like TinyPNG or ImageOptim
3. **Replace References**: Update HTML to use actual image files

### Required Images:
- `assets/hero-app.png` - App mockup for hero section
- `assets/about-image.png` - Team/about section image
- `assets/screenshot-1.png` - App screenshot 1
- `assets/screenshot-2.png` - App screenshot 2
- `assets/screenshot-3.png` - App screenshot 3
- `assets/app-store-badge.png` - Official App Store badge
- `assets/google-play-badge.png` - Official Google Play badge

## 🔧 Environment Configuration

### Contact Form:
The contact form currently shows success messages. For production:

1. **Backend Integration**: Connect to a service like:
   - Netlify Forms (free)
   - Formspree (free tier available)
   - EmailJS (free tier available)

2. **Update JavaScript**:
```javascript
// Replace the simulated form submission with real API calls
const response = await fetch('/api/contact', {
    method: 'POST',
    body: formData
});
```

### Analytics:
Add Google Analytics or other tracking:

```html
<!-- Add to <head> section -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## 📊 Performance Optimization

### Before Deployment:
1. **Minify CSS**: Use tools like CSSNano
2. **Minify JavaScript**: Use tools like Terser
3. **Optimize Images**: Compress and use WebP format
4. **Enable Gzip**: Most hosting providers do this automatically

### Tools:
```bash
# Install optimization tools
npm install -g cssnano-cli terser

# Minify CSS
cssnano styles.css styles.min.css

# Minify JavaScript
terser script.js -o script.min.js
```

## 🔒 Security Considerations

### HTTPS:
- Ensure SSL certificate is enabled
- Redirect HTTP to HTTPS
- Use secure headers

### Content Security Policy:
Add to your HTML:
```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline' https://cdnjs.cloudflare.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com;">
```

## 📈 SEO Optimization

### Meta Tags:
The website includes basic meta tags. Consider adding:

```html
<!-- Open Graph tags -->
<meta property="og:title" content="TherapyLogy - Your Mental Health Companion">
<meta property="og:description" content="Professional mental health support app with therapy, tools, and community.">
<meta property="og:image" content="https://therapylogy.com/assets/og-image.png">
<meta property="og:url" content="https://therapylogy.com">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="TherapyLogy - Your Mental Health Companion">
<meta name="twitter:description" content="Professional mental health support app with therapy, tools, and community.">
<meta name="twitter:image" content="https://therapylogy.com/assets/twitter-image.png">
```

### Sitemap:
Create a `sitemap.xml` file:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://therapylogy.com/</loc>
    <lastmod>2024-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

## 🧪 Testing

### Before Deployment:
1. **Cross-browser Testing**: Test on Chrome, Firefox, Safari, Edge
2. **Mobile Testing**: Test on various screen sizes
3. **Performance Testing**: Use Google PageSpeed Insights
4. **Accessibility Testing**: Use tools like axe or WAVE

### Post-Deployment:
1. **Check Console**: Ensure no JavaScript errors
2. **Test Forms**: Verify contact form works
3. **Check Links**: Ensure all navigation works
4. **Mobile Experience**: Test on actual devices

## 🆘 Troubleshooting

### Common Issues:

1. **Images Not Loading**:
   - Check file paths
   - Ensure images are in correct directory
   - Verify file permissions

2. **CSS Not Loading**:
   - Check file path in HTML
   - Verify CSS file exists
   - Check browser console for errors

3. **JavaScript Errors**:
   - Open browser console (F12)
   - Look for error messages
   - Check file paths and syntax

4. **Mobile Menu Not Working**:
   - Ensure JavaScript file is loaded
   - Check for CSS conflicts
   - Verify event listeners are attached

## 📞 Support

For deployment issues:
- **Email**: hello@therapylogy.com
- **Company**: ARBON LLC
- **Documentation**: Check hosting provider docs

---

**Happy Deploying! 🚀**

*TherapyLogy - Making mental health support accessible to everyone.*
