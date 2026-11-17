# Muslim Bangla Admin Panel — সেটআপ নির্দেশিকা

## কী করতে পারবেন
- অ্যাডমিন লগইন (Firebase Authentication)
- যাচাইকৃত কনটেন্ট/দু’আ/হাদিস/প্রবন্ধ প্রকাশ
- নোটিশ প্রকাশ
- কিছু public app settings পরিবর্তন
- কনটেন্ট/নোটিশের সংখ্যা দেখা

## এখনো কী করে না
- AdMob আয়/পেমেন্ট দেখায় না (AdMob account/API access দরকার)
- Firebase user management/analytics dashboard সম্পূর্ণ নয়
- Push notification পাঠায় না (FCM + trusted server function দরকার)
- Premium billing, donation/payment বা shop order management নেই
- Admin panel HTML-এ Firebase config placeholder আছে; Firebase project ছাড়া লগইন/ডেটাবেস চলবে না

## Firebase চালু করুন
1. https://console.firebase.google.com/ এ project তৈরি করুন।
2. Authentication → Sign-in method → Email/Password চালু করুন।
3. Authentication → Users থেকে নিজের admin user তৈরি করুন।
4. Firestore Database তৈরি করুন।
5. Project Settings → Web app থেকে config কপি করে `admin_panel/app.js`-এর `firebaseConfig`-এ বসান।
6. Firestore → Rules-এ project-এর `firestore.rules` কপি করে publish করুন।
7. নিজের user-এর UID কপি করুন।
8. নিরাপদ কম্পিউটার/সার্ভারে Firebase Admin SDK দিয়ে `firebase_admin_setup/set_admin_claim.js` চালিয়ে ওই UID-তে `{admin:true}` custom claim দিন। Service account JSON কখনো ফোনের frontend/GitHub-এ রাখবেন না।
9. Firebase Hosting বা অন্য HTTPS hosting-এ `admin_panel` ফোল্ডার publish করুন। GitHub Pages-এর মতো static hosting-এও পেজ রাখা যায়, কিন্তু Firebase config ও Firestore rules ঠিক থাকতে হবে।

## নিরাপত্তা
- Admin claim শুধুমাত্র trusted Firebase Admin SDK দিয়ে দিন।
- কখনো Firestore rules-এ `allow write: if true` দেবেন না।
- Firebase config-এর API key সাধারণত web config; কিন্তু service account private key নয়।
- কনটেন্টে ধর্মীয় সূত্র বাধ্যতামূলক রাখুন এবং প্রকাশের আগে আলেম/সম্পাদক দিয়ে যাচাই করুন।
- অ্যাডমিনের জন্য শক্তিশালী আলাদা পাসওয়ার্ড ও 2-step verification ব্যবহার করুন।

## AdMob ও আয়
AdMob revenue, payment profile, tax details ও payout শুধু AdMob Console-এ যাচাই/দেখুন। Admin panel-এ আয় দেখাতে AdMob reporting API, OAuth এবং নিরাপদ backend দরকার; secret বা refresh token frontend-এ রাখা যাবে না।
