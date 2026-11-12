---
type: reference
date: 2026-11-12
rating: 6
tags:
  - references
  - tooling
aliases:
  - "أوبن راوتر"
---

# OpenRouter

> [!abstract] ما هو؟
> موزّع API موحد لنماذج LLM المتعددة (مدفوعة + ==نماذج مجانية==)؛ العمود الفقري لبيئة الوكلاء المجانية التي بنى hafid في محادثة Gemini بتاريخ 2026-11-12 داخل Antigravity workspace.

## الدور المسجل في المحادثة
- **إعداد البيئة**: `OPENROUTER_API_KEY` في `.bashrc`/`.zshrc` (التوكن تسرّب نصاً في الصفحة المشتركة وحُجب في الأرشيف — انظر [!danger] في [[2026-11-12 Drift Hack and Myrmico Outreach]])؛ متوافق كذلك مع بديلَي التوافق: `HF_TOKEN` و`ANTHROPIC_AUTH_TOKEN`.
- **النماذج المجانية المستكشفة**: Tencent Hy3 preview (free — يزول مايو 2026)، ==Qwen3 Coder 480B A35B (free)== (الأكثر نفعاً للكوداج)، DeepSeek عبر HF (تحذير: ==V3 وليس V4== — V4 لم يصدر مستقراً ويرد `400` من Novita)، وخطأ `deepseek-ai/DeepSeek-V4-Pro:novita is not a valid model id`.
- **التكامل**: عبر OpenCode وContinue في VS Code، وأوامر `/model`، مع جدول تسعير أسبوعي (Weekly Tokens / $/M in/out / Context) لمقارنة النماذج.

## الخلاصة العملية
> [!callout] القرار المعتمد
> النماذج المجانية عبر OpenRouter تكفي مرحلة تطوير ميرميكو — لا اشتراكات مدفوعة؛ مع ==تنويع المزود== (Groq للسرعة، HF للحوسبة، Gemini للموسوعية، Opus للتفكير المجرد) والوكيل المحلي للتنفيذ.

## الارتباطات
- [[2026-11-12 Drift Hack and Myrmico Outreach]] · [[Paperclip]] · [[MYRMICO Network]]
