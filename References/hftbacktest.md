---
type: reference
url: https://github.com/nkaz001/hftbacktest
author: "nkaz001 (مفتوح المصدر)"
rating: 7
date: 2026-11-12
project:
  - "[[HFT Free Stack]]"
tags:
  - references
---

# hftbacktest

## الملخص (Summary)
إطار محاكاة تداول عالي التردد مفتوح المصدر (نواة Rust + Python/Numba، Python 3.11+) مصمم خصيصاً لمحاكاة موقع أمر Limit في الطابور (queue position) وكمون التغذية/الأمر (feed/order latency) على بيانات دفتر الأوامر L2/L3 الخام، مع دعم النشر الحي. هو المحاكي المرجعي في كل تصاميم [[HFT Free Stack]] الثلاثة.

## أبرز النقاط (Highlights)
- محاكاة الطابور والكمون معاً — الفجوة الأكبر في المحركات التقليدية (Touch-is-Fill)
- تحقق حي من وثائق المستودع في تصميمي Alexia 2 و3 (أكتوبر 2026)
- الدور المعتمد: معايرة نموذج الطابور الداخلي (FillModel) لا استبدال المحرك الحتمي الخاص
- رخصة MIT مفتوحة بالكامل — تمر قيود الميزانية الصفرية

## التقييم (Rating)
★★★★★★★ (7/7) — الأداة المتخصصة الوحيدة المجانية التي تسد فجوة FR-303 (محاكاة الطابور) بإجماع التصاميم الثلاثة

## المترابط (Related)
- [[HFT Free Stack]] · [[Alexia Design 1 Monolithic Python]] · [[Alexia Design 2 Independent Local]] · [[Alexia Design 3 Hybrid Rust]] · [[HFT Designs Comparison]]
