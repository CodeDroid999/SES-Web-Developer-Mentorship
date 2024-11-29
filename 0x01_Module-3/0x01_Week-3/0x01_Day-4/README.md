Here’s the content for **`SES-Web-Developer-Mentorship/0x01_Module-3/0x02_Week-3/day-4`**.

---

# Day 4: Progressive Web Apps (PWAs) - Best Practices and APIs

---

## Outline

1. **What Are PWAs?**
   - Characteristics of PWAs
   - Why PWAs matter
2. **Key APIs for PWAs**
   - Payment Request API
   - Geolocation API
   - Notifications API
3. **Designing for PWAs**
   - PRPL Pattern
   - RAIL Model
   - Optimizing Performance
4. **Hands-On: Adding Advanced PWA Features**
5. **Testing PWAs with Lighthouse**

---

## 1. What Are PWAs?

**Progressive Web Apps (PWAs)** are web applications that use modern web capabilities to deliver an app-like experience to users. They are reliable, fast, and engaging.

**Key Characteristics of PWAs:**
- Offline functionality
- Installable on devices
- Fast and responsive
- Secure (served over HTTPS)

---

## 2. Key APIs for PWAs

### **Payment Request API**
Streamline the checkout process for users by integrating browser-based payment interfaces.

Example:
```javascript
const paymentRequest = new PaymentRequest(
  [{ supportedMethods: 'basic-card' }],
  {
    total: { label: 'Total', amount: { currency: 'USD', value: '10.00' } },
  }
);

paymentRequest.show().then((paymentResponse) => {
  console.log(paymentResponse);
  paymentResponse.complete('success');
});
```

### **Geolocation API**
Enable location-based features in your app.

Example:
```javascript
navigator.geolocation.getCurrentPosition((position) => {
  console.log(`Latitude: ${position.coords.latitude}`);
  console.log(`Longitude: ${position.coords.longitude}`);
});
```

### **Notifications API**
Display system-level notifications to engage users.

Example:
```javascript
if ('Notification' in window) {
  Notification.requestPermission().then((permission) => {
    if (permission === 'granted') {
      new Notification('Hello! You’ve got a new message.');
    }
  });
}
```

---

## 3. Designing for PWAs

### **PRPL Pattern**
- **Push** critical resources.
- **Render** initial route.
- **Pre-cache** assets for offline use.
- **Lazy-load** resources.

### **RAIL Model**
Focuses on optimizing performance for:
- **Response** (e.g., tapping or scrolling)
- **Animation** (e.g., smooth transitions)
- **Idle time** (e.g., background tasks)
- **Load time** (e.g., first contentful paint)

### Optimizing Performance
- Minify JavaScript, CSS, and images.
- Use code-splitting and lazy-loading.
- Preload critical assets.

---

## 4. Hands-On: Adding Advanced PWA Features

1. Add **Payment Request API** to your app.
2. Integrate **Geolocation** to show user location.
3. Add **Notifications** to notify users of app updates.

---

## 5. Testing PWAs with Lighthouse

1. Run Lighthouse in Chrome DevTools.
2. Analyze:
   - PWA checklist
   - Performance metrics
   - Accessibility improvements

---

## Resources

- [Progressive Web Apps (MDN)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps)
- [Payment Request API](https://developer.mozilla.org/en-US/docs/Web/API/Payment_Request_API)
- [Geolocation API](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)
- [Notifications API](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API)
- [Lighthouse](https://web.dev/measure/)
```

---
