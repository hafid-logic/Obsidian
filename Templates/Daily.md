---
type: daily
date: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - daily
---

# <% tp.file.title %>

%% ملاحظة يومية بأسلوب kepano: لا تُكتب فيها مقالات — مجرد مهام وروابط إلى ما أُنجز اليوم %%

## المهام (Tasks)
- [ ] 

## محادثات اليوم (Today's Chats)
```dataview
TABLE project AS "Project", status
FROM "Chats"
WHERE chat_date = this.file.name
```

## روابط سريعة (Quick Links)
- [[Home]]
