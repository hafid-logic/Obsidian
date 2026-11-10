---
type: project
status: active
date: 2026-11-07
tags:
  - projects
aliases:
  - ginux-watch
  - مراقبة ginux
---

# Ginux Watch

> [!abstract] الهدف (Goal)
> بنية مراقبة **قراءة-فقط** لمستودع [gmkurtzer/ginux](https://github.com/gmkurtzer/ginux): تلتقط أي رد أو دمج أو تحرك في الخيوط #222 و#207 وPR #227 ورأس upstream/main، وتحفظ الأدلة حرفياً في `inbox/` — دون أي تدخل في upstream إطلاقاً.

## النطاق (Scope)
- يشمل: مستودع المراقبة [hafid-logic/ginux-watch](https://github.com/hafid-logic/ginux-watch) (matrix، outbox، directives، inbox، AGENTS، METHODOLOGY)، مهام cron مجدولة، team-watcher في Actions، ونظام الإشعار trip-notify.
- لا يشمل: أي نشر أو ردّ أو PR جديد في upstream — ممنوع بموجب قواعد القاطع؛ المراقبة سجل استخباراتي صامت يقرره hafid وحده.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- 2026-11-06: اعتماد قاطع الدائرة — أي رد جديد على الخيوط الثلاثة يوقف كل شيء: حفظ حرفي في inbox وإبلاغ بعنوانه ومؤلفه وتاريخه فقط.
- 2026-11-07 (v6.5-1): حجب البريد الشخصي إلزامي في كل الشجرة — 240 إصابة → 0 في 46 ملفاً؛ لا بريد غير noreply في أي ملف متتبَّع.
- 2026-11-07 (v6.5-2): حقل التقرير الموحّد هو `base_head` (كان `head_pushed`)؛ التقارير القديمة تبقى كما هي.
- 2026-11-07 (v6.5b-1): قاعدة CLEAR/BLIND — لا يُعلن وضوح الحالة إلا بقراءة API أو `git ls-remote`؛ HTML للعرض فقط.
- 2026-11-07 (v6.5b-2): مهام المراقبة بلا توكن نهائياً — المصدر `matrix/upstream-watch.json` + `ls-remote`.
- 2026-11-07 (v6.5b-3): الإشعار الآلي يفتح issue داخل ginux-watch عند أي تغيّر مرصود (`permissions: issues: write` لهذا الـjob وحده).
- 2026-11-07: مفتاح النشر `ginux_watch_deploy-20261107` مفعّل والدفع يعمل بعد إصلاح wrapper (تطبيع المسار + بثّ متزايد).
- [[2026-11-07 Ginux Watch v6.5]]: تنفيذ v6.5 + v6.5b اكتمل والتُزم على origin/main.
- 2026-11-10 (v7.1، قرار نهائي): **تحول المصادقة من SSH إلى PAT دقيق النطاق** — لا SSH ولا بدائل؛ التوكن يُجسَّد مرة واحدة في `work/keys/gh-pat` (600)، وبعد كل دفع: `git credential reject` + حذف `work/keys` + إبلاغ بأنه جاهز للإبطال.
- 2026-11-10 (v7.2): ginux-verify أصبح legacy (dispatch فقط، بلا جدولة)؛ وضع أحداث أسبوعي فقط (cron 519716، الاثنين 09:00 Algiers) بدل الجولات الكثيفة؛ ركن C2 بـ3 أسباب و3 شروط فك؛ C1/C3 مُسقطتان.
- 2026-11-10 (v7.3-2d): دلالة النبض الصحيحة — الإنذار (12 ساعة) على `last_success` فقط، فشل التشغيل ليس نبضاً؛ heartbeat يسجل last_run/last_success/last_conclusion منفصلة مع اختبار offline 7/7.
- 2026-11-10 (v7.3): إصلاح سباق الدفع العابر في team-watcher بحلقة 3 محاولات `pull --rebase -X theirs` + `rebase --abort` بين المحاولات (تحقق إنتاجي: run 30 + المجدول نجحا).
- 2026-11-10: أرقام اللوحات الرسمية مسجلة في limits_official — google RPM 5 / TPM 250K / RPD 20، nvidia 40 RPM، openrouter 20/50؛ والتنبيه: RPD 20 < eval cap 40 (قرار مالك معلق).
- [[2026-11-10 Ginux Watch v7]]: v7.1→v7.3 كاملة مدفوعة حتى `main=834e7d6`؛ المشرف الظل اجتاز اختبار الفخ؛ الـeval الثاني: nvidia 17/17 ok، google 16/17 rate_limited.

## المهام (Tasks)
- [x] إتمام `gh auth` عبر device-flow (يحتاج تفاعل hafid). ← عفا عنه تحول v7.1 إلى PAT.
- [x] تأكيد أول تشغيل team-watcher بعد الدفع + رقم issue الاختبار التجريبي (v6.5b-3). ← أُنجز في جولة v7.
- [ ] **إبطال التوكنين المسرّبين نصاً في صفحة محادثة v7 المشتركة** (أولوية أمنية).
- [ ] قرار المالك: قبول بوابات 12/12.1/12.25/12.5 + Gate 11 KVM/tolerance + تعارض RPD 20 < eval cap 40.
- [ ] مراقبة شروط فك C2 الثلاثة — عند أي إشارة: مذكرة ملاءمة ≤1 صفحة بلا بناء.
- [ ] رفع توكن الجلسات القادمة كملف في upload/ لا نصاً في المحادثة.
- [ ] إزالة مفتاح deploy القديم 20261106 من GitHub إن لم يُزل.

## الملاحظات المترابطة (Related Notes)
- [[Ginux]] — المستودع المرصود نفسه (مرجع).
- [[gmkurtzer]] — مالك upstream ومصدر دفعة الردود.
- [[HDAE Gates]] — ما يشغّل gmkurtzer حالياً (روابط غير محلولة مقصودة).
- [[overflow-checks]] — موضوع الخيوط الأصلية #222/#227.
- [[2026-11-10 Ginux Watch v7]] — جولة v7.1→v7.3 (مصادقة PAT، إصلاح team-watcher، اختبار الفخ، الـeval الثاني).
- [[Home]]

%% ملاحظة للوكيل: أي محادثة جديدة عن مراقبة ginux تُربط هنا في project + تُحدَّث القرارات والمهام %%
