---
type: reference
url: https://script.google.com
author: Google
rating: 5
date: 2026-11-11
tags:
  - references
---

# Google Apps Script

## الملخص (Summary)
منصة سكربتات سحابية مجانية من Google تُستخدم في صفحة هبوط [[Deglet Nour Platform]] كقناة استقبال طلبات بلا خادم: نموذج الصفحة يرسل طلباً بـ`fetch` بوضع no-cors إلى Web App منشور، والسكربت يسجّل الطلبات تلقائياً في جدول Google Sheets.

## أبرز النقاط (Highlights)
- مجاني بالكامل ويتكامل أصلياً مع Google Sheets — أسرع طريق لتسجيل الطلبات بلا Backend.
- وضع no-cors يمنع قراءة الاستجابة فيخفي الأخطاء ولا يوفر أي حماية: ==رابط الـWeb App مكشوف في كود المصدر وأي أحد يستطيع غمره بطلبات وهمية==.
- التحصين المقترح في [[2026-11-11 Deglet Nour Landing Page]]: reCAPTCHA للتحقق من البشر، أو Token للطلبات، أو Backend خفيف وسيط.

## التقييم (Rating)
5/7 — أداة انطلاق ممتازة بصفر كلفة، لكنها للاستقبال المؤقت لا للإنتاج بلا طبقة حماية.

## المترابط (Related)
- [[2026-11-11 Deglet Nour Landing Page]]
- [[Deglet Nour Platform]]
