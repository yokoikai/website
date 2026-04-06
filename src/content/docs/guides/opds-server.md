---
title: Configure the OPDS Server
description: Read your Yokoi library on any OPDS-compatible app using the built-in OPDS feed.
draft: false
---

Yokoi exposes an [OPDS](https://opds.io) (Open Publication Distribution System) feed so you can browse and download your books directly from any OPDS-compatible reading app.

## Feed URL

```
https://api.yokoi.app/opds
```

## Authentication

The OPDS feed uses **HTTP Basic authentication** with your Yokoi credentials:

- **Username**: your Yokoi account email
- **Password**: your Yokoi account password

Authentication is required to access the catalog. Most OPDS clients will prompt you for these when you add the feed URL.

## What's available

| Content | Visibility |
|---|---|
| Published books | Requires authentication |
| Your unpublished manuscripts | Requires authentication |

## Connecting your reading app

### KOReader

1. Open the **Search** menu → **OPDS catalog**
2. Tap the **+** button to add a catalog
3. Enter the catalog URL: `https://api.yokoi.app/opds`
4. Enter your Yokoi email and password when prompted
5. Browse and download books directly to your device

### Calibre

1. Open **Preferences → Sharing → OPDS Server** (to check your Calibre server) — or use the **Get Books** plugin
2. In the **Get Books** plugin, add a new store with the URL `https://api.yokoi.app/opds`
3. Enter your credentials when prompted

### Panels (iOS)

1. Tap **+** → **Add OPDS Catalog**
2. Enter `https://api.yokoi.app/opds` as the URL
3. Enter your Yokoi email and password
4. Your library will appear in the catalog browser

### Moon+ Reader / Lithium (Android)

1. Open the **Network** or **Catalogs** section
2. Add a new OPDS catalog with URL `https://api.yokoi.app/opds`
3. Enter your credentials when prompted

### Other apps

Any app that supports OPDS 1.x will work. Use the feed URL `https://api.yokoi.app/opds` with HTTP Basic auth.

## Supported formats

Books are available for download in **EPUB** and **PDF** formats.
