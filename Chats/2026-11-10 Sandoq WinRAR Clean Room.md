---
type: chat
url: https://chat.z.ai/s/edde337d-57fe-4d2a-86d6-12c530a32118
chat_date: 2026-11-10
chat_date_estimated: true
project:
  - "[[Sandoq]]"
status: processed
tags:
  - chats
---

# 2026-11-10 Sandoq WinRAR Clean Room

> [!info] المصدر (Source)
> [الرابط الأصلي للمحادثة](https://chat.z.ai/s/edde337d-57fe-4d2a-86d6-12c530a32118) — العنوان كما عُرض: «REA everything».
> التقاط حرفي كامل في [[2026-11-10 chat raw 03]].

> [!warning] التاريخ تقديري
> لم يُعثر على طابع زمني صريح في نص المحادثة — استُخدم تاريخ المعالجة (2026-11-10) في اسم الملف؛ اضبطه إن عرفت التاريخ الفعلي.
## الملخص (Summary)
- بدأت بقوائم تطبيقات مغلقة للتحليل العكسي (Obsidian ~100MB، Discord، Postman، Sublime، IDM، Photopea) ثم اختار hafid CamScanner بخطة ثلاثية وكلّف الهدف إلى WinRAR.
- فشلت الجلسات الثلاث مرتين: مسح خارجي حذف ملفات WinRAR وopencode/rea/claude من النظام، ثم نفاد حصص OpenCode المجانية (DeepSeek/GLM) — استُكمل بثلاثة تقارير مستقلة (2246/2664/2302 كلمة) دُمجت كمشرف.
- zarch 1.0.0 بلغة Go (~1100 سطر، مكتبة قياسية فقط): حاوية ZARC v1 (فهرس JSON + CRC32)، DEFLATE 0–9، AES-256-GCM + PBKDF2 (200 ألف دورة)، تقسيم، سجل استرداد يصلح كتلة تالفة؛ 13/13 اختباراً.
- تطبيق أندرويد Sandoq v1.0: فك ZIP/RAR4/RAR5/متعدد المجلدات/TAR/GZ/BZ2/XZ، إنشاء ZIP بتشفير AES-256، عربي/إنجليزي RTL، صفر صلاحيات إنترنت؛ 26/26 اختبار JVM بثنائي rar الرسمي (أُصلح عيب تعفير مجلدات zip4j 2.11.6 وكشف ترويسات ببايتات سالبة).
- بناء بلا root: jadx 1.5.3 + apktool 2.11.1، ECJ بدل JDK، d8 من build-tools 35، minSdk 19 (أندرويد 4.4 2013)؛ APK موقّع 670KB مع استخراج 2935 سلسلة و107 مفتاح تبديل من rar.txt.

## القرارات المستخلصة (Key Decisions)
- تغيير الهدف من CamScanner إلى WinRAR مع بقاء الخطة الثلاثية.
- اعتماد منهجية Clean-Room: الميزات والبنية الوظيفية فقط، كود أصلي 100%، فك RAR دون إنشاء.
- التطبيق لأندرويد قديم (minSdk 19) بطلب صريح، وتسليم APK للتحميل.

## المخرجات (Artifacts)
- [[2026-11-10 chat raw 03]] — النص الحرفي.
- download/zarch/ (ثنائيات + مصدر + README عربي + analysis/) وdownload/Sandoq-v1.0.apk (670KB موقّع).
- download/analysis-reports/ (5 تقارير).

## المتابعات (Follow-ups)
- [ ] تجربة APK على هاتف قديم وأرشيفات حقيقية.
- [ ] ميزات P1: تقسيم ZIP، إنشاء 7z/TAR، إشارات مرجعية.
- [ ] مفتاح OpenCode نُشر نصاً في المحادثة — حُجب في النسخة المحفوظة؛ الحساب مستهلك الحصة.

%% مرتبط: [[Sandoq]] · [[REA]] %%
