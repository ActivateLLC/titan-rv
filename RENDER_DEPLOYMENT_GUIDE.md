# TITAN RV Render Deployment Guide

This guide walks through the process of deploying the TITAN RV static website to Render.com.

## Prerequisites

- A GitHub account with access to the TITAN RV repository
- A Render.com account (free tier works for static sites)
- Ownership of the `titanrv.com` domain (for custom domain setup)

## Deployment Steps

### 1. Sign in to Render

Go to [https://dashboard.render.com](https://dashboard.render.com) and sign in to your account.

### 2. Create a New Static Site

1. Click the "New +" button in the top right corner
2. Select "Static Site" from the dropdown menu

### 3. Connect Your Repository

1. Connect your GitHub account if you haven't already
2. Select the "ActivateLLC/titan-rv" repository from the list
3. If you don't see the repository, you might need to configure permissions in GitHub

### 4. Configure Your Static Site

Enter the following settings:

- **Name**: `titan-rv` (or your preferred name)
- **Branch**: `main` (or your primary branch)
- **Root Directory**: Leave blank (use repository root)
- **Build Command**: Leave blank (no build step required)
- **Publish Directory**: `.` (the root directory)

### 5. Set Environment Variables (Optional)

No environment variables are required for this basic static site.

### 6. Deploy the Site

Click "Create Static Site" to deploy your site. Render will automatically build and deploy your static site.

## Custom Domain Setup

### 1. Add Your Custom Domain on Render

1. Once your site is deployed, go to the "Settings" tab
2. Scroll down to the "Custom Domain" section
3. Click "Add Custom Domain"
4. Enter your domain: `titanrv.com`
5. Follow the verification steps provided by Render

### 2. Update DNS Records

You'll need to update your DNS records at your domain registrar:

1. Create a CNAME record:
   - Name: `www` (or `@` for root domain)
   - Value: Your Render URL (e.g., `titan-rv.onrender.com`)
   - TTL: 3600 (or as recommended)

2. If using the root domain (`titanrv.com` without www):
   - Create an ALIAS or ANAME record pointing to your Render URL
   - Or use your registrar's domain forwarding to point to the www version

### 3. Wait for DNS Propagation

DNS changes may take up to 48 hours to propagate globally, though often it's much faster.

## Verify Deployment

1. Visit your Render URL (e.g., `https://titan-rv.onrender.com`) to verify the site is working correctly
2. Once DNS propagation is complete, visit your custom domain (`https://titanrv.com`) to verify it's correctly linked

## Troubleshooting

If you encounter any issues:

1. Check the Render logs by going to the "Logs" tab in your Render dashboard
2. Verify your DNS settings at your domain registrar
3. Ensure the CNAME file in your GitHub repository contains the correct domain
4. Check that your DNS records are correctly configured

## Maintaining Your Site

Any changes pushed to the main branch of your GitHub repository will trigger an automatic deployment on Render. The process typically takes less than a minute for simple static sites.

## Next Steps

Consider setting up:

1. HTTPS for your custom domain (Render handles this automatically)
2. Custom routing rules in the "Redirects/Rewrites" tab
3. Cache control headers for improved performance

For more information, consult the [Render documentation](https://render.com/docs/static-sites).