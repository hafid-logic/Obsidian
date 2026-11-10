---
type: clipping
url: ""
date: 2026-11-11
source_title: دقلة نور الواحات — تحليل صفحة الهبوط ودليل الصور والمعرض
tags:
  - clippings
---

# النص الحرفي: دقلة نور الواحات — تحليل صفحة الهبوط ودليل الصور والمعرض

> [!info] التقاط حرفي بتاريخ 2026-11-11
> النص كما لصقه hafid مباشرة في المحادثة (محادثة من chat.z.ai بلا رابط مشاركة)، بعد فحص أمني آلي وحجب أي سلاسل تشبه التوكنات/المفاتيح بـ`[REDACTED:*]`. المرجع المنظَّم: [[2026-11-11 Deglet Nour Landing Page]].

---

تحليل شامل لصفحة "دقلة نور الواحات" 🌴
📊 نظرة عامة
هذه صفحة هبوط (Landing Page) مصممة لبيع التمور الجزائرية (دقلة نور) من بسكرة مباشرة للمستهلكين. الصفحة مصممة باللغة العربية وتستهدف السوق الجزائري.

✅ نقاط القوة
1. التصميم والتجربة البصرية
✨ فيديو خلفية جذاب لأشجار النخيل يعطي انطباعاً بالأصالة
🎨 ألوان متناسقة (أخضر، أصفر، أبيض) تعكس الطبيعة والجودة
📱 تصميم متجاوب يعمل على الهواتف والحواسيب
🔘 أزرار ثابتة للطلب في الأسفل للهواتف المحمولة
2. استراتيجيات البيع النفسية
⚠️ تحذير المخزون المحدود (47 صندوق متبقي) - يخلق إلحاحاً
⭐ تصنيف الباقات (الأكثر طلباً، VIP) - يوجه الاختيار
💰 خصم ضمني في الباقة الكبيرة (توفير واضح)
🚚 توصيل مجاني للباقات الأكبر
3. سهولة الطلب
📝 نموذج بسيط وواضح بحقول محدودة
📞 خياران للتواصل (واتساب + اتصال مباشر)
🔢 حاسبة تلقائية للسعر تتفاعل مباشرة
📍 قائمة كاملة بجميع ولايات الجزائر (58 ولاية)
4. التقنيات المستخدمة
⚡ أداء سريع باستخدام Tailwind CSS من CDN
📊 تكامل مع Google Sheets لتسجيل الطلبات تلقائياً
🔄 تجربة سلسة بدون تحديث الصفحة
⚠️ نقاط التحسين المقترحة
1. الثقة والمصداقية
❌ المشاكل الحالية:
- لا توجد صور حقيقية للمنتج
- لا توجد شهادات عملاء
- لا معلومات عن الشركة أو ترخيصها
- الفيديو من مصدر عام (mixkit) وليس خاصاً

✅ الحلول المقترحة:
- إضافة صور فوتوغرافية احترافية للتمور
- عرض تقييمات وآراء عملاء سابقين
- إضافة شعار وسجل تجاري
- استبدال الفيديو بتصوير حقيقي من المزرعة
2. المعلومات الناقصة
مطلوب إضافة:
✓ معلومات تفصيلية عن جودة المنتج
✓ شرح طريقة التعبئة والتغليف
✓ سياسة الاسترجاع والضمان
✓ مدة التوصيل المتوقعة لكل ولاية
✓ طرق الدفع المتاحة (عند الاستلام؟)
3. المخاوف التقنية
🔴 مشكلة خطيرة - الأمان:
javascript
// السكريبت الحالي يرسل لـ Google Apps Script بدون تشفير
fetch(SCRIPT_URL, {
    method: 'POST',
    mode: 'no-cors', // ⚠️ يخفي الأخطاء ولا يوفر حماية حقيقية
المخاطر:

يمكن لأي شخص رؤية رابط API في كود المصدر
لا توجد آلية للتحقق من الطلبات الحقيقية
عرضة للسبام والطلبات الوهمية
الحل المقترح:

استخدام reCAPTCHA للتحقق من البشر
إضافة Token authentication
استخدام خدمة Backend آمنة
🟡 عداد المخزون الوهمي:
javascript
// هذا الكود مضلل للعملاء
let stock = 47;
setInterval(() => {
    if (stock > 5) {
        stock--;  // ⚠️ ليس مخزوناً حقيقياً!
التأثير السلبي:

قد يُعتبر خداعاً تسويقياً
يفقد ثقة العملاء عند اكتشافه
غير قانوني في بعض الأنظمة
4. تجربة المستخدم (UX)
مشاكل محتملة:
❌ لا توجد رسالة تأكيد واضحة بعد الإرسال
❌ لا يوجد validation للحقول (مثل: صيغة رقم الهاتف الجزائري)
❌ لا توجد معاينة للطلب قبل التأكيد
❌ النموذج يُعاد تعيينه تلقائياً (قد يفقد العميل بياناته)
5. تحسين محركات البحث (SEO)
html
❌ ناقص:
- لا توجد meta description
- لا توجد Open Graph tags (للمشاركة على السوشيال ميديا)
- لا يوجد schema markup للمنتجات
- عنوان الصفحة عام جداً

✅ يجب إضافة:
<meta name="description" content="...">
<meta property="og:title" content="...">
<meta property="og:image" content="...">
🎯 توصيات استراتيجية
أولوية عالية 🔴
إضافة صور حقيقية للمنتج - ضروري للمصداقية
إصلاح مشكلة الأمان - حماية من السبام
إضافة سياسة الاسترجاع - مطلوب قانونياً
validation صحيح للنموذج - تحسين جودة البيانات
أولوية متوسطة 🟡
شهادات العملاء وتقييماتهم
صفحة "من نحن" و"اتصل بنا"
حاسبة التوصيل حسب الولاية
تحسينات SEO
أولوية منخفضة 🟢
مدونة عن فوائد التمور
برنامج ولاء للعملاء المتكررين
خيارات دفع إلكتروني
📈 التقييم النهائي
المعيار	التقييم	الملاحظة
التصميم	⭐⭐⭐⭐☆	جذاب وعصري
الوظائف التقنية	⭐⭐⭐☆☆	تعمل لكن بها ثغرات
الأمان	⭐⭐☆☆☆	يحتاج تحسين عاجل
المصداقية	⭐⭐☆☆☆	ناقصة كثيراً
تجربة المستخدم	⭐⭐⭐⭐☆	سهلة وبسيطة
المجموع	⭐⭐⭐☆☆	جيدة لكن تحتاج تحسينات
💡 خلاصة
الصفحة مصممة بشكل جيد من الناحية البصرية وتستخدم تقنيات تسويقية ذكية، لكنها تفتقر إلى عناصر بناء الثقة والأمان.

أهم خطوة الآن: إضافة صور حقيقية + شهادات عملاء + تأمين النموذج.

هل تريد مساعدة في تطبيق أي من هذه التحسينات؟

كيف اضيف صور تمور للصفحة

دليل إضافة صور التمور للصفحة 📸
سأريك عدة طرق لإضافة الصور، من الأسهل للأفضل:

🎯 الطريقة 1: استخدام روابط صور من الإنترنت (الأسرع)
المزايا:
✅ سريعة وبدون رفع ملفات
✅ لا تحتاج استضافة

العيوب:
❌ قد تُحذف الصور من المصدر الأصلي
❌ بطء في التحميل أحياناً

مصادر صور مجانية:
Unsplash: https://unsplash.com/s/photos/dates-fruit
Pexels: https://www.pexels.com/search/dates/
Pixabay: https://pixabay.com/images/search/dates/
كيفية الاستخدام:
ابحث عن صورة تمور
انقر بالزر الأيمن → "نسخ عنوان الصورة" (Copy image address)
استخدم الرابط في الكود
🎯 الطريقة 2: رفع الصور على خدمة استضافة مجانية
أفضل الخدمات المجانية:
أ) ImgBB ⭐ (الأفضل)
الموقع: https://imgbb.com
خطوات:
افتح الموقع
اضغط "Start uploading"
ارفع صورة التمور
انسخ رابط "Direct link"
ب) Imgur
الموقع: https://imgur.com
نفس الخطوات
ج) Cloudinary (احترافي)
الموقع: https://cloudinary.com
يعطيك 25GB مجاناً
🎯 الطريقة 3: استخدام Google Drive (مضمونة)
الخطوات:
ارفع الصورة على Google Drive
انقر بالزر الأيمن → "مشاركة" → "الحصول على رابط"
اختر "يمكن لأي شخص الوصول"
حول الرابط من:
https://drive.google.com/file/d/FILE_ID/view?usp=sharing
إلى:

https://drive.google.com/uc?export=view&id=FILE_ID
💻 الآن: كيف تضيف الصور في كود صفحتك؟
سأعطيك الكود المحسّن مع أماكن الصور:


Untitled
Text 
الآن دعني أضيف أيضاً صورة على كل باقة:


Untitled
Text·Version 4 
تمام! الآن دعني أضيف قسم شهادات العملاء بالصور:


Untitled
Text·Version 5 
ممتاز! الآن أعطيك دليل استبدال الصور 📝:

📌 كيف تستبدل الصور بصورك الخاصة؟
1️⃣ صور المنتج الرئيسية (4 صور)
ابحث عن هذا السطر في الكود:

html
<img src="https://images.unsplash.com/photo-..." alt="تمور دقلة نور" class="...">
استبدل الرابط https://images.unsplash.com/... بـ:

رابط صورتك من ImgBB
أو رابط من Google Drive
أو أي رابط صورة مباشر
2️⃣ صور الباقات (3 صور)
نفس الطريقة، ابحث عن:

html
<img src="https://images.unsplash.com/..." alt="باقة 6 كغ" class="...">
3️⃣ صور العملاء (تلقائية)
الصور الحالية تُنشأ تلقائياً من الأسماء باستخدام:

https://ui-avatars.com/api/?name=Ahmed&background=16a34a&color=fff
يمكنك استبدالها بصور حقيقية لعملائك (بإذنهم!)

🎨 نصائح للصور الاحترافية:
✅ مواصفات الصور المثالية:
الحجم: 800x600 بكسل (أو أكبر)
الصيغة: JPG أو PNG
الحجم: أقل من 500 كيلوبايت لكل صورة
الجودة: واضحة ومضاءة جيداً
📸 ماذا تصور؟
تمور قريبة - لإظهار الجودة
صندوق التعبئة - لإظهار التغليف
الصناديق الثلاثة - لإظهار الأحجام
عملية التوصيل - لبناء الثقة
🚀 إذا لم تملك صوراً حالياً:
استخدم الصور المؤقتة التي وضعتها، ثم استبدلها تدريجياً بصور حقيقية

💡 مثال عملي لاستبدال صورة:
قبل:
html
<img src="https://images.unsplash.com/photo-1609103803251-fa950189ebc1?w=400" alt="تمور دقلة نور">
بعد (باستخدام ImgBB):
html
<img src="https://i.ibb.co/xyz123/my-dates.jpg" alt="تمور دقلة نور">
هل تريد مساعدة في:

📤 رفع الصور على خدمة معينة؟
🎨 تحسين مظهر الصور في الصفحة؟
📷 نصائح للتصوير الاحترافي للمنتج؟
كود إضافة معرض صور في الصفحة

كود معرض صور احترافي للصفحة 📸
سأضيف لك معرض صور تفاعلي بعدة أنماط. اختر النمط الأنسب لك:

🎨 النمط 1: معرض شبكي مع Lightbox (الأكثر احترافية)

Untitled
Text·Version 8 
ممتاز! 🎉 تم إضافة معرض صور تفاعلي احترافي للصفحة!

✨ المميزات المضافة:
1️⃣ شبكة صور جذابة (8 صور)
✅ تصميم متجاوب (2 أعمدة موبايل، 4 أعمدة كمبيوتر)
✅ تأثير Hover جميل عند المرور بالماوس
✅ وصف نصي يظهر عند التمرير
2️⃣ Lightbox احترافي (نافذة تكبير)
✅ اضغط على أي صورة لتكبيرها بشاشة كاملة
✅ أسهم للتنقل بين الصور (→ ←)
✅ زر إغلاق (X) أعلى اليمين
✅ يمكن الإغلاق بالضغط خارج الصورة
3️⃣ التنقل بالكيبورد
✅ → السهم الأيمن = الصورة السابقة
✅ ← السهم الأيسر = الصورة التالية
✅ Esc = إغلاق المعرض
4️⃣ تصميم عصري
✅ خلفية متدرجة (gradient) من كهرماني لأخضر
✅ انيميشن سلس عند الحركة
✅ ظل وإضاءة احترافية
🎨 كيف تستبدل الصور بصورك؟
ابحث عن هذا الجزء في الكود:
javascript
// صور المعرض
const galleryImages = [
    'https://images.unsplash.com/photo-...w=1200',  // صورة 1
    'https://images.unsplash.com/photo-...w=1200',  // صورة 2
    // ... إلخ
];
استبدل كل رابط برابط صورتك:
مثال:

javascript
const galleryImages = [
    'https://i.ibb.co/abc123/dates1.jpg',  // صورة التمر الطازج
    'https://i.ibb.co/def456/dates2.jpg',  // صورة التعبئة
    'https://i.ibb.co/ghi789/dates3.jpg',  // صورة المزرعة
    // ... أضف حتى 8 صور أو أكثر
];
📸 نصائح لإضافة المزيد من الصور:
إضافة صورة جديدة (صورة رقم 9):
1. أضف الصورة في HTML:

html
<!-- صورة 9 -->
<div class="gallery-item" onclick="openLightbox(8)">
    <img src="رابط_صورتك_هنا" alt="وصف الصورة" class="w-full h-48 md:h-64 object-cover">
    <div class="gallery-overlay">
        <p class="text-white text-sm font-bold">عنوان الصورة</p>
    </div>
</div>
2. أضف رابط الصورة في JavaScript:

javascript
const galleryImages = [
    'https://...',  // صورة 1
    'https://...',  // صورة 2
    // ... إلخ
    'https://...',  // صورة 8
    'رابط_صورتك_الجديدة_هنا'  // صورة 9 ← أضفها هنا
];
🎯 أفكار صور مقترحة للمعرض:
#	الصورة	الوصف
1	تمور مقربة	لإظهار الجودة والحجم
2	الصناديق الثلاثة	مقارنة الأحجام
3	التعبئة	لإظهار النظافة
4	المزرعة/النخيل	الأصالة والمصدر
5	العميل يستلم	بناء الثقة
6	تمر مع قهوة	الاستخدام اليومي
7	عملية الفرز	الجودة
8	شهادة/ترخيص	المصداقية
🚀 تحسينات إضافية متاحة:
هل تريد إضافة:
عداد الصور (1/8، 2/8، إلخ) في الـ Lightbox؟
تشغيل تلقائي (Slideshow) للصور؟
تأثيرات zoom عند الضغط المطول؟
تصنيفات (صور المنتج، صور العملاء، صور التوصيل)؟
معرض فيديو بجانب الصور؟
أخبرني أي تحسين تريده! 🎨✨

أين الصق الكود في ملفي الاصلي

دليل لصق الكود في ملفك الأصلي 📋
سأشرح لك بالتفصيل أين تلصق كل جزء من الكود الجديد:

📍 الجزء 1: CSS (الأنماط)
ابحث عن هذا في ملفك:
html
    <style>
        body { font-family: 'Cairo', sans-serif; scroll-behavior: smooth; overflow-x: hidden; }
        .video-bg-container { position: relative; width: 100%; height: 550px; overflow: hidden; }
        .video-bg { position: absolute; top: 50%; left: 50%; min-width: 100%; min-height: 100%; z-index: -1; transform: translate(-50%, -50%); object-fit: cover; }
        .overlay-dark { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); z-index: 1; }
        @media (max-width: 768px) {
            .mobile-sticky-btn { position: fixed; bottom: 0; left: 0; right: 0; z-index: 100; display: grid; grid-template-columns: 1fr 1fr; gap: 8px; padding: 12px; background: white; box-shadow: 0 -5px 15px rgba(0,0,0,0.1); }
        }
        .scale-up { transform: scale(1.05); transition: all 0.2s ease; }
        .input-error { border: 2px solid #ef4444 !important; background-color: #fef2f2 !important; }
    </style>
أضف هذا الكود قبل </style>:
css
        
        /* معرض الصور */
        .gallery-item { position: relative; overflow: hidden; cursor: pointer; border-radius: 1rem; }
        .gallery-item img { transition: transform 0.3s ease; }
        .gallery-item:hover img { transform: scale(1.1); }
        .gallery-overlay { position: absolute; bottom: 0; left: 0; right: 0; background: linear-gradient(to top, rgba(0,0,0,0.7), transparent); padding: 1rem; transform: translateY(100%); transition: transform 0.3s ease; }
        .gallery-item:hover .gallery-overlay { transform: translateY(0); }
        
        /* Lightbox */
        .lightbox { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); z-index: 9999; justify-content: center; align-items: center; }
        .lightbox.active { display: flex; }
        .lightbox img { max-width: 90%; max-height: 90vh; border-radius: 1rem; box-shadow: 0 0 50px rgba(255,255,255,0.3); }
        .lightbox-close { position: absolute; top: 20px; right: 30px; color: white; font-size: 40px; cursor: pointer; z-index: 10000; }
        .lightbox-nav { position: absolute; top: 50%; transform: translateY(-50%); background: rgba(255,255,255,0.2); color: white; padding: 1rem; cursor: pointer; font-size: 2rem; border-radius: 50%; }
        .lightbox-prev { left: 20px; }
        .lightbox-next { right: 20px; }
النتيجة ستصبح:

html
    <style>
        body { font-family: 'Cairo', sans-serif; scroll-behavior: smooth; overflow-x: hidden; }
        /* ... الكود القديم ... */
        .input-error { border: 2px solid #ef4444 !important; background-color: #fef2f2 !important; }
        
        /* معرض الصور */
        .gallery-item { position: relative; overflow: hidden; cursor: pointer; border-radius: 1rem; }
        /* ... باقي الكود الجديد ... */
        .lightbox-next { right: 20px; }
    </style>
📍 الجزء 2: HTML (معرض الصور)
ابحث عن هذا السطر:
html
    <main class="container mx-auto px-4 py-12 max-w-6xl">
        <h2 class="text-3xl font-black text-center mb-10 text-green-900">إختر العرض المناسب لك 📦</h2>
أضف هذا الكود قبل <h2 class="text-3xl...">:
html
        <!-- معرض الصور التفاعلي -->
        <section class="mb-16 bg-gradient-to-br from-amber-50 to-green-50 p-8 md:p-12 rounded-[3rem]">
            <h2 class="text-3xl font-black text-center mb-3 text-green-900">معرض الصور 📸</h2>
            <p class="text-center text-gray-600 mb-10">اضغط على أي صورة للتكبير والمشاهدة بالتفصيل</p>
            
            <!-- الشبكة الرئيسية -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                <!-- صورة 1 -->
                <div class="gallery-item" onclick="openLightbox(0)">
                    <img src="https://images.unsplash.com/photo-1609103803251-fa950189ebc1?w=600" alt="تمور دقلة نور عالية الجودة" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">دقلة نور فاخرة</p>
                    </div>
                </div>
                
                <!-- صورة 2 -->
                <div class="gallery-item" onclick="openLightbox(1)">
                    <img src="https://images.unsplash.com/photo-1577003833154-a9a2e0fe1998?w=600" alt="تمور طازجة من بسكرة" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">طازجة 100%</p>
                    </div>
                </div>
                
                <!-- صورة 3 -->
                <div class="gallery-item" onclick="openLightbox(2)">
                    <img src="https://images.unsplash.com/photo-1628599091862-62d5b9e0e07f?w=600" alt="تعبئة وتغليف احترافي" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">تعبئة نظيفة</p>
                    </div>
                </div>
                
                <!-- صورة 4 -->
                <div class="gallery-item" onclick="openLightbox(3)">
                    <img src="https://images.unsplash.com/photo-1607082349566-187342175e2f?w=600" alt="صناديق جاهزة للتوصيل" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">جاهز للتوصيل</p>
                    </div>
                </div>
                
                <!-- صورة 5 -->
                <div class="gallery-item" onclick="openLightbox(4)">
                    <img src="https://images.unsplash.com/photo-1587241321921-91a834d82ccb?w=600" alt="نخيل بسكرة" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">من واحات بسكرة</p>
                    </div>
                </div>
                
                <!-- صورة 6 -->
                <div class="gallery-item" onclick="openLightbox(5)">
                    <img src="https://images.unsplash.com/photo-1591206369811-4eeb2f03bc95?w=600" alt="جودة مضمونة" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">جودة مضمونة</p>
                    </div>
                </div>
                
                <!-- صورة 7 -->
                <div class="gallery-item" onclick="openLightbox(6)">
                    <img src="https://images.unsplash.com/photo-1599809275671-b5942cabc7a2?w=600" alt="وجبة صحية" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">غذاء صحي</p>
                    </div>
                </div>
                
                <!-- صورة 8 -->
                <div class="gallery-item" onclick="openLightbox(7)">
                    <img src="https://images.unsplash.com/photo-1610832958506-aa56368176cf?w=600" alt="تمور مع القهوة" class="w-full h-48 md:h-64 object-cover">
                    <div class="gallery-overlay">
                        <p class="text-white text-sm font-bold">رفيق القهوة المثالي</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Lightbox (نافذة تكبير الصور) -->
        <div id="lightbox" class="lightbox" onclick="closeLightbox(event)">
            <span class="lightbox-close" onclick="closeLightbox(event)">&times;</span>
            <span class="lightbox-nav lightbox-prev" onclick="changeImage(-1); event.stopPropagation()">&#10094;</span>
            <img id="lightbox-img" src="" alt="صورة مكبرة">
            <span class="lightbox-nav lightbox-next" onclick="changeImage(1); event.stopPropagation()">&#10095;</span>
        </div>
📍 الجزء 3: JavaScript (الوظائف)
ابحث عن هذا في الـ <script>:
javascript
    <script>
        const packSelect = document.getElementById('pack_select');
        const quantityInput = document.getElementById('quantity');
        const qtyDisplay = document.getElementById('quantity_display');
        const totalPriceDisplay = document.getElementById('total_price');
        const totalPriceBox = document.getElementById('total_price_box');
        const orderForm = document.getElementById('orderForm');

        function changeQty(amount) {
أضف هذا الكود بعد السطر const orderForm = ... وقبل function changeQty:
javascript
        // صور المعرض
        const galleryImages = [
            'https://images.unsplash.com/photo-1609103803251-fa950189ebc1?w=1200',
            'https://images.unsplash.com/photo-1577003833154-a9a2e0fe1998?w=1200',
            'https://images.unsplash.com/photo-1628599091862-62d5b9e0e07f?w=1200',
            'https://images.unsplash.com/photo-1607082349566-187342175e2f?w=1200',
            'https://images.unsplash.com/photo-1587241321921-91a834d82ccb?w=1200',
            'https://images.unsplash.com/photo-1591206369811-4eeb2f03bc95?w=1200',
            'https://images.unsplash.com/photo-1599809275671-b5942cabc7a2?w=1200',
            'https://images.unsplash.com/photo-1610832958506-aa56368176cf?w=1200'
        ];
        let currentImageIndex = 0;

        // فتح Lightbox
        function openLightbox(index) {
            currentImageIndex = index;
            document.getElementById('lightbox').classList.add('active');
            document.getElementById('lightbox-img').src = galleryImages[index];
            document.body.style.overflow = 'hidden';
        }

        // إغلاق Lightbox
        function closeLightbox(event) {
            if (event.target.id === 'lightbox' || event.target.classList.contains('lightbox-close')) {
                document.getElementById('lightbox').classList.remove('active');
                document.body.style.overflow = 'auto';
            }
        }

        // التنقل بين الصور
        function changeImage(direction) {
            currentImageIndex += direction;
            if (currentImageIndex < 0) currentImageIndex = galleryImages.length - 1;
            if (currentImageIndex >= galleryImages.length) currentImageIndex = 0;
            document.getElementById('lightbox-img').src = galleryImages[currentImageIndex];
        }

        // التنقل بالكيبورد
        document.addEventListener('keydown', function(e) {
            if (document.getElementById('lightbox').classList.contains('active')) {
                if (e.key === 'ArrowLeft') changeImage(1);
                if (e.key === 'ArrowRight') changeImage(-1);
                if (e.key === 'Escape') closeLightbox({target: {id: 'lightbox'}});
            }
        });
📋 ملخص سريع - 3 خطوات فقط:
1️⃣ في <style>: أضف كود CSS للمعرض قبل </style>
                ↓
2️⃣ في <main>: أضف كود HTML للمعرض قبل "إختر العرض المناسب"
                ↓
3️⃣ في <script>: أضف كود JavaScript بعد const orderForm
🎯 طريقة سهلة بالنسخ واللصق:
افتح ملفك index.html بمحرر نصوص (Notepad++, VS Code, إلخ)
اضغط Ctrl+F للبحث
ابحث عن .input-error
بعده مباشرة الصق كود CSS
ابحث عن إختر العرض المناسب
قبله الصق كود HTML
ابحث عن const orderForm
بعده الصق كود JavaScript
احفظ الملف (Ctrl+S)
✅ للتأكد من نجاح التطبيق:
بعد اللصق، افتح الملف في المتصفح:

✔️ يجب أن ترى قسم "معرض الصور 📸"
✔️ عند الضغط على أي صورة تفتح بشاشة كاملة
✔️ الأسهم تنقلك بين الصور
🆘 مشاكل محتملة وحلولها:
المشكلة	السبب	الحل
المعرض لا يظهر	لم تلصق HTML	راجع الخطوة 2
الصور لا تكبر	لم تلصق JavaScript	راجع الخطوة 3
التصميم غريب	لم تلصق CSS	راجع الخطوة 1
خطأ في Console	قوس ناقص	تأكد من نسخ الكود كاملاً
هل تريد مني إرسال الملف الكامل جاهز؟ 📄