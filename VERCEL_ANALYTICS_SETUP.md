# Vercel Web Analytics Setup Guide

This document explains how Vercel Web Analytics has been configured for this static HTML website.

## What Was Implemented

Vercel Web Analytics tracking code has been added to all main HTML pages in this project:

- `index.html` (Homepage)
- `about-us/index.html`
- `contact-us/index.html`
- `commercial/index.html`
- `residential/index.html`
- `gallery/index.html`
- `installation/index.html`

## Analytics Code Added

The following code snippet was added to the `<head>` section of each page, just before the closing `</head>` tag:

```html
<!-- Vercel Web Analytics -->
<script>
  window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

## How It Works

For static HTML sites deployed on Vercel:

1. **Automatic Injection**: Once you enable Web Analytics in your Vercel dashboard, Vercel automatically serves the analytics script from `/_vercel/insights/script.js`

2. **Queue System**: The inline script creates a queue (`window.vaq`) to collect analytics events before the main script loads

3. **Deferred Loading**: The script loads asynchronously (`defer` attribute) to avoid blocking page rendering

## Enabling Analytics

To activate analytics for this project:

1. **Go to Vercel Dashboard**: Navigate to your project settings at vercel.com

2. **Enable Analytics**: 
   - Click on the "Analytics" tab
   - Select your project
   - Click the "Enable" button in the header

3. **Deploy**: The analytics will become active after your next deployment

## Verification

After deployment, verify analytics is working:

1. Visit your deployed website
2. Open browser DevTools (F12)
3. Go to the Network tab
4. Look for requests to `/_vercel/insights/*` endpoints
5. Check for a POST request to the analytics endpoint when navigating pages

## Viewing Analytics Data

Once enabled and deployed:

1. Go to your Vercel dashboard
2. Select your project
3. Navigate to the Analytics tab
4. View real-time and historical traffic data including:
   - Page views
   - Unique visitors
   - Top pages
   - Traffic sources
   - Geographic distribution

## Technical Details

- **Framework**: Static HTML (no build process required)
- **Integration Type**: Manual script tag injection
- **Privacy**: Vercel Web Analytics is privacy-friendly and doesn't use cookies
- **Performance**: Script is served from Vercel's edge network for optimal loading speed

## Additional Resources

- [Vercel Web Analytics Documentation](https://vercel.com/docs/analytics)
- [Vercel Analytics Quickstart](https://vercel.com/docs/analytics/quickstart)
- [Privacy & Compliance](https://vercel.com/docs/analytics/privacy-policy)

## Notes

- The analytics script path `/_vercel/insights/script.js` is standard for Vercel projects
- Analytics data appears in the dashboard within minutes of deployment
- No additional configuration or API keys are required
- The tracking is automatic once enabled in the dashboard
