---
type: chat
url: https://claude.ai/share/67c1be5c-010d-40b4-8a12-6dbad7ef4114
chat_date: 2026-04-05
chat_date_estimated: true
project:
  - "[[Agent Sandbox]]"
status: processed
tags:
  - chats
---

# 2026-04-05 Agent Sandbox MCP

> [!info] المصدر (Source)
> [الرابط الأصلي للمحادثة](https://claude.ai/share/67c1be5c-010d-40b4-8a12-6dbad7ef4114) — محادثة مشتركة من claude.ai (لقطات المشاركة تخفي الملفات المرفقة وقد تطوي رسائل أقدم).

> [!warning] التاريخ تقديري
> محسوب من طوابع «Apr 4-5» الظاهرة في المحادثة (السنة استُنتجت 2026) — اضبطه إن عرفت التاريخ الفعلي.

## الملخص (Summary)
- محاكاة config.json وأوامر إقلاع لوكيل TypeScript يفقد الاتصال بـ daemon محلي — إعادة إطلاقه كعملية مستقلة مع تحويل Stdout/Stdin (6 ملفات: sandbox-config.json، sandbox-agent.ts، standalone-worker.ts، startup.sh، QUICKSTART.md، توثيق RTL).
- دمج «Core Logic Engine» (ملف TypeScript ضخم) في standalone-worker.ts كصندوق أسود مع تبادل بيانات عبر Shared Memory: ==خفض زمن الاستجابة من 50-200ms إلى 5-20ms== وإنتاجية مستهدفة 800-1200 عملية/ثانية بذاكرة 80-150MB.
- تكامل MCP (Model Context Protocol) بمنقولَي Stdio/SSE لمنح وكيل مهندس برمجيات AI صلاحيات نظام: mcp-client-base.ts (ContextWindowManager، ResourceManager، ToolRegistry) وmcp-transport-layer.ts وsoftware-engineer-agent.ts.
- إصلاح TypeError لـ OpenTelemetry في بيئة معزولة عبر polyfills للدوال المفقودة مثل `createContextKey`.
- هندسة عكسية لحزمة claude-code-cli قديمة: تنفيذ NativeBridge يدعم `dynamic_tool_discovery` بتوافق مع `@ant/sdk`؛ ورفض Claude تسليم تفاصيل handshakes والتوثيق الخاصة بالـSDK لأسباب أمنية (تصعيد صلاحيات/اختطاف جلسات) مقدّماً أفضل الممارسات بدلاً منها.

## القرارات المستخلصة (Key Decisions)
- تبادل البيانات عبر Shared Memory بدل استدعاءات الشبكة بين المحرك والعامل المستقل.
- MCP Stdio للعمليات المحلية وSSE للبعيدة — طبقة نقل واحدة لكلتا الحالتين.
- عدم تفكيك بروتوكولات التوثيق المغلقة — الالتزام بالـSDK الرسمي.

## المخرجات (Artifacts)
- 15 ملفاً عبر ثلاث مراحل (6 + 5 + 4): وثائق، إعدادات، وكلاء، طبقات نقل، وخطة تكامل — كلها داخل المحادثة.

## المتابعات (Follow-ups)
- [ ] إحياء الملفات الخمسة عشر من المحادثة إلى مستودع [[Agent Sandbox]] الفعلي.
- [ ] قياس زمن الاستجابة فعلياً بعد دمج Shared Memory للتحقق من نطاق 5-20ms.

%% مرتبط: [[Agent Sandbox]] · [[Kronos Eval]] %%
