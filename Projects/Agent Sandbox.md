---
type: project
status: active
date: 2026-11-10
tags:
  - projects
aliases:
  - agent sandbox
  - sandbox worker
---

# Agent Sandbox

> [!abstract] الهدف (Goal)
> صندوق رملي لوكيل AI مهندس برمجيات: عامل TypeScript مستقل يعيد الإقلاع بعد فقدان الـdaemon، محرك منطق مدموج عبر Shared Memory، وصلاحيات نظام عبر MCP (Stdio/SSE).

## النطاق (Scope)
- يشمل: إقلاع ذاتي للوكيل بعد انقطاع الاتصال (config.json + startup.sh)، دمج Core Logic Engine كصندوق أسود (زمن استجابة مستهدف 5-20ms بدل 50-200ms)، طبقة MCP كاملة (ContextWindowManager، ResourceManager، ToolRegistry)، وإصلاح polyfills لـ OpenTelemetry في البيئات المعزولة.
- لا يشمل: تفكيك بروتوكولات التوثيق المغلقة (رفض موثق) — الالتزام بالـSDK الرسمي.

## المحادثات المرتبطة (Linked Chats)
![[Project Chats.base]]

## القرارات (Decisions)
- ([[2026-04-05 Agent Sandbox MCP]]): تبادل البيانات بين المحرك والعامل المستقل عبر Shared Memory — خفض زمن الاستجابة من 50-200ms إلى 5-20ms وإنتاجية مستهدفة 800-1200 عملية/ثانية.
- ([[2026-04-05 Agent Sandbox MCP]]): منقولَا MCP: Stdio للعمليات المحلية وSSE للبعيدة — طبقة نقل واحدة لكلتا الحالتين.
- ([[2026-04-05 Agent Sandbox MCP]]): NativeBridge يدعم `dynamic_tool_discovery` متوافقاً مع `@ant/sdk` من هندسة عكسية لحزمة claude-code-cli قديمة — دون لمس تفاصيل التوثيق الأمنية.

## المهام (Tasks)
- [ ] إحياء ملفات المراحل الثلاث (15 ملفاً) من المحادثة إلى مستودع فعلي.
- [ ] قياس فعلي لزمن الاستجابة بعد دمج Shared Memory مقابل نطاق 5-20ms.

## الملاحظات المترابطة (Related Notes)
- [[Kronos Eval]] — الخط التنفيذي المجاور (مشروع open-terminal).
- [[Claude Code Leak]] — سياق أدوات Claude Code المُهندسة عكسياً.
- [[Home]]
