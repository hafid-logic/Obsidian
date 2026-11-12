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
- ([[2026-11-12 HFT Design Responses]]): وصلت ردود وكيل Alexia الثلاثة على Brief v2.0 (= 4 مقترحات تصميم كاملة S0–S11) وأرشفت وتحللت مفصلاً: [[Alexia Design 1 Monolithic Python]] (جزءان، Python أحادية)، [[Alexia Design 2 Independent Local]] (محلياً أولاً + أصدق معاملة للحتمية)، [[Alexia Design 3 Hybrid Rust]] (هجين + 18 مصدراً متحققاً حياً). ==الإجماع شبه كامل== على النواة الدقيقة والاختلاف في 3 نقاط فقط (اللغة، السحابة، صرامة البوابات) — الموازنة الكاملة في [[HFT Designs Comparison]].

## المهام (Tasks)
- [x] لصق v2 لوكيل مشرف أو تنفيذ T0–T9 — منجز عبر وكيل Alexia: الردود الثلاثة مستلمة ومؤرشفة ([[2026-11-12 HFT Design Responses]]).
- [ ] الإجابة على أسئلة المالك الموحدة (البلد، البطاقة، رأس المال، Spot/Perps، إتقان Rust، التنبيهات، صلاحية Kill) — قائمة في [[HFT Designs Comparison]].
- [ ] الحسم في المكدس النهائي: مصدر البيانات + محرك backtesting + البوت — مبني على التركيبة الموصى بها في [[HFT Designs Comparison]].

## الملاحظات المترابطة (Related Notes)
- [[2026-11-12 HFT Design Responses]] — سجل استقبال الردود الثلاثة وأرشفتها.
- [[Alexia Design 1 Monolithic Python]] · [[Alexia Design 2 Independent Local]] · [[Alexia Design 3 Hybrid Rust]] — التحليل المفصل للتصاميم.
- [[HFT Designs Comparison]] — الموازنة الشاملة والإجماع والخلافات والتركيبة الموصى بها.
- [[hftbacktest]] · [[NautilusTrader]] · [[msgspec]] · [[Hyperliquid]] · [[Deflated Sharpe Ratio]] — المفاهيم المرجعية المشتركة.
- [[Haim Bodek]] — المرجعية الفكرية (كقائمة فحص لا أطروحة).
- [[Anti-HFT Decision]] — الوجه المكمّل: دعم قرار يدوي ضد HFT (بدون تنفيذ آلي) لنفس المجال.
- [[Kronos Eval]] — التقييم التجريبي لنموذج التنبؤ المرتبط.
- [[Home]]
