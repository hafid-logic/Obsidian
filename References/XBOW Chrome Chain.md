---
type: reference
url:
author: XBOW Labs / تحليل هافيد
date: 2026-10-14
rating: 6
tags:
  - references
---

# XBOW Chrome Chain

## الملخص (Summary)
تحليل سلسلة XBOW الكاملة على Chrome/ويندوز (منشور XBOW Labs «Zero to Calc in Six Days» 2026-10-13): سلسلة استغلال كاملة بُنيت في 6 أيام (2–7 أغسطس 2026) بحوالي 40 ألف دولار حوسبة ونموذج gpt-5.6-sol ومكافأة 250 ألف دولار. ثلاث ثغرات: Maglev في V8 (HeapNumber قابل للتعديل عند deoptimization)، WebP متحرك في Blink (TOCTOU على ArrayBuffer منقول — الوحيدة التي اجتازت قفص V8)، وCrashpad (ERROR_PARTIAL_COPY عبر صندوق OS).
محادثتا التحليل: [[2026-10-14 XBOW Chrome Chain]] و[[2026-10-14 XBOW Security Dialogue]].

## أبرز النقاط (Highlights)
- جلسة التحقق صححت 3 أخطاء في المستند: Maglev لم تجتز قفص V8 (تحكم داخله فقط)، وWebP هي العابرة للقفص، وCrashpad اجتازت صندوق OS؛ و«الثوابت مكتوبة» صحيح في Maglev وحده.
- جدول نماذج أكتوبر 2026: GLM-5.3/Flash (MIT، الأعلى المفتوح في SWE-bench Verified)، Kimi K3 (Terminal-Bench 2.1)، DeepSeek V4.1 Flash (سياق مليون)، Qwen3-Coder-Next (46GB محلياً).
- اقتراح capture–recapture (N̂=n₁·n₂/m) كمُحكِّم جزئي للمدافع، مع تحذير انحيازه نحو طمأنة زائفة.
- قرارات منهجية: لا يُوسم ادعاء بـ«من المصدر» إلا بمحدِّد قابل للفحص خارجياً (رقم تعديل أو اقتباس حرفي)؛ فصل الصلاحيات بين الوكيل والتنفيذ والتحقق؛ تنويع النماذج والمزودين.

## التقييم (Rating — سلّم kepano من 7)
**6/7** — حالة دراسية مثالية لأتمتة الأمن مع دروس منهجية مباشرة قابلة للتطبيق في مساهمات [[Ginux]].

## المترابط (Related)
- [[Invariant Violations Paper]] — الثوابت الضمنية نفسها (TOCTOU/type confusion) بمعزل أكاديمي.
