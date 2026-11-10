---
type: project
status: paused
date: 2026-10-23
tags:
  - projects
aliases:
  - kronos eval
  - open-terminal
---

# Kronos Eval

> [!abstract] الهدف (Goal)
> تقييم علمي صارم لنموذج [Kronos-small](https://huggingface.co/NeoQuasar/Kronos-small) (24,741,376 معامل) على BTCUSDT/ETHUSDT — باك تستان حتمي، مقارنة إحصائية مع rw_boot، ثم بروتوكول paper-trading مجمد بقرار مكتوب.

## النطاق (Scope)
- يشمل: خط التقييم T1–T8 (اكتمل)، خط open-terminal التنفيذي (verify.py، backtest 50×30، paper-trading)، أرشيف final-clean.
- لا يشمل: T9/T10 (قرار مشرف معلق)، ولا أي مال حقيقي.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- 2026-10-22 تقديري ([[2026-10-22 Open Terminal Build]]): مشروع open-terminal بـ8 مراحل (5 مكتملة) — verify.py نظام تحقق آلي ببوابة env إلزامية، وأرشيف نظيف 590KB.
- 2026-10-23 ([[2026-10-23 Open Terminal Freeze]]): باك تستان BTCUSDT 1h اكتمل (acc 0.40 مقابل قاعدة 0.56، استراتيجية −23.2% مقابل buy&hold +6.9%)؛ ETHUSDT 4h أُعيد مرة واحدة بعد حظر Binance 418 بموافقة مكتوبة (acc 0.54، +20.7%)؛ ثم **أمر تجميد كامل** — لا تشغيل ولا اتصال حتى قرار مكتوب، مع خط أساس هاشات (verify.py a01c27b1).
- 2026-10-26 ([[2026-10-26 Kronos T6-T8]]): اكتمال T5.2 رسمي 390/390؛ **الحكم الإحصائي: Kronos أسوأ من rw_boot على الأصلين** (BTC CRPS 5359.22 مقابل 3532.40، DM p=0.0047؛ ETH 349.65 مقابل 156.66، p=0.000049)؛ خطة تحليل مسبق مقفولة sha256 746abb28 قبل T6 — ممنوع تعديل العتبات بعد النتائج؛ تصحيح الوثيقة: 24.74M معامل لا 4.1M (DEV-001)؛ تقرير T8 عربي RTL بـ8 صفحات.

## المهام (Tasks)
- [ ] قرار المشرف المكتوب على الأرشيف النهائي وتفكيك التجميد.
- [ ] قرار T9/T10 (لم تُنفذا عمداً).
- [ ] تصحيح وثيقة المشروع upstream (4.1M → 24.74M).

## الملاحظات المترابطة (Related Notes)
- [[HFT Free Stack]] — الخط الأوسع لأدوات التداول المجانية.
- [[Home]]

%% درس المشروع: الحتمية (seeds + bit-exact) والبوابات المكتوبة قبل كل تشغيل — نمط متكرر في عمل hafid %%
