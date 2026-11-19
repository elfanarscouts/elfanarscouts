# كشافة الفنار

## هيكل المستودع (كله في الجذر)
index.html · config.js · manifest.webmanifest · sw.js · icons/ · supabase/schema.sql · .gitignore · .env.example

## خطوات التنفيذ
1. **Supabase → SQL Editor:** خد نسخة احتياطية من `records`، وتأكد إن `private.sql` اتشغل، وبعدين شغّل `supabase/schema.sql` كله مرة واحدة.
2. **تأكد:** Storage فيه bucket اسمه `media`، وفي Table Editor الجداول `audit_log` و`login_log` و`attendance` و`announcements`.
3. **config.js:** فيه رابط المشروع ومفتاح anon (متعبّيين). لو غيّرت المشروع عدّلهم هناك.
4. **GitHub:** ارفع كل الملفات (بما فيها مجلد icons) على الفرع main، وبعدين Settings ← Pages ← Deploy from branch ← main / root.
5. **التثبيت كتطبيق:** أندرويد (Chrome): قائمة ⋮ ← تثبيت التطبيق. آيفون (Safari): مشاركة ← إضافة إلى الشاشة الرئيسية.
6. **تحديث نسخة جديدة:** غيّر رقم `V` في `sw.js` (مثلًا fanar-v2) عشان الموبايلات تاخد التحديث.

## الأمان (مهم)
- موقع GitHub Pages ثابت: أي مفتاح بيوصل للمتصفح. مفتاح **anon** مصمَّم يبقى عام، والحماية الحقيقية من سياسات RLS في `private.sql` و`schema.sql`.
- **ممنوع** تحط مفتاح `service_role` في أي ملف. صلاحياتك الكاملة بتكون من لوحة Supabase نفسها.
- ملف `.env` بيشتغل بس لو نقلت المشروع لأداة بناء زي Vite، فهنا عملنا `.env.example` للتوثيق و`.gitignore` يمنع رفع أي `.env` بالغلط.
