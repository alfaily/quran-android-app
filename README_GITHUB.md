# 🚀 بناء تطبيق القرآن الكريم باستخدام GitHub Actions

## 📋 الخطوات (سهلة جداً!)

### الخطوة 1: إنشاء حساب GitHub (مجاني)

1. اذهب إلى: https://github.com/
2. اضغط **"Sign up"** (تسجيل)
3. أدخل:
   - البريد الإلكتروني
   - كلمة المرور
   - اسم المستخدم
4. أكمل التسجيل

### الخطوة 2: إنشاء Repository جديد

1. بعد تسجيل الدخول، اضغط **"+"** في الأعلى
2. اختر **"New repository"** (مستودع جديد)
3. املأ المعلومات:
   - **Repository name**: `quran-app` (أو أي اسم تريده)
   - **Description**: `تطبيق القرآن الكريم`
   - اختر **Public** (عام) أو **Private** (خاص)
   - ✅ اختر **"Add a README file"**
4. اضغط **"Create repository"**

### الخطوة 3: رفع الملفات

#### الطريقة الأولى: من خلال الموقع (الأسهل)

1. في صفحة Repository، اضغط **"Add file"** → **"Upload files"**
2. اسحب وأفلت **كل محتويات مجلد `quran-android`** (كل الملفات والمجلدات)
3. في الأسفل، اكتب رسالة مثل: "Initial commit"
4. اضغط **"Commit changes"**

**مهم جداً**: تأكد من رفع:
- ✅ مجلد `.github/workflows/` (يحتوي على build-apk.yml)
- ✅ ملف `gradlew`
- ✅ مجلد `gradle/`
- ✅ مجلد `app/`
- ✅ جميع ملفات `.gradle` و `.xml`

#### الطريقة الثانية: باستخدام Git (للمتقدمين)

```bash
cd quran-android
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/quran-app.git
git push -u origin main
```

### الخطوة 4: تشغيل GitHub Actions

بعد رفع الملفات:

1. اذهب إلى تبويب **"Actions"** في أعلى الصفحة
2. سترى workflow اسمه **"Build Android APK"**
3. إذا لم يبدأ تلقائياً:
   - اضغط على اسم الـ workflow
   - اضغط **"Run workflow"** (تشغيل)
   - اضغط الزر الأخضر **"Run workflow"**

### الخطوة 5: تحميل APK

1. انتظر 5-10 دقائق حتى ينتهي البناء
2. عندما يصبح لون ✅ أخضر، اضغط على اسم الـ workflow run
3. في الأسفل، ستجد قسم **"Artifacts"**
4. اضغط على **"quran-app-debug"** لتحميل APK
5. فك الضغط عن الملف المحمّل
6. ستجد `app-debug.apk` - هذا هو تطبيقك! 🎉

---

## 🎯 ملاحظات مهمة

### ✅ المميزات
- **مجاني 100%** - GitHub Actions مجاني للمشاريع العامة
- **تلقائي** - كل مرة ترفع تحديث، يُبنى APK جديد
- **لا يحتاج Android Studio** - كل شيء في السحابة
- **آمن** - ملفاتك محفوظة على GitHub

### ⚠️ تنبيهات
- **APK غير موقّع**: الـ APK المُنتَج هو `debug` version (نسخة تجريبية)
- **للاستخدام الشخصي**: يمكن تثبيته على هاتفك مباشرة
- **للنشر على Google Play**: تحتاج لتوقيع الـ APK (خطوة إضافية)

### 📱 كيف تثبت APK على هاتفك؟

1. انقل ملف `app-debug.apk` إلى هاتفك
2. افتح الملف من مدير الملفات
3. قد يطلب منك السماح بـ "تثبيت من مصادر غير معروفة"
4. اسمح بذلك
5. اضغط "تثبيت"
6. جاهز! 🎉

---

## 🔧 حل المشاكل

### المشكلة: Build فشل (❌ أحمر)

**الحل**:
1. اضغط على الـ workflow الفاشل
2. اقرأ رسالة الخطأ
3. تأكد من رفع جميع الملفات خاصة:
   - `.github/workflows/build-apk.yml`
   - `gradlew`
   - `gradle/wrapper/gradle-wrapper.properties`

### المشكلة: لا أجد تبويب Actions

**الحل**:
- تأكد أن Repository عام (Public)
- أو فعّل Actions من Settings → Actions → Enable

### المشكلة: لا أجد Artifacts

**الحل**:
- انتظر حتى ينتهي الـ build (✅ أخضر)
- Artifacts تظهر فقط بعد نجاح الـ build

---

## 🎁 خطوة إضافية: توقيع APK للنشر

إذا أردت نشر التطبيق على Google Play:

1. أنشئ keystore:
```bash
keytool -genkey -v -keystore quran-app.keystore -alias quran -keyalg RSA -keysize 2048 -validity 10000
```

2. أضف secrets في GitHub:
   - Settings → Secrets → New repository secret
   - أضف: `KEYSTORE_FILE`, `KEYSTORE_PASSWORD`, `KEY_ALIAS`, `KEY_PASSWORD`

3. عدّل workflow لاستخدام `assembleRelease` بدلاً من `assembleDebug`

---

## 📞 المساعدة

إذا واجهت أي مشكلة:
1. تأكد من رفع كل الملفات
2. تحقق من رسائل الخطأ في Actions
3. تأكد من أن ملف `build-apk.yml` في المسار الصحيح: `.github/workflows/`

---

**بالتوفيق! 🚀 ستحصل على APK في دقائق!**

