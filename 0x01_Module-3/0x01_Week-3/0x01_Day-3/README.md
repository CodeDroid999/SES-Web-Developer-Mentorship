
# Day 3: Advanced Service Workers and Offline Strategies

---

## Outline

1. **Recap: Service Workers**
2. **Advanced Service Worker Features**
   - Handling Background Sync
   - Push Notifications
3. **Offline Strategies**
   - Cache-First
   - Network-First
   - Stale-While-Revalidate
4. **Hands-On: Building an Offline-Capable App**
5. **Testing and Debugging Service Workers**

---

## 1. Recap: Service Workers

Service workers enable offline access, caching, and background tasks. They act as a programmable proxy between the web app and the browser.

---

## 2. Advanced Service Worker Features

### **Background Sync**
Allows the app to retry failed operations when the network is restored.

Example:
```javascript
self.addEventListener('sync', (event) => {
  if (event.tag === 'sync-posts') {
    event.waitUntil(syncPosts());
  }
});

async function syncPosts() {
  const posts = await getPostsFromIndexedDB();
  for (let post of posts) {
    await fetch('/api/posts', {
      method: 'POST',
      body: JSON.stringify(post),
    });
  }
}
```

### **Push Notifications**
Send real-time notifications to users, even when the app is closed.

Example:
```javascript
self.addEventListener('push', (event) => {
  const data = event.data.json();
  event.waitUntil(
    self.registration.showNotification(data.title, {
      body: data.body,
      icon: '/icon.png',
    })
  );
});
```

---

## 3. Offline Strategies

### **Cache-First Strategy**
Use cached resources first, then fall back to the network if not available.
```javascript
self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
```

### **Network-First Strategy**
Try fetching from the network first, and use the cache as a fallback.
```javascript
self.addEventListener('fetch', (event) => {
  event.respondWith(
    fetch(event.request).catch(() => caches.match(event.request))
  );
});
```

### **Stale-While-Revalidate Strategy**
Serve from the cache, but update it in the background.
```javascript
self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.open('dynamic-cache').then((cache) => {
      return cache.match(event.request).then((response) => {
        const fetchPromise = fetch(event.request).then((networkResponse) => {
          cache.put(event.request, networkResponse.clone());
          return networkResponse;
        });
        return response || fetchPromise;
      });
    })
  );
});
```

---

## 4. Hands-On: Building an Offline-Capable App

1. Create a simple notes app.
2. Add offline support using the **Cache-First** strategy.
3. Enable background sync for saving notes offline and syncing them when the network is restored.

---

## 5. Testing and Debugging Service Workers

1. Use Chrome DevTools:
   - Application Tab > Service Workers
   - Test offline mode and background sync.

2. Use Lighthouse to evaluate offline readiness.

---

## Resources
- [Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
- [Background Sync API](https://web.dev/background-sync/)
- [Push API](https://web.dev/push-notifications-overview/)
- [Offline Strategies](https://web.dev/offline-cookbook/)
- [Testing Service Workers](https://developer.chrome.com/docs/devtools/progressive-web-apps/)
```

---
