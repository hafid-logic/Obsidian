---
type: project
status: active
date: 2026-11-10
tags:
  - projects
aliases:
  - hft free stack
  - agent-brief-hft
---

# HFT Free Stack

> [!abstract] الهدف (Goal)
> منظومة تداول خوارزمي/عالي التردد **بميزانية صفرية** (أسواق أمريكية + كريبتو، L1/L2، ثلاث بيئات): وثيقة agent-brief تُسلَّم لوكيل مشرف يبنيها على أدوات جاهزة مفتوحة المصدر — بلا أي أدوات مؤسسية من Goldman Sachs.

## النطاق (Scope)
- يشمل: مصادر بيانات مجانية (yfinance/Binance WebSocket/Alpaca/Alpha Vantage)، محركات backtesting (backtrader/vectorbt/hftbacktest)، بوتات (freqtrade/hummingbot)، ومنهجية تقييم صارمة.
- لا يشمل: Marquee API المؤسسي (مقفل بمعرّف عميل)، ولا مال حقيقي قبل اجتياز FR-306.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- ([[2026-11-10 GS Quant HFT Brief]]): اعتماد وثيقة agent-brief-hft-free-stack.md (Markdown شامل 6+ صفحات بأسلوب SRS بعد إعادة اختيار مرتين) — 10 أقسام، FR-101→FR-703، مهام T1–T6 ومخرجات D1–D6 بمعايير قبول؛ إدراج اطروحات Haim Bodek (Trading Machines LLC، شكواه للـSEC وغرامة BATS ~14M$) كمرجعية فكرية.
- ([[2026-11-10 HFT Brief v2]]): إصدار v2 من الوثيقة بتدرج v2.0→v2.7 — 12 قراراً إلزامياً (Python مع hybrid، bus، الترميز، التخزين، محركات المحاكاة، ML، الأمان)، 9 مهام T0–T9، **v2.4: افتراض «اعتماد جاهز ما لم يثبت العكس» بدل البناء من الصفر**، و**v2.5: لا مال حقيقي قبل اجتياز FR-306** (منع lookahead، walk-forward، Deflated Sharpe)، وv2.2 مراجعة تقنية مفتوحة.

## المهام (Tasks)
- [ ] لصق v2 لوكيل مشرف أو تنفيذ T0–T9 داخل z.ai.
- [ ] الحسم في المكدس النهائي: مصدر البيانات + محرك backtesting + البوت.

## الملاحظات المترابطة (Related Notes)
- [[Anti-HFT Decision]] — الوجه المكمّل: دعم قرار يدوي ضد HFT (بدون تنفيذ آلي) لنفس المجال.
- [[Kronos Eval]] — التقييم التجريبي لنموذج التنبؤ المرتبط.
- [[Home]]
