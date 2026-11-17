# মোবাইল দিয়ে APK বানানোর পদ্ধতি (কম্পিউটার ছাড়াই)

এই ZIP-এ `.github/workflows/build-apk.yml` রাখা হয়েছে। GitHub-এর cloud runner-এ Flutter build চলবে; আপনার ফোনে Flutter/Android Studio ইনস্টল করতে হবে না।

## ফোন দিয়ে APK বানান

1. GitHub-এ অ্যাকাউন্ট খুলুন: https://github.com/
2. ব্রাউজারে GitHub-এ **New repository** চাপুন। নাম দিন `muslim-bangla-app`; Public বা Private যেকোনোটি বেছে নিন।
3. ZIP ফাইলটি ফোনে Extract করুন (Files app / ZArchiver)।
4. Extract করা `muslim_bangla_flutter` ফোল্ডারের ভেতরের সব ফাইল GitHub repository-তে আপলোড করুন। `.github` ফোল্ডারটিও অবশ্যই আপলোড করবেন। GitHub mobile website-এ একাধিক ফাইল upload করা যায়; প্রয়োজনে GitHub app বা browser-এর Desktop site ব্যবহার করুন।
5. সব ফাইল `main` branch-এ commit করুন।
6. Repository-র **Actions** tab খুলুন। `Build Android APK` workflow নির্বাচন করে **Run workflow** চাপুন (push করলেও build শুরু হবে)।
7. Build শেষ হলে workflow run খুলে **Artifacts** থেকে `muslim-bangla-release-apk` ডাউনলোড করুন।
8. ZIP artifact extract করে `app-release.apk` ফোনে ইনস্টল করুন। Android-এ browser/files app থেকে install permission চাইতে পারে।

## গুরুত্বপূর্ণ সীমাবদ্ধতা

- এই starter-এ UI, তাসবিহ কাউন্টার, আমল ট্র্যাকার, প্রাথমিক যাকাত ক্যালকুলেটর, নেভিগেশন এবং AdMob test banner আছে।
- কুরআন/হাদিসের পূর্ণ নির্ভরযোগ্য ডেটা, লাইভ নামাযের সময়, আজান অ্যালার্ম, প্রকৃত কিবলা কম্পাস, মসজিদ ম্যাপ, AI উত্তর, লাইভ সম্প্রচার, লগইন/ক্লাউড সিঙ্ক, পূর্ণ Admin Panel, পেমেন্ট/সাবস্ক্রিপশন এখনো সংযুক্ত নয়। এগুলোর জন্য API key, Firebase project, অনুমতি, যাচাইকৃত কনটেন্ট এবং নিরাপদ server-side code লাগবে।
- APK-টি এখন GitHub Actions থেকে unsigned/ডিবাগ-সাইনিং fallback সহ তৈরি হতে পারে; Play Store-এ প্রকাশের জন্য নিজস্ব upload keystore ও release signing সেটআপ আবশ্যক। Keystore/password কখনো GitHub-এ আপলোড করবেন না।
- AdMob-এর sample test ID কেবল পরীক্ষার জন্য। নিজের AdMob App ID ও Ad Unit ID বসাতে হবে এবং Google-এর অনুমোদন/consent requirements পূরণ করতে হবে। নিজের বিজ্ঞাপনে ক্লিক করবেন না।
- কুরআন, হাদিস ও নামাযের সময় যাচাই না করে ইবাদতের কাজে ব্যবহারযোগ্য বলে প্রচার করবেন না।
