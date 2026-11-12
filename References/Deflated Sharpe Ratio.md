---
type: reference
url: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2460551
author: "Bailey, D. H., & López de Prado, M. (2014)"
rating: 7
date: 2026-11-12
project:
  - "[[HFT Free Stack]]"
tags:
  - references
---

# Deflated Sharpe Ratio

## الملخص (Summary)
معيار إحصائي يصحح نسبة Sharpe المرصودة لتضليلها: انحياز الاختيار عبر تجريب استراتيجيات وتركيبات معلمات متعددة، عدم الاعتدالية (Skew والتفرطح Kurtosis)، وقصر العينة. يحول السؤال من كم الربح إلى ما احتمال أن يكون الأداء وليد الحظ والتجريب المتكرر — وفق الورقة المصدرية (Journal of Portfolio Management 40(5)).

## أبرز النقاط (Highlights)
- البوابة الإلزامية FR-306 في كل تصاميم [[HFT Free Stack]]: DSR > 0.95 (تصميمان) أو ≥ 0.90 (الهجين)
- شرطه المصاحب: تسجيل كل تجربة في trials_log لإعلان عدد المحاولات N الحقيقي
- يعمل ضمن خط أنابيب Walk-Forward + Purged Embargoed CV (منهجية López de Prado)
- الدلالة العملية: DSR ≥ 0.95 يعني احتمال الأداء بالصدفة < 5%
- تُدعم بحساب ذاتي (ResearchValidityEvaluator — المستوى B في عقود التصميم الأول)

## التقييم (Rating)
★★★★★★★ (7/7) — المعيار الإحصائي الوحيد الذي يمنع تسلل استراتيجيات Overfitting عبر بوابة المال الحقيقي

## المترابط (Related)
- [[HFT Free Stack]] · [[Alexia Design 1 Monolithic Python]] · [[Alexia Design 2 Independent Local]] · [[Alexia Design 3 Hybrid Rust]] · [[HFT Designs Comparison]] · [[Kronos Eval]]
