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

## المهام (Tasks)
- [ ] إتمام `gh auth` عبر device-flow (يحتاج تفاعل hafid).
- [ ] تأكيد أول تشغيل team-watcher بعد الدفع + رقم issue الاختبار التجريبي (v6.5b-3).
- [ ] إزالة مفتاح deploy القديم 20261106 من GitHub.
- [ ] قرار مصير ملف التوكن القديم في /tmp (مسار مبلَّغ فقط).

## الملاحظات المترابطة (Related Notes)
- [[Ginux]] — المستودع المرصود نفسه (مرجع).
- [[gmkurtzer]] — مالك upstream ومصدر دفعة الردود.
- [[HDAE Gates]] — ما يشغّل gmkurtzer حالياً (روابط غير محلولة مقصودة).
- [[overflow-checks]] — موضوع الخيوط الأصلية #222/#227.
- [[Home]]

%% ملاحظة للوكيل: أي محادثة جديدة عن مراقبة ginux تُربط هنا في project + تُحدَّث القرارات والمهام %%
