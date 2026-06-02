# CYBER NAV - Neural Network Navigation System

[English Doc](./Readme-en.md)

A cyberpunk-style web navigation portal built with HTML + CSS + JavaScript. Futuristic interface design with neon aesthetics, perfect for accessing essential tools and resources in the digital frontier.

## Features

- Pure static HTML pages, no backend required
- Responsive design, mobile-friendly
- Cyberpunk visual theme with neon accents
- Neural search with multiple search engines
- Organized category navigation
- Website submission functionality
- Easy deployment, multiple deployment options

## Live Preview

- GitHub Pages: https://kukutete1111.github.io/web_tool/

## Quick Start

### Local Preview

1. Clone the project
```bash
git clone https://github.com/kukutete1111/web_tool.git
cd web_tool
```

2. Run with any HTTP server
```bash
# Python 3
python -m http.server 8000

# Node.js (requires http-server)
npx http-server -p 8000

# Or open index.html directly in browser
```

3. Visit `http://localhost:8000`

## Deployment Guide

### Option 1: Nginx Deployment

#### 1. Preparation

Ensure Nginx is installed:

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install nginx

# CentOS/RHEL
sudo yum install nginx
```

#### 2. Upload Files

```bash
sudo mkdir -p /var/www/web_tool
scp -r ./* user@your-server:/var/www/web_tool/
```

#### 3. Configure Nginx

```bash
sudo vim /etc/nginx/sites-available/web_tool
```

Add configuration:

```nginx
server {
    listen 80;
    server_name your-domain.com;

    root /var/www/web_tool;
    index index.html;

    gzip on;
    gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

    location / {
        try_files $uri $uri/ /index.html;
    }

    location ~* \.(jpg|jpeg|png|gif|ico|css|js|svg|woff|woff2|ttf|eot)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }

    error_page 404 /404.html;
    location = /404.html {
        internal;
    }
}
```

#### 4. Enable Site

```bash
sudo ln -s /etc/nginx/sites-available/web_tool /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
sudo systemctl enable nginx
```

#### 5. HTTPS (Recommended)

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d your-domain.com
sudo certbot renew --dry-run
```

### Option 2: Vercel Deployment (Recommended)

#### Method 1: Vercel Dashboard

1. Visit [Vercel](https://vercel.com) and sign in
2. Click "Add New Project"
3. Import your GitHub repository
4. Framework Preset: "Other"
5. Click "Deploy"

#### Method 2: Vercel CLI

```bash
npm install -g vercel
vercel login
cd web_tool
vercel
vercel --prod
```

### Option 3: Other Platforms

#### GitHub Pages
1. Enable Pages in repository settings
2. Select branch and directory

#### Cloudflare Pages
1. Login to Cloudflare Dashboard
2. Create new Pages project
3. Connect GitHub repository
4. Deploy

#### Netlify
1. Login to Netlify
2. "Add new site" -> "Import an existing project"
3. Select Git repository
4. Click "Deploy site"

## Development

### Modify Navigation Content

Edit `index.html`, find the URL card sections:

```html
<div class="url-card col-6 col-sm-6 col-md-4 col-xl-5a col-xxl-6a">
    <a href="https://your-website.com" target="_blank" class="card no-c mb-4">
        <div class="card-body">
            <div class="url-content d-flex align-items-center">
                <img src="assets/images/logos/logo.png" alt="Site Name">
                <div class="url-info flex-fill">
                    <strong>Site Name</strong>
                    <p>Site description</p>
                </div>
            </div>
        </div>
    </a>
</div>
```

### Customize Styles

Main CSS files in `assets/css/`:
- `custom-style.css` - Custom styles
- `style-3.03029.1.css` - Theme styles

### Add New Categories

Add new category sections in `index.html`:

```html
<div class="d-flex flex-fill">
    <h4 class="text-gray text-lg mb-4">
        <i class="site-tag iconfont icon-tag icon-lg mr-1" id="category-id"></i>
        Category Name
    </h4>
</div>
<div class="row">
    <!-- URL cards -->
</div>
```

## Project Structure

```
web_tool/
├── index.html              # Main page
├── commit.html             # Submit page
├── 404.html               # 404 page
├── about/
│   └── index.html         # About page
├── assets/
│   ├── css/               # Stylesheets
│   ├── js/                # JavaScript
│   ├── images/            # Images
│   └── fontawesome-5.15.4/ # Icons
├── README.md              # Documentation
└── vercel.json            # Vercel config
```

## FAQ

### 1. Resource Loading Issues
Check relative paths in HTML files.

### 2. Website Submission Backend
Currently stores in localStorage. For persistent storage:
- Use Vercel Serverless Functions
- Configure backend API
- Use third-party form services

### 3. Analytics
Integrated with 51.la analytics.

### 4. SEO Optimization
- Improve meta tags
- Add sitemap.xml
- Submit to search engines

## Tech Stack

- HTML5
- CSS3
- JavaScript (jQuery)
- Bootstrap 4
- Font Awesome 5

## License

MIT License

## Contributing

Feel free to submit Issues and Pull Requests!

---

⚡ Welcome to the Cyber Frontier!