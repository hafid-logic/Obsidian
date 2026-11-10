---
type: reference
url: https://doc.rust-lang.org/cargo/reference/profiles.html#overflow-checks
author: The Rust Project & Cargo Documentation
rating: 6
date: 2026-11-07
tags:
  - references
---

# overflow-checks

## الملخص (Summary)
إعداد في ملفات [profile.release] الخاص بـ Cargo في Rust يتحكم في فحص فيض الأعداد الصحيحة (integer overflow) عند التشغيل: `true` يعني أن أي فيض يُرجع panic بدل التفاف صامت (wrapping)، و`false` — القيمة الافتراضية في release — يضحّي بالفحص مقابل سرعة أعلى. هذا بالضبط موضوع الخلاف في مستودع [[Ginux]]: الخيط [#222](https://github.com/gmkurtzer/ginux/issues/222) يسأل إن كان حذفه من `[profile.release]` مقصوداً، و[PR #227](https://github.com/gmkurtzer/ginux/issues/227) المفتوح يعيده إلى `true` — وكلاهما ما يزال بلا حسم من [[gmkurtzer]] حتى تاريخ 2026-11-07.

## أبرز النقاط (Highlights)
- الفرق بين release وdebug في Cargo يشمل عدة إعدادات؛ `overflow-checks` واحد منها ويُعطَّل افتراضياً في release لأداء أفضل.
- إعادة تفعيله تكلف زمن تشغيل لكنها تكشف أخطاء الفيض في الإنتاج بدل إخفائها — توازن أمان/أداء كلاسيكي.
- سجلات المراقبة في [[Ginux Watch]] تراقب مصير PR #227 (رأسه ثابت `9ac0f544`) — قرار [[gmkurtzer]] فيه سيحسم الموضوع.

## التقييم (Rating — سلّم kepano من 7)
**6/7** — توثيق رسمي مستقر ومفهوم مركزي لقرار تقني معلق في مشروع مرصود فعلياً.

## المترابط (Related)
- [[Ginux]] · [[gmkurtzer]] · [[2026-11-07 Ginux Watch v6.5]] · [[HDAE Gates]]
