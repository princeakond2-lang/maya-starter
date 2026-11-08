# Maya Starter — শুরুর প্রজেক্ট

এটা একটা ছোট্ট Android (Kotlin) প্রজেক্ট: মাইক বাটনে চাপলে বাংলায় কথা শুনবে,
Google Gemini API-তে পাঠাবে, আর উত্তর বাংলায় পড়ে শোনাবে। Maya AI-এর পুরো
অ্যাপ না, কিন্তু এর "ভয়েস → AI → ভয়েস" মূল অংশটা এখান থেকেই শুরু হয়।

## যা যা লাগবে (সব ফ্রি)
1. **Android Studio** — ডাউনলোড: https://developer.android.com/studio
2. **Gemini API key** — https://aistudio.google.com এ গিয়ে Google অ্যাকাউন্ট
   দিয়ে লগইন করুন, "Get API key" চাপুন, ফ্রি key তৈরি হবে।

## সেটআপ
1. এই পুরো ফোল্ডারটা Android Studio-তে "Open" করুন।
2. `app/src/main/java/com/example/mayastarter/MainActivity.kt` ফাইল খুলুন।
3. উপরের দিকে এই লাইন খুঁজুন:
   ```kotlin
   private val GEMINI_API_KEY = "PASTE_YOUR_GEMINI_API_KEY_HERE"
   ```
   এখানে নিজের key বসান।
4. একটা ফোন বা emulator কানেক্ট করে ▶ Run চাপুন।
5. অ্যাপ খুললে প্রথমবার মাইক পারমিশন চাইবে — Allow দিন।
6. 🎤 বলুন বাটনে চেপে বাংলায় প্রশ্ন করুন।

## এরপর কী যোগ করবেন (Maya AI-এর মতো বানাতে চাইলে)
- **ভাসমান অর্ব (floating orb):** `TYPE_APPLICATION_OVERLAY` দিয়ে একটা
  Service বানাতে হবে, আর "Display over other apps" পারমিশন নিতে হবে।
- **ফোন/অ্যাপ কন্ট্রোল (WhatsApp মেসেজ পাঠানো ইত্যাদি):**
  `AccessibilityService` ক্লাস বানিয়ে ব্যবহারকারীর কাছ থেকে
  Accessibility পারমিশন নিতে হবে। এটা একটু জটিল এবং Google Play-তে
  publish করতে গেলে বাড়তি review লাগে।
- **লগইন:** Firebase Authentication (ফ্রি) যোগ করুন।
- **স্মৃতি/মেমোরি সেভ করা:** Room ডাটাবেজ (Android-এর built-in, ফ্রি)।
- **স্ক্রিন স্ক্যান করা:** MediaProjection API দিয়ে স্ক্রিনশট নিয়ে
  সেটা Gemini-তে ছবি হিসেবে পাঠানো যায় (Gemini ছবি বুঝতে পারে)।

## সতর্কতা
- কোডে key হার্ডকোড করা শুধু নিজের টেস্টের জন্য ঠিক আছে। অ্যাপ অন্য কাউকে
  দিলে বা Play Store-এ দিলে, key টা APK থেকে বের করা সম্ভব — তাই আসল
  অ্যাপে key নিজের সার্ভারে রেখে, ফোন থেকে আপনার সার্ভারে কল করান।
- Gemini-এর ফ্রি টিয়ারের ব্যবহার-সীমা আছে; বেশি ব্যবহারকারী হলে তা পেরিয়ে
  যেতে পারে। সীমা Google AI Studio-তে গিয়ে দেখে নিন।
