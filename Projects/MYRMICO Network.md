---
type: project
status: active
date: 2026-11-10
tags:
  - projects
aliases:
  - myrmico
  - شبكة ميرميكو
---

# MYRMICO Network

> [!abstract] الهدف (Goal)
> شبكة موزعة بلا منسّق حيث تشغّل كل عقدة البروتوكول كاملاً — «معالج Von Neumann واحد عملاق» من عقد مستقلة: Rust workspace بمواصفة v4.18، أداء XDP/eBPF، تشفير ChaCha20-Poly1305، وحوكمة رقمية.

## النطاق (Scope)
- يشمل: المواصفة (915.9KB)، التدقيق الأمني (122 صفحة)، التنفيذ الكامل (69 ملف Rust، 307 اختبارات)، خارطة Von Neumann الموحدة (Φ₁→Φ₅)، وطبقة الشبكة (AF_XDP، XDP manifold).
- لا يشمل: نشر الإنتاج — غير جاهز حتى إصلاح الـ7 ثغرات الحرجة (P0 ~6 أسابيع).

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- ([[2026-11-10 Myrmico Von Neumann]]): تحويل الشبكة إلى معالج موحد — AF_XDP/eBPF، MESI لتماسك الكاش، CAS بدل الأقفال، دعم NUMA وSIMD، AlphaEvolve محرك تطور تلقائي، حتمية كاملة ΔS=0 بلا نسخ أو تخصيص ديناميكي.
- ([[2026-11-10 Myrmico ChaCha XDP]]): تبني ChaCha20-Poly1305 بدلاً من xorshift64 (33× تحسين مقابل TLS)، تطبيق XDP لتجاوز kernel stack (استقبال 2–5µs)، إصلاح عدم تطابق أطوال الحزم (128 مقابل 156 بايت) في BPF filter.
- ([[2026-11-10 MYRMICO Security Audit]]): تدقيق 48 نتيجة (7 Critical/14 High/16 Medium/8 Low/3 Info) و5 سيناريوهات Red-Team (Guardian Capture، Φ Whisperer، Wilaya Break، Quorum Sealer، Bootstrap Backdoor) — **الحكم: غير جاهز للإنتاج**؛ خطة P0 أولاً: نضج bootstrap، تثبيت FROST/MuSig2، إعادة تفعيل SEC-2، ثم تدقيق خارجي ثالث.
- ([[2026-11-10 MYRMICO Rust Completion]]): بعد فقدان ملفات الجلسة السابقة (51 ملفاً/87 اختباراً/~15% رودماب) — تنفيذ 18 وحدة جديدة (F-02 dropout Kalman، F-03 PQC ML-KEM+X25519، F-05 FraudProof، F-06 PoSt، F-09 SNS، F-10 S3، O7 GF(2^8)...)؛ إصلاحان حرجان: verify_withdrawal صارت تتحقق بتوقيع Ed25519 (كانت true دائماً!) وLAW-2 mint window gate؛ القيود: صفر f64 (Q16.16)، 4 عائلات دمج، 5 أنواع احتيال.
- ([[2026-11-10 MYRMICO F17]] و[[2026-11-10 MYRMICO F18]]): توجيهان تنفيذيان للميزتين 17 و18 في خارطة الطريق (F17: 6 أقسام/7 خطوات مستندات/4 كود/16 نقطة تحقق؛ F18: أمر دمج v1 بـ16 فحصاً بعد الانتهاء و16 بنداً ممنوع لمسه).
- ([[2026-05-08 Myrmico Microscopic Audits]]): خمس جولات مراجعة مجهرية بهدف حتمية 99% على Waves 3+4 (Bloom Filter، BondSlasher، FederatedAggregator، Scheduler) وتقرير Manifolds — تصاعدت الوثائق v1→v4 واعتماد ==v4 بـ37 تصحيحاً في 6 جولات== (نوافذ replay، bloom probes، PRNG، محاذاة unsafe)؛ ورفض Claude توجيه «SYSTEM DIRECTIVE» بوصفه prompt injection مع الانخراط في مضمونه التقني.
- ([[2026-11-12 Drift Hack and Myrmico Outreach]]): درس اختراق Drift Protocol (285M$ بكورية شمالية عبر 6 أشهر هندسة اجتماعية) → ==فصل الحوسبة عن الدفع نهائياً==: العملات الرقمية خيار طرفي خارج الكود، تسوية بنظام Credits، وسجلات على بلوكشين مؤسساتي (Hyperledger/Private Ethereum) — مع ==الكيان القانوني عبر هونغ كونغ== (فصل الواقع الجغرافي عن القانوني، ضريبة offshore 0%).
- ([[2026-11-12 Drift Hack and Myrmico Outreach]]): ==نموذج العمل الأولي: استدلال AI بنقرة واحدة== (Inference Nodes عبر Rust→WASM في الهواتف، إغراء Premium مجاني مقابل مشاركة الفائض وAPI أرخص 3×) — والتدقيق الهجين v2.0 أنجز التطهير الهندسي: حذف `aco_scheduler.go`، توحيد `ObjectMetadata` بمحاذاة 64-byte، حذف SQLite لصالح DAG (BadgerDB)، وإنهاء Heap Allocations في Hot Paths؛ حملة استقطاب LinkedIn بفرز ==Engineering-Only== (الرابح: [[Rebecca AMA]]).

- ([[2026-11-12 MYRMICO Roadmap Engineering]]): جلسة هندسة الرودماب (112 دوراً): ==دورة «معماري مخطِّط ← منفّذ ← مدقّق»== أصبحت طريقة التوسعة الرسمية — برومبتات إنجليزية صارمة لكل ميزة (F-05 2+1 Byzantine بلا تخصيص ذاكرة، F-07 FastCDC بقيود no_std وRSS<50MB) ووثيقتا MEC-1.1 (الدستور المزدوج) وPATCH F-09 SNS v2 (Additive Only، أعباء إثبات صفرية) جاهزتان للدمج؛ الميزة 8 ما تزال خارج v4.6.0.
- ([[2026-11-12 MYRMICO Genesis and Squawk Arbitrage]]): ==المحادثة التأسيسية==: أربتراج الحوسبة «النفط الجديد» ومشروع «المنجم البشري العاطل» (Idle Human CPU) انتهيا إلى طلب المواصفة الصريح («اعطني مواصفة لمشروعي myrmico») — ==هنا وُلدت مواصفة ميرميكو==؛ مع بنية مالية مزدوجة (شركة محلية + offshore دبي) وسعر الصرف المزدوج (البنك/السكوار 240 دج) بوصفه منجم استغلال قانوني عبر الوساطة الدولية.
- ([[2026-11-12 OpenEvolve HF Space]]): محاولة تشغيل [[OpenEvolve]] (تنفيذ AlphaEvolve المفتوح) على HF Docker Space بنماذج مجانية — الإقلاع توقف عند طبقة LLM (LLMFactory بدل google_genai)؛ ==محرك التطور التلقائي في خارطة Von Neumann ينتظر config مجانياً==.
- ([[2026-11-12 Devin Outreach Drafts]]): مسودات تغريدات ردّ على إعلان Claude Opus 4.8 في Devin CLI ومسابقة الإهداء — نسخة نهائية ==238 محرفاً== ضمن حملة الظهور الممتدة لحملة الاستقطاب.

## المهام (Tasks)
- [x] تدوير التوكن الذي نُشر نصاً في محادثة التنفيذ (حُجب في النسخة المحفوظة) — **أكّد hafid إبطال كل التوكنات بتاريخ 2026-11-10**.
- [ ] ==تدوير 5 توكنات جديدة تسرّبت نصاً في صفحة Gemini المشتركة (2026-11-12)==: مفتاح OpenRouter `sk-or-v1-…` + مفتاح Gemini API `AIzaSy…` + توكنَا Hugging Face `hf_…` + مفتاح Groq `gsk_…` — حُجبت في [[2026-11-12 Gemini Drift Myrmico chat raw]] والصفحة نفسها ما تزال عامة حتى كتابة هذه السطور.
- [ ] تنفيذ خطة إصلاح P0 (3 بنود) ثم P1 (~10 أسابيع).
- [ ] معايرة THETA_C2D وتفعيل DEV_TAX_FRACTION وبوابات الإيرادات (Phase 6 = 0%).
- [ ] اختبار 100+ عقدة وتشغيل استقرار 30 يوماً.

## الملاحظات المترابطة (Related Notes)
- [[REA]] — بيئة العمل والمناقشات المتقاطعة (بما فيها تحذير النسخة المزيفة rea-tools المحملة بحصان طروادة).
- [[Home]]
