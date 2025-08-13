# همس - منصة الإبلاغ المجهول الآمنة

منصة آمنة ومشفرة للإبلاغ عن المعلومات الحساسة بسرية تامة ودون الكشف عن الهوية.

## الميزات الأمنية

### 🔐 التشفير من النهاية إلى النهاية
- تشفير PGP لجميع التقارير
- مفاتيح تشفير قابلة للتخصيص
- تشفير احتياطي بـ AES

### 🛡️ حماية الهوية
- عدم تسجيل عناوين IP
- إزالة تلقائية لبيانات EXIF من الصور
- دعم شبكة Tor (.onion)
- وضع التصفح الخاص

### ⚡ الأداء المحسن
- تحميل سريع على الاتصالات البطيئة
- ضغط الملفات والصور
- تحسين للشبكات في سوريا

### 🚨 ميزات الأمان الطارئة
- زر الخروج السريع
- مهلة زمنية للخمول
- مسح البيانات الحساسة تلقائياً

## التقنيات المستخدمة

- **Frontend**: React + TypeScript + Tailwind CSS
- **Backend**: Supabase (قاعدة البيانات + تخزين الملفات)
- **التشفير**: OpenPGP.js + CryptoJS
- **الاستضافة**: Netlify
- **الأمان**: Row Level Security (RLS)

## التثبيت والتشغيل

### المتطلبات
- Node.js 18+
- حساب Supabase
- حساب Netlify (للنشر)

### الإعداد المحلي

1. **استنساخ المشروع**
```bash
git clone <repository-url>
cd secure-whistleblowing-platform
```

2. **تثبيت التبعيات**
```bash
npm install
```

3. **إعداد متغيرات البيئة**
```bash
cp .env.example .env
```

4. **تحديث ملف .env**
```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
  45wgrc-codex/verify-functionality-of-hams-website
VITE_AES_FALLBACK_KEY=your_aes_fallback_key
  
VITE_AES_FALLBACK_KEY=your_persistent_aes_key
 main
```

5. **تشغيل الخادم المحلي**
```bash
npm run dev
```

### إعداد Supabase

1. **إنشاء مشروع جديد** في [Supabase](https://supabase.com)

45wgrc-codex/verify-functionality-of-hams-website
2. **تشغيل Migrations**
   - نفّذ جميع الملفات داخل مجلد `supabase/migrations` في محرر SQL لدى Supabase

2. **تشغيل Migration**
   - انسخ محتوى `.bolt/supabase_discarded_migrations/20250626124600_polished_wildflower.sql`
   - نفذه في SQL Editor في Supabase
main

3. **إعداد Storage Bucket**
   - أنشئ bucket باسم `report-files`
   - فعّل الوصول العام للقراءة

4. **تحديث مفتاح PGP**
   - أنشئ مفتاح PGP جديد
   - حدّث الإعداد في جدول `platform_settings`

### النشر على Netlify

1. **ربط المستودع**
   - ادفع الكود إلى GitHub
   - اربط المستودع بـ Netlify

2. **إعداد البناء**
   - Build command: `npm run build`
   - Publish directory: `dist`

3. **إضافة متغيرات البيئة**
   - أضف `VITE_SUPABASE_URL` و `VITE_SUPABASE_ANON_KEY`

4. **النشر**
   - Netlify سينشر الموقع تلقائياً

## إعداد Tor Hidden Service

لأقصى درجات الأمان، يُنصح بإعداد خدمة Tor مخفية:

1. **تثبيت Tor**
```bash
sudo apt install tor
```

2. **تحديث إعدادات Tor** (`/etc/tor/torrc`)
```
HiddenServiceDir /var/lib/tor/whisper/
HiddenServicePort 80 127.0.0.1:8080
```

3. **إعادة تشغيل Tor**
```bash
sudo systemctl restart tor
```

4. **الحصول على عنوان .onion**
```bash
sudo cat /var/lib/tor/whisper/hostname
```

## الأمان والخصوصية

### للمستخدمين
- استخدم متصفح Tor للوصول
- استخدم شبكة Wi-Fi عامة
- لا تذكر معلومات تكشف هويتك
- احتفظ بالرقم المرجعي في مكان آمن

### للمطورين
- جميع البيانات مشفرة في قاعدة البيانات
- لا يتم تسجيل عناوين IP
- Row Level Security مفعل
- Headers أمنية شاملة
- منع فهرسة محركات البحث

## الدعم والمساهمة

### الإبلاغ عن مشاكل أمنية
- استخدم ملف `security.txt` للتواصل
- شفّر رسائلك بمفتاح PGP المنصة

### المساهمة
- Fork المشروع
- أنشئ branch للميزة الجديدة
- اختبر التغييرات محلياً
- أرسل Pull Request

## الترخيص

هذا المشروع مرخص تحت رخصة MIT - انظر ملف [LICENSE](LICENSE) للتفاصيل.

## إخلاء المسؤولية

هذه المنصة مصممة لحماية المبلغين، لكن الأمان الكامل يتطلب احتياطات إضافية من المستخدم. استخدم هذه المنصة على مسؤوليتك الخاصة.