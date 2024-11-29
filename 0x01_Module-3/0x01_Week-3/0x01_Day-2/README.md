
# Day 2: Progressive Web Apps (PWAs)

---

## Outline

1. **What Are Progressive Web Apps (PWAs)?**
2. **Core Features of PWAs**
3. **Service Workers**
4. **The Web App Manifest**
5. **Building Your First PWA Using Next.js**
6. **Testing and Deploying a PWA**

---

## 1. What Are Progressive Web Apps (PWAs)?

Progressive Web Apps (PWAs) combine the best features of web and native applications. They deliver reliable, fast, and engaging experiences across devices.

---

## 2. Core Features of PWAs

1. **Reliable**:
   - Load instantly, even in uncertain network conditions.
   - Achieved through caching with service workers.

2. **Fast**:
   - Ensure smooth interactions and fast load times.
   - Focus on performance optimization techniques.

3. **Engaging**:
   - Provide app-like experiences with push notifications, offline support, and add-to-home-screen functionality.

---

## 3. Service Workers

### What Is a Service Worker?
A service worker is a script that runs in the background of a web app, separate from the main browser thread. It enables features like:
- Caching resources.
- Offline access.
- Push notifications.

### Key Events:
1. **Install**: Triggered when the service worker is installed.
2. **Activate**: Triggered after installation, when the service worker is activated.
3. **Fetch**: Intercepts and handles network requests.

### Example:
```javascript
self.addEventListener('install', (event) => {
  console.log('Service Worker Installed');
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
```

---

## 4. The Web App Manifest

### What Is a Web App Manifest?
The manifest is a JSON file that provides metadata about your PWA, like its name, icons, and theme.

### Example:
`manifest.json`:
```json
{
  "name": "My PWA",
  "short_name": "PWA",
  "icons": [
    {
      "src": "/icon.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ],
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff"
}
```

---

## 5. Building Your First PWA Using Next.js

### Steps:
1. Install the `next-pwa` package:
   ```bash
   npm install next-pwa
   ```

2. Create a `next.config.js` file:
   ```javascript
   const withPWA = require('next-pwa')({
     dest: 'public',
   });

   module.exports = withPWA({
     // Next.js config
   });
   ```

3. Add a `manifest.json` file and an icon in the `public` folder.

4. Register the service worker:
   - Next.js will handle this automatically via the `next-pwa` package.

---

## 6. Testing and Deploying a PWA

### Testing:
- Use **Lighthouse** in Chrome DevTools to check PWA compliance.

### Deployment:
- Deploy the app to Vercel or Netlify.
- Ensure HTTPS is enabled (required for PWAs).

---

## Resources
- [What are PWAs?](https://web.dev/what-are-pwas/)
- [Service Workers](https://developers.google.com/web/fundamentals/primers/service-workers)
- [Web App Manifest Guide](https://developer.mozilla.org/en-US/docs/Web/Manifest)
- [Next.js PWA Documentation](https://github.com/shadowwalker/next-pwa)
```

---
