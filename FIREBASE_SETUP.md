# ☁️ গুগল ফায়ারবেস (Firebase) ক্লাউড ডাটাবেজ সেটআপ গাইড
### মোবাইল ও ল্যাপটপের মধ্যে লাইভ রিয়েল-টাইম ডাটা সিঙ্ক (Vercel & GitHub)

---

## 🧐 কেন ফায়ারবেস ডাটাবেজ প্রয়োজন?

আপনি ওয়েবসাইটটি **Vercel**-এ হোস্ট করেছেন। ভার্সেল আপনার এইচটিএমএল ও জাভাস্ক্রিপ্ট ফাইলগুলো ইন্টারনেটে সার্ভ করে, কিন্তু কোনো কেন্দ্রীয় ডাটাবেজ সংরক্ষণ করে না। 

ফায়ারবেস ডাটাবেজ ছাড়া:
- আপনি মোবাইলে গেস্ট অ্যাড করলে তা শুধু **মোবাইলের মেমোরিতে (LocalStorage)** থাকে।
- ল্যাপটপ বা অন্য কারো মোবাইল তা দেখতে পায় না।

গুগল ফায়ারবেস (Firebase Realtime Database) যুক্ত করলে:
- 📱 মোবাইল থেকে যে কেউ ফর্ম ফিলাপ করলে সাথে সাথে ল্যাপটপে অ্যাডমিন তা লাইভ দেখতে পাবেন!
- 🚪 গেটের ভলেন্টিয়ার যেকোনো ফোন দিয়ে স্ক্যান করে **"✓ গেস্ট চেক ইন"** চাপলে ল্যাপটপে বসে অ্যাডমিন সাথে সাথে স্ট্যাটাস `Checked In` দেখতে পাবেন!
- 💻 ল্যাপটপ থেকে কোনো গেস্ট এডিট বা অ্যাড করলে সকল ফোনে সাথে সাথে আপডেট হয়ে যাবে!
- 🌍 যেকোনো ডিভাইস থেকে তৈরি হওয়া কিউআর কোড বিশ্বের যেকোনো মোবাইল বা কম্পিউটার দিয়ে স্ক্যান করা যাবে!

> **নোট:** গুগল ফায়ারবেস সম্পূর্ণ **ফ্রি** (Spark Plan), কোনো ক্রেডিট কার্ড বা পেমেন্ট প্রয়োজন নেই।

---

## ⚡ মাত্র ২ মিনিটে ফায়ারবেস সেটআপ করার ৪টি সহজ ধাপ:

### ধাপ ১: ফায়ারবেস প্রজেক্ট তৈরি করুন
1. ব্রাউজারে যান: [console.firebase.google.com](https://console.firebase.google.com/)
2. আপনার জিমেইল দিয়ে লগইন করুন এবং **"Create a project"** (বা **"Add project"**) এ ক্লিক করুন।
3. প্রজেক্টের একটি নাম দিন, যেমন: `alipur-event` বা `eventpass-alipur`।
4. Google Analytics এর অপশন আসলে টিক চিহ্ন তুলে দিয়ে (Disable) **"Create project"** এ ক্লিক করুন।
5. কয়েক সেকেন্ডের মধ্যে প্রজেক্ট তৈরি হয়ে যাবে, **Continue** চাপুন।

---

### ধাপ ২: Realtime Database তৈরি করুন
1. বাম পাশের মেন্যু থেকে **Build** > **Realtime Database** এ ক্লিক করুন।
2. **"Create Database"** বাটনে চাপুন।
3. ডাটাবেজ লোকেশন যা ডিফল্ট আছে রেখে **Next** চাপুন।
4. সিকিউরিটি রুলস অপশন আসলে অবশ্যই **"Start in test mode"** নির্বাচন করুন।
   *(এটি `.read: true` এবং `.write: true` করে দেয়, যাতে ওয়েবসাইট সরাসরি পড়তে ও লিখতে পারে)*
5. **"Enable"** বাটনে ক্লিক করুন। আপনার ডাটাবেজ তৈরি হয়ে গেল!

---

### ধাপ ৩: Web App কনফিগ কোড নিন
1. ফায়ারবেস স্ক্রিনের উপরে বামে গিয়ার আইকন (⚙️) ক্লিক করে **Project settings** এ যান।
2. পেজের নিচে স্ক্রল করে **Your apps** সেকশনে যান এবং ওয়েব আইকন `</>` এ ক্লিক করুন।
3. App nickname দিন, যেমন: `EventPass Web` এবং **"Register app"** চাপুন।
4. স্ক্রিনে একটি কোড ব্লক দেখতে পাবেন, যেখানে `firebaseConfig` থাকবে:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyDxxxxxxxxx...",
  authDomain: "alipur-event.firebaseapp.com",
  databaseURL: "https://alipur-event-default-rtdb.firebaseio.com",
  projectId: "alipur-event",
  storageBucket: "alipur-event.appspot.com",
  messagingSenderId: "123456789...",
  appId: "1:123456789:web:xxxxxx..."
};
```

---

### ধাপ ৪: কোডটি আপনার `index.html`-এ বসিয়ে গিটহাবে পুশ করুন

আপনার প্রজেক্টের `index.html` ফাইলটি টেক্সট এডিটরে (VS Code বা Notepad) ওপেন করুন।
লাইন ২৯০ এর দিকে নিচের অংশটি দেখতে পাবেন:

```javascript
const HARDCODED_FIREBASE_CONFIG = {
  apiKey: "",
  authDomain: "",
  databaseURL: "",
  projectId: "",
  storageBucket: "",
  messagingSenderId: "",
  appId: ""
};
```

এখানে ফায়ারবেস থেকে পাওয়া আপনার তথ্যগুলো বসিয়ে দিন। যেমন:
```javascript
const HARDCODED_FIREBASE_CONFIG = {
  apiKey: "AIzaSyDxxxxxxxxx...",
  authDomain: "alipur-event.firebaseapp.com",
  databaseURL: "https://alipur-event-default-rtdb.firebaseio.com",
  projectId: "alipur-event",
  storageBucket: "alipur-event.appspot.com",
  messagingSenderId: "123456789...",
  appId: "1:123456789:web:xxxxxx..."
};
```

ফাইলটি সেভ করুন এবং গিটহাবে পুশ করুন:
```bash
git add index.html
git commit -m "Connect Firebase Realtime Cloud Database"
git push
```

---

## 🚀 ফলাফল ও পরীক্ষা (Testing)

গিটহাবে পুশ করার ১০ সেকেন্ডের মধ্যে ভার্সেল স্বয়ংক্রিয়ভাবে লাইভ সাইট আপডেট করে ফেলবে:

1. আপনার লাইভ সাইট খুলুন: `https://eventpass-alipur.vercel.app/`
2. উপরে দেখতে পাবেন সবুজ ব্যাজ: **`🟢 ☁️ Cloud Live`**
3. **ল্যাপটপে:** সাইটটি ওপেন রাখুন।
4. **মোবাইলে:** সাইটটি ওপেন করে "📝 Fill Up the Form" দিয়ে একজন নতুন গেস্ট যোগ করুন।
5. **জাদু দেখুন:** মোবাইলে সাবমিট করার ১ সেকেন্ডের মধ্যে ল্যাপটপের স্ক্রিনে কোনো রিফ্রেশ ছাড়াই ওই নতুন গেস্টের নাম ও ছবি চলে আসবে!
6. গেট স্ক্যানার দিয়ে মোবাইল থেকে স্ক্যান করে চেক-ইন করলে সাথে সাথে ল্যাপটপে স্ট্যাটাস সবুজ হয়ে `Verified / Checked In` হয়ে যাবে!
