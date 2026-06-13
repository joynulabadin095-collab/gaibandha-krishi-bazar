# 🌾 গাইবান্ধা কৃষি বাজার

## ধাপে ধাপে deploy করার নির্দেশিকা

---

## ধাপ ১ — Firebase Setup (বিনামূল্যে)

1. https://console.firebase.google.com যাও
2. **"Create a project"** চাপো
3. Project name: `gaibandha-krishi-bazar`
4. Google Analytics: বন্ধ রাখো → **Create project**
5. বাম মেনু থেকে **Firestore Database** → **Create database**
6. **"Start in test mode"** বেছে নাও → Next → Enable
7. উপরে ⚙️ **Project settings** → **"Your apps"** → `</>` (Web) চাপো
8. App nickname: `krishi-web` → **Register app**
9. নিচে `firebaseConfig` এর values কপি করো

---

## ধাপ ২ — Firebase Config বসাও

`src/firebase.js` ফাইল খোলো এবং তোমার values বসাও:

```js
const firebaseConfig = {
  apiKey: "এখানে তোমার apiKey",
  authDomain: "এখানে তোমার authDomain",
  projectId: "এখানে তোমার projectId",
  storageBucket: "এখানে তোমার storageBucket",
  messagingSenderId: "এখানে তোমার messagingSenderId",
  appId: "এখানে তোমার appId"
};
```

---

## ধাপ ৩ — GitHub এ upload করো

1. https://github.com যাও → **New repository**
2. Repository name: `gaibandha-krishi-bazar`
3. Public রাখো → **Create repository**
4. এই সব files upload করো:
   - `index.html`
   - `package.json`
   - `vite.config.js`
   - `src/` ফোল্ডার (App.jsx, main.jsx, firebase.js)

**GitHub Desktop দিয়ে সহজে করতে পারো:**
- https://desktop.github.com থেকে download করো
- File → Add Local Repository → এই folder টা বেছে নাও
- Commit → Push

---

## ধাপ ৪ — Vercel এ Deploy করো

1. https://vercel.com যাও
2. **"Continue with GitHub"** দিয়ে login করো
3. **"New Project"** → তোমার repository বেছে নাও
4. Framework: **Vite** (auto detect হবে)
5. **Deploy** চাপো
6. ২-৩ মিনিট পর live link পাবে! 🎉

---

## ধাপ ৫ — Firestore Security Rules (গুরুত্বপূর্ণ!)

Firebase Console → Firestore → **Rules** tab → এই rules বসাও:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /products/{doc} {
      allow read: if true;
      allow write: if true;
    }
    match /orders/{doc} {
      allow read: if true;
      allow write: if true;
    }
  }
}
```

**Publish** চাপো।

---

## বিক্রেতার পাসওয়ার্ড

ডিফল্ট পাসওয়ার্ড: `krishi2026`

পরিবর্তন করতে `src/App.jsx` এর প্রথম দিকে:
```js
const SELLER_PASS = "krishi2026"; // এখানে নতুন পাসওয়ার্ড বসাও
```

---

## সমস্যা হলে

- Firebase config ঠিকমতো বসানো হয়েছে কিনা চেক করো
- Firestore rules publish করা হয়েছে কিনা দেখো
- Vercel এ redeploy দাও: Vercel Dashboard → Redeploy

---

**তৈরি করা হয়েছে:** গাইবান্ধা জেলার কৃষকদের জন্য 🌾
