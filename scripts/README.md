# Appwrite Database Setup للمشروع Bousla

هذا السكريبت يقوم بإنشاء جميع الـ Collections والـ Attributes المطلوبة تلقائياً في Appwrite.

## 📋 المتطلبات

1. حساب Appwrite نشط
2. Node.js مثبت على جهازك
3. API Key من Appwrite Console

## 🚀 خطوات التشغيل

### 1️⃣ إنشاء API Key

1. افتح [Appwrite Console](https://fra.cloud.appwrite.io/console/project-696446d40034324177b2)
2. اذهب إلى **Settings** → **API Keys**
3. اضغط **Create API Key**
4. اسم الـ Key: `Database Setup`
5. اختر Scopes التالية:
   - ✅ `databases.read`
   - ✅ `databases.write`
   - ✅ `collections.read`
   - ✅ `collections.write`
   - ✅ `attributes.read`
   - ✅ `attributes.write`
6. انسخ الـ API Key

### 2️⃣ تحديث السكريبت

افتح ملف `setup-appwrite.js` وضع الـ API Key في السطر 18:

```javascript
.setKey('YOUR_API_KEY_HERE'); // ⚠️ استبدل هذا بالـ API Key
```

### 3️⃣ تثبيت التبعيات

```bash
npm install
```

### 4️⃣ تشغيل السكريبت

```bash
npm run setup
```

أو مباشرة:

```bash
node setup-appwrite.js
```

## 📦 Collections التي سيتم إنشاؤها

السكريبت سيقوم بإنشاء 8 Collections:

1. ✅ **applicants** - بيانات المتقدمين والطلاب
2. ✅ **page_visits** - تتبع زيارات الموقع
3. ✅ **admins** - المستخدمين والمدرسين
4. ✅ **messages** - رسائل الشات
5. ✅ **calendar_content** - محتوى التقويم
6. ✅ **global_tasks** - المهام العامة
7. ✅ **transactions** - المعاملات المالية
8. ✅ **finance_todos** - مهام الإدارة المالية

## 🗂️ الخطوة التالية: إنشاء Storage Buckets

بعد تشغيل السكريبت، يجب عليك إنشاء Buckets يدوياً في Appwrite Console:

### 1. Bucket: `chats`
- **Name:** Chats
- **ID:** `chats`
- **Permissions:** 
  - Read: `any`
  - Create: `any`
  - Update: `any`
  - Delete: `any`
- **File Size Limit:** 50 MB
- **Allowed File Extensions:** Leave empty (allow all)

### 2. Bucket: `calendar`
- **Name:** Calendar
- **ID:** `calendar`
- **Permissions:** 
  - Read: `any`
  - Create: `any`
  - Update: `any`
  - Delete: `any`
- **File Size Limit:** 10 MB
- **Allowed File Extensions:** `jpg, jpeg, png, gif, webp`

## ⚠️ ملاحظات مهمة

- السكريبت يتعامل مع Collections الموجودة بالفعل ويتخطاها
- إذا حدث خطأ في إنشاء attribute معين، سيستمر السكريبت في باقي الـ attributes
- يوجد تأخير بسيط بين كل عملية لتجنب Rate Limiting

## 🔧 استكشاف الأخطاء

### خطأ: "Invalid API Key"
- تأكد من نسخ الـ API Key بشكل صحيح
- تأكد من أن الـ API Key لديه الصلاحيات المطلوبة

### خطأ: "Database not found"
- تأكد من أن Database ID هو `BouslaDB`
- تأكد من إنشاء Database في Appwrite Console أولاً

### خطأ: "Collection already exists"
- هذا طبيعي، السكريبت سيتخطى الـ Collection الموجودة

## 📞 الدعم

إذا واجهت أي مشاكل، تحقق من:
1. Console logs في Terminal
2. Appwrite Console → Database → Collections
3. Network tab في Developer Tools

---

**تم إنشاء هذا السكريبت لمشروع Bousla** 🚀
