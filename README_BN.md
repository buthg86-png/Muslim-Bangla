# মুসলিম বাংলা — Flutter Android starter

এই প্রজেক্টটি আপনার স্ক্রিনশটের অনুপ্রেরণায় তৈরি একটি বাংলা ইসলামিক অ্যাপের **চালু করা যায় এমন starter source**। এটি এখনই Play Store-এ প্রকাশের জন্য সম্পূর্ণ প্রস্তুত নয়। কুরআন/হাদিসের পূর্ণ ডেটা, যাচাইকৃত নামাযের সময়, কিবলা সেন্সর, নোটিফিকেশন, Firebase backend, privacy policy, আপনার AdMob account ও release signing key যুক্ত করতে হবে।

## ১) চালানোর নিয়ম

1. Flutter SDK ও Android Studio ইনস্টল করুন।
2. টার্মিনালে চালান:
   ```bash
   flutter create muslim_bangla
   ```
3. এই ZIP-এর `pubspec.yaml` ও `lib/main.dart` নতুন প্রজেক্টে কপি করে আগের ফাইল replace করুন।
4. প্রজেক্ট ফোল্ডারে:
   ```bash
   flutter pub get
   flutter run
   ```

## ২) বিজ্ঞাপন থেকে আয় (AdMob)

- Google AdMob account খুলে অ্যাপটি register করুন: https://admob.google.com/
- AdMob-এ Android App ID এবং Banner Ad Unit ID তৈরি করুন।
- `lib/main.dart`-এর `testBannerId`-কে আপনার Banner Ad Unit ID দিয়ে বদলান।
- `android/app/src/main/AndroidManifest.xml`-এর `<application>` ট্যাগের ভিতরে এই metadata যোগ করুন:
  ```xml
  <meta-data
      android:name="com.google.android.gms.ads.APPLICATION_ID"
      android:value="ca-app-pub-XXXXXXXXXXXXXXXX~YYYYYYYYYY"/>
  ```
- `android:value`-এ আপনার নিজের App ID বসাবেন; Banner ID নয়।
- টেস্ট চলাকালে sample test ID-ই রাখুন। নিজের বিজ্ঞাপনে নিজে ক্লিক করবেন না, ভুয়া impression/click তৈরি করবেন না। AdMob approval ও policy compliance ছাড়া আয় নিশ্চিত নয়।
- ইউজারের সম্মতি/প্রাইভেসি সংক্রান্ত Google UMP consent flow এবং প্রয়োজনীয় disclosures production release-এর আগে যুক্ত করুন।

## ৩) APK তৈরি

ডিবাগ APK:
```bash
flutter build apk --debug
```
Release APK:
```bash
flutter build apk --release
```
Play Store-এর জন্য সাধারণত App Bundle:
```bash
flutter build appbundle --release
```
ফাইল পাবেন `build/app/outputs/`-এর ভিতরে।

## ৪) Release signing

Play Store-এ দেওয়ার আগে নিজের upload keystore তৈরি করে Flutter-এর Android signing নির্দেশনা অনুসরণ করুন:
https://docs.flutter.dev/deployment/android
Keystore/password কখনো কাউকে পাঠাবেন না বা GitHub-এ দেবেন না।

## ৫) যে কাজগুলো এখনো integration দরকার

- Prayer time: location permission + নির্ভরযোগ্য calculation library/API + calculation method + madhhab + local mosque adjustment।
- Azan reminder: local notification plugin, Android 13+ notification permission, exact alarm policy, battery optimization handling; পূর্ণ আজান audio ব্যবহারের আগে লাইসেন্স যাচাই।
- Qibla: device compass/magnetometer + location + heading calibration।
- Quran/Hadith: যাচাইকৃত আরবি মূল, অনুবাদ, তাফসির, অডিও ও সঠিক রেফারেন্স; কপিরাইট/লাইসেন্স অনুমতি।
- Firebase: user login, cloud sync, admin content panel, analytics/crash reporting (যদি দরকার হয়)।
- Mosque finder: Google Maps/Places API key, billing, privacy disclosures।
- Donations: অনুমোদিত payment gateway, charity verification, receipt, refund ও transparent accounting। ব্যক্তিগত অ্যাকাউন্টে অনুদান নেবেন না যদি তা আইন/নীতির সঙ্গে না মেলে।
- Privacy policy, Terms, account/data deletion, support email ও store listing।

## ৬) আয়ের বাস্তবতা

অ্যাপ ডাউনলোড হলেই টাকা আসে না। AdMob-এ অনুমোদন, বিজ্ঞাপনের বৈধ impression, দেশ/বিজ্ঞাপনের চাহিদা, retention এবং Play Store policy-এর ওপর আয় নির্ভর করে। বিজ্ঞাপন যেন কুরআন/নামায/দোয়ার পাঠে বাধা না দেয়; ইবাদতের গুরুত্বপূর্ণ স্ক্রিনে intrusive ads ব্যবহার করবেন না। সাবস্ক্রিপশন বা donation থাকলে মূল্য, সুবিধা ও অর্থের ব্যবহার স্পষ্টভাবে দেখান।

## ৭) নিরাপদ প্রকাশের আগে যাচাই

- পাঁচ ওয়াক্ত নামাযের সময় একাধিক স্থানীয় মসজিদের সময়ের সঙ্গে মিলিয়ে দেখুন।
- কুরআন/হাদিসের প্রতিটি লেখা যোগ্য আলেম/সম্পাদক দিয়ে যাচাই করুন।
- ভুল সময় বা ভুল ধর্মীয় উদ্ধৃতি থাকলে প্রকাশ করবেন না।
- Privacy policy ও Data safety form বাস্তব data collection-এর সঙ্গে মিলিয়ে পূরণ করুন।


## শুধু মোবাইল দিয়ে APK
কম্পিউটার ছাড়াই GitHub Actions ব্যবহার করে ফোন থেকে APK বানানোর ধাপগুলো `MOBILE_BUILD_BN.md` ফাইলে দেওয়া আছে। `.github/workflows/build-apk.yml` ফোল্ডারটি GitHub-এ আপলোড করা জরুরি।


## Admin Panel
`admin_panel/`-এ Firebase Authentication ও Firestore-ভিত্তিক Admin Panel starter আছে। সেটআপের জন্য `ADMIN_PANEL_SETUP_BN.md` পড়ুন। Firebase project/config/admin custom claim ছাড়া এটি কাজ করবে না।
