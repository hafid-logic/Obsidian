---
type: project
status: active
date: 2026-11-10
tags:
  - projects
aliases:
  - titan
  - لغة تيتان
---

# Titan Language

> [!abstract] الهدف (Goal)
> لغة برمجة نظام «أقوى من C» بمشروع طرحي: ملكية ذاكرة وسلامة مثل Rust مع بساطة C وتنفيذ وقت-ترجمة مثل Zig — تُبنى فوق LLVM خلال 3-6 أشهر MVP.

## النطاق (Scope)
- يشمل: تصميم اللغة (ownership، generics صفرية الكلفة، sum types، comptime، تزامن آمن، assembly مدمج)، MVP فوق LLVM (Lexer + Parser + backend)، وخطة 30 يوماً للنموذج الأولي.
- لا يشمل: نظام تشغيل كامل — نقاش بناء OS كان استكشافياً وقرر أن بناء اللغة أسرع طريقاً لنتيجة ملموسة.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- ([[2026-01-20 Titan Language and OS]]): اعتماد LLVM خلفية للمترجم — تختصر تطوير المترجمات من 5-10 سنوات إلى 6-12 شهراً وتمنح تحسينات عالمية المستوى.
- ([[2026-01-20 Titan Language and OS]]): جدول مرجعي C/Rust/Zig/Titan — Titan يجمع سلامة Rust + generics حقيقية + comptime؛ جدول الأداء 5/5 للجميع كهدف صريح.
- ([[2026-01-20 Titan Language and OS]]): تقسيم العمل: Lexer ‏90% بمساعدة AI، Parser ‏80%، AST ‏70%، المفسر الأساسي 60% — مع مراجعة بشرية إلزامية لكل سطر حرج.

## المهام (Tasks)
- [ ] MVP خلال 3-6 أشهر: Lexer + Parser + LLVM backend + إدارة ذاكرة أساسية.
- [ ] مرحلة الملكية والأنواع (6-12 شهراً) ثم async/comptime/metaprogramming (12-24 شهراً).

## الملاحظات المترابطة (Related Notes)
- [[LLVM]] — البنية التحتية المعتمدة للمترجم.
- [[Home]]
