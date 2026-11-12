---
type: reference
url: https://github.com/jcrist/msgspec
author: "jcrist (مفتوح المصدر، BSD)"
rating: 6
date: 2026-11-12
project:
  - "[[HFT Free Stack]]"
tags:
  - references
---

# msgspec

## الملخص (Summary)
مكتبة تسلسل Python مكتوبة بلغة C: أسرع محلل JSON/MessagePack في المنظومة (10–20x أسرع من json القياسي، ~2x من orjson مع التحقق)، وفك ترميز مباشر إلى msgspec.Struct مقيدة الأنواع (frozen/array_like) بلا dict وسيط — أي صفر تخصيصات وسيطة في الحلقة الساخنة.

## أبرز النقاط (Highlights)
- تحقق مخطط مدمج (Zero-cost Type Validation) — أساس مخطط الأحداث الكانوني في التصاميم الثلاثة
- MessagePack مدمج للسجل الثنائي (WAL) وبديل msgpack/zstd للأرشيف
- Struct بـ array_like=True يقلص حجم الذاكرة للكائنات الساخنة
- البديل المعتمد عند الحاجة: orjson (بلا تحقق أنواع) — serde_json/simd-json داخل Rust

## التقييم (Rating)
★★★★★★☆ (6/7) — حجر التسلسل المعتمد إجماعاً في الحلقة الساخنة — أداء قرب اللغات المترجمة ببقاء Python

## المترابط (Related)
- [[HFT Free Stack]] · [[Alexia Design 1 Monolithic Python]] · [[Alexia Design 3 Hybrid Rust]] · [[HFT Designs Comparison]]
