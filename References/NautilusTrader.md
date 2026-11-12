---
type: reference
url: https://github.com/nautechsystems/nautilus_trader
author: "nautechsystems"
rating: 6
date: 2026-11-12
project:
  - "[[HFT Free Stack]]"
tags:
  - references
---

# NautilusTrader

## الملخص (Summary)
محرك تداول خوارزمي مفتوح المصدر بنواة Rust أصيلة وواجهة Python عبر PyO3، يوفر تكافؤاً كاملاً بين الاختبار الرجعي والتداول الحي بدقة قياسية 64-bit (9 خانات) وعالية 128-bit (16 خانة). في 2026-10-04 صدر 2.0.0rc6 مع rc7 تجريبي، وحُذف دعم BitMEX بعد إغلاقها في 23/9/2026 (توثيق حي لتغير المنصات).

## أبرز النقاط (Highlights)
- تكافؤ backtest/live بنواة Rust — أقرب إطار جاهز لعقود المستوى A
- إصدار 2.0 ما يزال RC بتغييرات كاسرة → قرار التصاميم: إعادة تقييم عند 2.0 النهائي
- عياره عند التبني: نقل استراتيجية خلال يومين (اختبار التصميم الثاني)
- يفرض هيكله الخاص (Actors/Adapters) — تكلفة تبنٍّ لا تكلفة أداء

## التقييم (Rating)
★★★★★★☆ (6/7) — إطار جاهز قوي لكنه مؤجل — بديل مرجعي لا أساس للنواة الخاصة وفق إجماع التصاميم

## المترابط (Related)
- [[HFT Free Stack]] · [[Alexia Design 2 Independent Local]] · [[Alexia Design 3 Hybrid Rust]] · [[HFT Designs Comparison]]
