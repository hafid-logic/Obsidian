---
type: project
status: active
date: 2026-10-29
tags:
  - projects
aliases:
  - ginux contribution
  - مساهمة ginux
---

# Ginux Contribution

> [!abstract] الهدف (Goal)
> برنامج مساهمات منضبط في [gmkurtzer/ginux](https://github.com/gmkurtzer/ginux): فرص مساهمة تُقاس بالأدلة، نصوص تُعتمد هنا قبل النشر، وسقف نشر صارم — بوكيل تنفيذي (z.ai) ومشرف تحليلي (Claude) وهافيد ناشراً يدوياً.

## النطاق (Scope)
- يشمل: تحليل upstream (بدأ بتقييم دور Rust 2026-10-29)، بنية ginux-watch الداعمة، صياغة وتعتميد النصوص المنشورة، تتبع أثر المساهمات (#4 و#43 كودياً).
- لا يشمل: النشر المباشر — ينشر Abdelhafid يدوياً فقط بعد اعتماد نصّ محدد، والمراقبة اليومية مشروع [[Ginux Watch]] المستقل.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- 2026-10-29 ([[2026-10-29 Ginux Rust Evaluation]]): انطلاق البرنامج بتوجيهَي «تقييم دور Rust في Ginux» v1/v2 — نواة 139 ألف سطر بناها Gregory Kurtzer في 11 يوماً بمساعدة AI، unsafe ≈9–12%.
- 2026-11-02 تقديري ([[2026-11-02 Ginux Contribution v3.3]]): منهجية ginux-watch v3 في docs/METHODOLOGY.md؛ سلّم الأدلة hypothesis←confirmed←branch←draft-PR←published←merged؛ حد طلبين مفتوحين حتى دمج الأول؛ ردّ على المراجعات ≤24 ساعة؛ توقيع commits باسم Abdelhafid DJIDEL (noreply) وإفصاح AI إلزامي.
- 2026-11-02 تقديري: فحص diff #54 أثبت أن Gregory أصلح مواقع then_some الخمسة بنفسه → إلغاء PR المواقع الخمسة؛ workflow issue-14 مكسور → حذفه مرشح PR-1.
- 2026-11-06 ([[2026-11-06 Ginux Contribution v4]]): سلسلة v4.1→v4.5 على نص سؤال overflow-checks — الاكتشاف الأهم: المالك أصلح الطفح كودياً في #54 (47fc22c8) قبل زوال السطر في دمج #152، فصار السؤال «هل الحذف مقصود؟»؛ النص المعتمد النهائي -3 (871 حرفاً) يضم normalize_archive_path مع الإقرار بعدم مراجعة scan_layer؛ **النشر ممنوع قبل 2026-11-10T06:23:25Z** (السقف الأسبوعي المتحرك، 5 تجاوزات سابقة رفض منح سادس).
- قاعدة الإيقاع: سقف نشر يومي 1 وأسبوعي محدود؛ مراجعات يومية 09:00 توقيت الجزائر (D4).

## المهام (Tasks)
- [ ] نشر issue overflow-checks (النص المعتمد -3) بعد 2026-11-10T06:23Z مع إعادة البوابة الحية (main + السطور 426/436/683 + لا issue مماثل).
- [ ] PR-1: حذف workflow issue-14 المكسور (بانتظار إذن hafid).
- [ ] PR-2 بعد دمج #54: استخراج linux_decimal + اختبارات host بنمط pe.rs.
- [ ] فرصة 3 (fuzz vfs-index): تصميم فقط حتى 2026-11-12، لا تشغيل.

## الملاحظات المترابطة (Related Notes)
- [[Ginux Watch]] — البنية التحتية للمراقبة التي وُلدت من هذا البرنامج.
- [[Ginux]] · [[gmkurtzer]] · [[overflow-checks]] · [[HDAE Gates]]
- [[Home]]

%% الجدول الزمني للبرنامج: تقييم (10-29) → خطة v3.3 (11-02) → اعتماد نص overflow-checks (11-06) → النشر المراقب (11-10+) %%
