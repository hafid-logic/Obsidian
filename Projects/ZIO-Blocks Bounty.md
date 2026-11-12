---
type: project
status: active
date: 2026-11-12
tags:
  - projects
aliases:
  - zio blocks bounty
  - checkblock
---

# ZIO-Blocks Bounty

> [!abstract] الهدف (Goal)
> اقتحام جوائز المصدر المفتوح في منظومة ZIO (John A. De Goes) — التكامل الفني (دمج CheckBlock في Parser الـ Markdown) بوصفه مدخل السمعة، مع فصل واضح بين ==ZIO-Blocks ($500-1,000)== و==ZIO-Schema Migration ($4,000)==.

## النطاق (Scope)
- يشمل: بيئة GitHub Codespaces + sbt 1.12.5 (تثبيت sdkman لكل جلسة)، ملفات Parser وHtmlRenderer وParserSpec (اختبارات GFM)، مستودع خاص hafid-logic/zio-blocks-private، وScala Steward المتعثر.
- لا يشمل: أي وعد بمبلغ $4,000 على ZIO-Blocks — ==تصحيح موثق: المبلغ $500-1,000==؛ الجائزة الكبرى في ZIO-Schema.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- ([[2026-11-12 ZIO-Blocks CheckBlock Integration]]): الاستمرار رغم تصحيح قيمة الجائزة — ==قيمة التعلّم والسمعة تفوق المبلغ==.
- ([[2026-11-12 ZIO-Blocks CheckBlock Integration]]): كل تعديل ملف بإعادة كتابة كاملة (لا ترقيعاً جزئياً) — يمنع بقايا الأقواس والقطع عند الانقطاع.
- ([[2026-11-12 Kimi A13969 and ZIO Bounty]]): فصل الجائزتين تماماً — ZIO-Schema (هجرة بيانات بفقدان صفر Data Loss = 0) مختلفة عن ZIO-Blocks (Parser/Docs).
- ([[2026-11-12 ZIO-Blocks CheckBlock Integration]]): الجسر الاستراتيجي نهاية الجلسة: عرض «الخوارزمية» للتدريب داخل أجهزة مؤسسات جزائرية موزعة — ==من جوائز المصدر المفتوح إلى رؤية [[MYRMICO Network]]==.

## المهام (Tasks)
- [ ] تطهير Block.scala (بقيت غير مطهرة نهاية جلسة 2026-11-12) وإكمال تكامل CheckBlock.
- [ ] devcontainer يثبت sbt تلقائياً (تفادي التثبيت اليدوي كل جلسة).
- [ ] فحص فشل Scala Steward في zio-blocks-private (كل المهام فشلت 1:17).
- [ ] فحص إيشو ZIO-Schema Migration قبل أي قرار على الجائزة الكبرى.

## الملاحظات المترابطة (Related Notes)
- [[ZIO-Blocks]] — المشروع الهدف.
- [[CrowdGen Artichoke]] — مسار الدخل الموازي.
- [[Home]]
