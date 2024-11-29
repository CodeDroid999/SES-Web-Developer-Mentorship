# Day 5: Progressive Web Apps (PWA) Fundamentals

---

## Outline

1. **What Are Progressive Web Apps (PWAs)?**
2. **Core Features of PWAs**
3. **Service Workers**
4. **Web App Manifest**
5. **Caching Strategies**
6. **Implementing Offline Mode**
7. **Testing and Debugging PWAs**

---

## 1. What Are Progressive Web Apps (PWAs)?

### Definition
Progressive Web Apps are web applications that use modern web capabilities to deliver an app-like experience to users. They are reliable, fast, and engaging.

### Key Characteristics:
- **Reliable**: Work offline or with poor network conditions.
- **Fast**: Provide quick load times and smooth interactions.
- **Engaging**: Feel like a native app with immersive user experiences.

---

## 2. Core Features of PWAs

### Features:
1. **Installable**: Can be added to the home screen.
2. **Offline Support**: Work without internet using caching.
3. **Push Notifications**: Engage users with timely updates.
4. **App-Like Feel**: Mimics native app UX.
5. **Cross-Platform**: Works on all devices and browsers.

---

## 3. Service Workers

### What Are Service Workers?
Service Workers are JavaScript files that run in the background, intercept network requests, and provide offline capabilities.

### Lifecycle:
1. **Install**: Triggered when the Service Worker is installed.
2. **Activate**: Ensures old caches are cleared.
3. **Fetch**: Intercepts requests and serves cached responses.

### Example:
```javascript
self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open('my-cache').then((cache) => {
      return cache.addAll(['/index.html', '/styles.css', '/script.js']);
    })
  );
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
