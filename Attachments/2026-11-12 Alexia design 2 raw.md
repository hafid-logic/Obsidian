---
type: clipping
url: ""
date: 2026-11-12
source_title: INDEPENDENT DESIGN REVIEW — رد مستقل على Brief v2.0 (محلياً أولاً)
original_file: "التصميم_المستقل_رد_على_Brief_v2.docx"
tags:
  - clippings
---

# النص الحرفي: INDEPENDENT DESIGN REVIEW — رد مستقل على Brief v2.0 (محلياً أولاً)

> [!info] التقاط حرفي بتاريخ 2026-11-12
> النص الكامل للوثيقة المرفوعة من hafid (ملف `التصميم_المستقل_رد_على_Brief_v2.docx`، من وكيل Alexia — أكتوبر 2026).
> وسوم `[UNVERIFIED]` و`[قرار]` و`[غير مشغّل]` و`[افتراض]` و`[task]` مأخوذة حرفياً من الوثيقة الأصلية.
> التحليل المفصل: [[Alexia Design 2 Independent Local]] — المقارنة الشاملة: [[HFT Designs Comparison]] — المشروع: [[HFT Free Stack]].

+---------------------------------------------------------------------------------------------------+
| > INDEPENDENT DESIGN REVIEW --- LOW-LATENCY ALGORITHMIC TRADING                                   |
| >                                                                                                 |
| > **التصميم المستقل ---**                                                            |
| >                                                                                                 |
| > **منصة تداول خوارزمي**                                                             |
| >                                                                                                 |
| > **منخفض الكمون**                                                                   |
| >                                                                                                 |
| > منصة مجانية دائمة --- رد فني شامل على Brief v2.0                                   |
| >                                                                                                 |
| > نطاق الوثيقة: الأقسام S0--S11 --- من الملخص التنفيذي إلى المصادر المفتوحة          |
| >                                                                                                 |
| > [منهجية التحقق: بحث ويب (أكتوبر 2026) مع وسوم [قرار] و[UNVERIFIED] و[افتراض]  |
| >                                                                                                 |
| > الخلاصة الجوهرية: التشغيل محلياً أولاً --- السحابة المجانية الدائمة تتطلب بطاقة تحقق |
| >                                                                                                 |
| > Alexia Agent --- Response to Brief v2.0 أكتوبر 2026                                |
+---------------------------------------------------------------------------------------------------+

**المحتويات**

S0 --- ملخص تنفيذي 1

S1 --- الافتراضات وحدود البحث 1

S2 --- T0: تدقيق الحقائق 1

S3 --- T1: تحليل الفجوات 2

S4 --- T2: مراجعة الحد الأعلى للتقنية 3

S5 --- T3: البنية ومسارات الفشل 4

S6 --- T4: خريطة الطريق 5

S7 --- T5: عقود المستوى A 6

S8 --- T6 وT8: مصفوفة الصدق والجدوى 13

S9 --- T7: Red Team 15

S10 --- T9: أسئلة المالك وسجل ADR 15

S11 --- المصادر المفتوحة فعلاً (مقتطفات بحث، أكتوبر 2026) 16

*ملاحظة: هذا الجدول مُنشأ عبر الحقول التلقائية؛ لضمان دقة أرقام الصفحات بعد أي تعديل، انقر بزر الفأرة الأيمن على الجدول واختر «تحديث الحقل».*

# **S0 --- ملخص تنفيذي**

**الحكم العام:** يمكن بناء منصة تداول في نطاق L1 (قرار من ثوانٍ إلى دقائق، وإرسال الأمر في 50--500ms) بأدوات مجانية بالكامل، بشرط أن يكون التشغيل **محلياً أولاً**. التشغيل السحابي المجاني الدائم يحتاج بطاقة تحقق في كل خيار تحققتُ منه. التسمية "HFT" مضللة، والوصف الصحيح للمشروع هو **"تداول خوارزمي منخفض الكمون يعمل بالأحداث"** **[قرار]**.

**أهم 5 قرارات:**

**1.** [نواة Python 3.12 أحادية العملية تسير عليها حلقة الأحداث كلها بتسلسل واحد حتمي. Rust مؤجل إلى أن يثبت القياس أنه ضروري (ADR-1) **[قرار]**].

**1.** [الأسعار والكميات أعداد صحيحة int64 بوحدات tick/lot. لا نستخدم Decimal ولا float إلا عند الحدود (ADR-2) **[قرار]**].

**1.** [لا Redis ولا وسيط رسائل خارجي. نستخدم مُسلسِلاً (Sequencer) داخل العملية، وسجل أحداث ثنائي للبيانات، وSQLite WAL لأحداث التحكم والأوامر (ADR-3/4) **[قرار]**].

**1.** [نواة خاصة رفيعة تُبنى على عقود المستوى A. hftbacktest مرجع لمعايرة نموذج الطابور، ويُعاد تقييم NautilusTrader عند صدور 2.0 النهائي (ADR-5) **[قرار]**].

**1.** [المرحلة 1 لا تحتاج حساباً في أي بورصة. تستخدم بيانات عامة مع منفّذ محاكاة، فلا يوقفها القيد الجغرافي ولا KYC (ADR-6) **[قرار]**].

**أكبر 3 مخاطر:**

**1.** غياب الميزة الربحية: صناعة السوق بحساب فردي سلبية الهامش على الأزواج الرئيسية بعد الرسوم (T8).

**1.** Overfitting في البحث، ويعالجه FR-306 كبوابة إلزامية.

**1.** خطر المنصة والجغرافيا: حظر، أو إغلاق مثل BitMEX في 2026، أو تغيّر شروط الاستخدام.

# **S1 --- الافتراضات وحدود البحث**

**•** بحث ويب محدود بـ 8 استعلامات، تعطّل منها 3. قرأتُ مقتطفات الصفحات فقط ولم أفتحها كاملة.

**•** لم أتحقق من: Binance (القيود الجغرافية)، gs-quant، vectorbt وPRO، backtrader، pandas-ta، GCP e2-micro، رسوم أي بورصة، Alpaca/IEX، msgspec وأداؤه، وحدود الـ API لأي منصة. كل هذه موسومة **[UNVERIFIED]**.

**•** [**[افتراض]** المطوّر شخص واحد يتقن Python، ورأس المال الأولي صغير.]

**•** [**[افتراض]** المالك خارج الولايات المتحدة، والدولة غير معروفة (انظر T9).]

**•** [كل الكود في S7 **[غير مشغّل]**].

# **S2 --- T0: تدقيق الحقائق**

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **#**   **الادعاء في الوثيقة**                                    **الحكم**                        **المصدر / الملاحظة**
  -------- ---------------------------------------------------------------------- --------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------
  1        Oracle Always Free بلا بطاقة                              خاطئ                             docs.oracle.com FreeTier: البطاقة مطلوبة لمعظم المستخدمين ولا تُخصم

  2        Oracle تسترد الموارد الخاملة                              متحقق                            docs.oracle.com resourceref: عتبات 20% على 7 أيام. حساب PAYG معفى حسب مصادر ثانوية

  3        Oracle A1 = 4 OCPU / 24GB                                              متعارض                           الوثائق تقول 4/24، ومصدران ثانويان (2026) يقولان 2/12. يُتحقق منه من لوحة التحكم

  4        الجهاز المصغّر = "1 vCPU/1GB"                            خاطئ جزئياً                       E2.1.Micro = ثُمن OCPU مع إمكانية الاندفاع، و1GB

  5        Fly.io مجاني                                              خاطئ للحسابات الجديدة            مصادر ثانوية متعددة (2026). الصفحة الرسمية لم تُفتح

  6        Alpha Vantage ≈ 25 طلباً/يوم                               متحقق (ثانوي متسق)               + 5 طلبات/دقيقة

  7        hftbacktest يدعم الطابور والكمون                          متحقق                            وثائق nkaz001/hftbacktest: L2/L3، موقع الطابور، الكمون، Rust + نشر حي

  8        NautilusTrader نواة Rust وتكافؤ backtest/live             متحقق                            nautilustrader.io + releases. 2.0.0rc6 في 4/10/2026، وrc7 إصدار تجريبي

  9        gs-quant: 13.2k نجمة، إصدار 2.2.1، .claude/skills         غير قابل للتحقق الآن             **[UNVERIFIED]** ولا يؤثر على التصميم

  10       Binance محجوب في الولايات المتحدة                         غير قابل للتحقق الآن             **[UNVERIFIED]**

  11       vectorbt مفتوح / PRO مدفوع، صيانة backtrader وpandas-ta   غير قابل للتحقق الآن             **[UNVERIFIED]** ولا أعتمد على أيّ منها

  12       غرامة BATS بـ 14 مليون دولار عام 2015                     غير قابل للتحقق الآن             من الذاكرة: التسوية كانت مع بورصتي EDGA/EDGX (Direct Edge، المملوكة آنذاك لـ BATS). **[UNVERIFIED]**

  13       GCP e2-micro مجاني دائماً                                  غير قابل للتحقق الآن             **[UNVERIFIED]**

  14       ملاحظة إضافية: BitMEX أُغلقت في 23/9/2026                  متحقق (ملاحظات إصدار Nautilus)   دليل على خطر المنصة
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **S3 --- T1: تحليل الفجوات**

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **#**   **FR**    **الفجوة**                                                           **الخطورة**          **البديل / المعالجة**
  -------- --------- --------------------------------------------------------------------------------- --------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------
  G1       101       yfinance غير رسمي وAV مقيد بـ 25/يوم                                 متوسطة               yfinance للتطوير فقط مع تخزين مؤقت Parquet، وAlpaca للبيانات اليومية إن كان الحساب متاحاً **[UNVERIFIED]**

  G2       102/107   لا ضمان لسلامة الدفتر المحلي بلا إجراء snapshot+diff                 عالية                آلة حالات للدفتر (S7-#1 وS5)، والدفتر غير المتحقق منه يحجب التداول

  G3       103       backfill الصفقات ممكن، أما backfill دفتر L2 تاريخياً فغير ممكن عادةً   عالية                الفجوة تبطل الدفتر: إعادة snapshot، ووسم الفترة gap في المسجّل

  G4       104       المخطط الأصلي بلا تسلسل ولا أوقات متعددة                             عالية                S7-#1

  G5       108       لا قياس لانجراف الساعة                                               متوسطة               chrony + DriftMonitor (S7-#3)

  G6       203       رقم 10ms غير مبرر                                                    منخفضة               ميزانية داخلية t1→t5 تُقاس في المرحلة 1

  G7       303       محاكاة الطابور غائبة                                                 عالية لصناعة السوق   واجهة FillModel (S7-#10) ومعايرة ضد hftbacktest

  G8       306       لا ضوابط overfitting                                                 حرجة                 سجل التجارب + walk-forward + DSR كبوابة

  G9       307       لا حتمية                                                             عالية                Sequencer + SimClock + hash للإعدادات

  G10      401/402   ccxt لا يكفي OMS                                                     عالية                OMS داخلي + capability flags

  G11      404/406   خطر الأمر المزدوج عند إعادة الاتصال                                  حرجة                 clientorderid حتمي + reconcile قبل التفعيل

  G12      501/502   لا price collar ولا فشل مغلق                                         حرجة                 دالة نقية fail-closed

  G13      602       Grafana لا تتسع في 1GB                                               متوسطة               ملفا Minimal/Full

  G14      703       لا نموذج تهديد لوكيل AI                                              عالية                واجهة نوايا مقيدة، ولا تعديل للحدود (S9)

  G15      4.4       السحابة المجانية = بطاقة + استرداد عند الخمول                        عالية                محلي أولاً، والسحابة قرار للمالك (T9)
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **S4 --- T2: مراجعة الحد الأعلى للتقنية**

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Q**                                **المرشحون (≥3) والمفاضلة**                                                                                                                                                                                                                                                                 **الحكم**                                                                                                                 **ما الذي يغيّر الحكم**
  ------------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------
  Q1 لغة الحلقة الساخنة   [Python (سرعة تطوير، المنظومة، المسار الحرج بالـ ms مقبول)؛ Rust (أداء وسلامة ذاكرة، وتكلفة تطوير ×2--3 **[افتراض]**)؛ C++/Java-Disruptor/Go (أداء، لكن بلا تكافؤ مع أدوات البحث)]                                                                                                          [Python 3.12 + asyncio (uvloop اختياري) **[قرار]**]                                                                       p99 داخلي t1→t5 > 20ms بعد التحسين، أو استراتيجية عبر عشرات الرموز

  Q2 أحادية أم hybrid     أحادية Python؛ Python+Rust (PyO3)؛ Rust كاملة                                                                                                                                                                                                                                               أحادية الآن + حدود FFI معرّفة مسبقاً (S7-#12)                                                                               نفس معيار Q1

  Q3 Event bus                         داخل العملية (ترتيب كلي، صفر شبكة)؛ Redis Streams (حوالي 50--100MB RAM **[UNVERIFIED]**، قفزة شبكة)؛ NATS/ZeroMQ (مفيدة لعدة عمليات)؛ Aeron/Kafka (مبالغة)                                                                                                      [داخل العملية **[قرار]**]                                                                                                 الحاجة لفصل recorder في عملية أخرى، وحينها ZeroMQ PUB

  Q4 الترميز              msgspec (Structs مكتوبة الأنواع + msgpack، سريع **[UNVERIFIED]**)؛ orjson (JSON فقط)؛ Protobuf/FlatBuffers/SBE (تعدد لغات، تكلفة أدوات)                                                                                                                         [msgspec داخلياً، ويُفك JSON البورصة بـ msgspec مباشرة **[قرار]**]                                                          تبنّي Rust، وحينها FlatBuffers أو Arrow IPC

  Q5 التخزين              Parquet+zstd + DuckDB للتحليل؛ SQLite WAL للسجل؛ QuestDB/ClickHouse/Timescale (خوادم دائمة تستهلك RAM)                                                                                                                                                                                      [Parquet/DuckDB + SQLite + ملف ثنائي إلحاقي للبيانات **[قرار]**]                                                          حجم استعلام يومي يتجاوز RAM على DuckDB

  Q6 محرك الاختبار        محرك خاص يشارك الكود الحي (تكافؤ بالبنية)؛ hftbacktest (طابور وكمون L2/L3، متحقق)؛ NautilusTrader (متكامل، 2.0 RC بتغييرات كاسرة، متحقق)؛ vectorbt/backtrader (متجهي أو قديم، **[UNVERIFIED]**)                                                                              [خاص + hftbacktest للمعايرة **[قرار]**]                                                                                   صدور Nautilus 2.0 مستقراً + اختبار نقل استراتيجية خلال يومين ⇒ إعادة تقييم

  Q7 مصدر الكريبتو        CEX: OKX/Bybit/Kraken/Coinbase (وصول جغرافي، KYC، L2 عبر WS، testnet، كله **[UNVERIFIED]**)؛ DEX بدفتر أوامر: Hyperliquid/dYdX (بلا KYC غالباً، لكن مطابقة على كتل ومخاطر تنظيمية وتقنية **[UNVERIFIED]**)؛ ccxt كطبقة REST مساعدة   [المرحلة 1: بيانات عامة من منصة يصل إليها المالك. التنفيذ الحي يُحدَّد بعد T9 **[سؤال مفتوح]**]                              بلد المالك

  Q8 التحليلات            numpy/numba ذاتي للمؤشرات الست (شفاف ومتطابق في backtest وlive)؛ pandas-ta (صيانة **[UNVERIFIED]**)؛ TA-Lib (تبعية C)؛ Polars للبحث                                                                                                                             [تنفيذ ذاتي تدريجي للحلقة الحية، وPolars/pandas للبحث **[قرار]**]                                                         ---

  Q9 ML                                GBM baseline؛ DeepLOB وما بعده؛ RL                                                                                                                                                                                                                                                          مؤجل خلف بوابة FR-306. لم أتحقق من دليل منشور على ربح خارج العينة بعد الرسوم لحساب فردي **[UNVERIFIED]**   نتيجة DSR إيجابية لـ baseline بسيط أولاً

  Q10 المراقبة            Prometheus+Grafana (RAM)؛ VictoriaMetrics single-node (أخف **[UNVERIFIED]**)؛ سجلات JSON + أوامر DuckDB                                                                                                                                                         Minimal: سجلات JSON + endpoint /metrics. Full: VictoriaMetrics + Grafana **[قرار]**                        ---

  Q11 النشر               Docker Compose؛ systemd؛ Nix                                                                                                                                                                                                                                                                [Compose (NFR-204) + chrony على المضيف **[قرار]**]                                                                        ---

  Q12 الأمان              ملف .env بصلاحيات 600؛ SOPS/age؛ مدير أسرار سحابي                                                                                                                                                                                                                              [age/SOPS للملفات المشفرة، ومفاتيح تداول فقط، وIP whitelist **[قرار]**]                                                   ---
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**الـ Stack النهائي:**

  -------------------------------------------------------------------------------------------------------
  **الطبقة**   **الأساسي**                            **البديل**
  ------------------------- --------------------------------------------------- -------------------------
  Runtime                   Python 3.12 + asyncio                               Rust/PyO3 (P6)

  الأحداث      msgspec                                             orjson

  Bus                       Sequencer داخلي                        ZeroMQ

  السجل        SQLite WAL + ملف msgpack/zstd          ---

  التحليل      DuckDB + Polars + Parquet                           pandas

  المحاكاة     محرك خاص + hftbacktest للمعايرة        NautilusTrader

  الأسهم       yfinance للتطوير + Alpaca paper        Alpha Vantage

  التنبيهات    Telegram Bot API                                    Discord webhook

  المراقبة     سجلات JSON / VictoriaMetrics+Grafana   Prometheus
  -------------------------------------------------------------------------------------------------------

# **S5 --- T3: البنية ومسارات الفشل**

flowchart LR
subgraph Sources
WS[Venue WS: trades + L2] -->|recv_ts| NB[Normalizer → canonical]
RP[ReplaySource: recorded file] --> NB2[same canonical]
TM[Timers / Commands]
end
NB --> SEQ[Sequencer: dedupe + seq_local + journal]
NB2 --> SEQ
TM --> SEQ
EX[Execution reports] --> SEQ
SEQ --> BK[BookStore + integrity FSM]
BK --> RS[RiskState]
RS --> OMS[OMS state machine]
OMS --> ST[StrategyHost → OrderIntent]
ST --> RG{Risk gate: pure, fail-closed}
RG -- reject --> LOG[Decision trace]
RG -- ok --> OMS2[OMS: cid + journal BEFORE send]
OMS2 --> EXE{Executor}
EXE -- backtest/paper --> SIM[SimExecutor + FillModel] --> EX
EXE -- live --> BA[BrokerAdapter] --> EX

**المشترك بين الأوضاع الثلاثة:** كل ما بين SEQ وOMS2. **المختلف:** مصدر الأحداث، والمنفّذ، والساعة فقط.

**مسارات الفشل** (السلوك الافتراضي: إيقاف الأوامر الجديدة، والسماح بالإلغاء وتقليص المراكز):

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **الحدث**              **الكشف**                       **الاستجابة**
  ----------------------------------- -------------------------------------------- -------------------------------------------------------------------------------------------------
  انقطاع WS              heartbeat/timeout                            الدفتر يصبح STALE، والمخاطر ترفض. إعادة اتصال تراجعية + snapshot جديد

  فجوة في update id      prevlastupdate_id ≠ last                     INVALID، إعادة مزامنة، وحدث GapMarker في المسجّل

  رسالة مكررة            (venue, kind, seq_venue)                     تُسقَط في Sequencer

  تأخر شديد              recv − exchange > عتبة         stale_data في بوابة المخاطر

  فيضان الطابور          Queue full                                   Overflow ⇒ إبطال الدفتر وإيقاف مؤقت. تقارير التنفيذ لا تُسقَط أبداً

  انقطاع أثناء الإرسال   أمر بحالة PENDING_NEW بلا ack   استعلام بالـ cid، ثم إعادة إرسال بنفس الـ cid أو وسمه "مفقوداً"

  تعطل العملية           ---                                          recovery من السجل ← reconcile ← التفعيل فقط إذا تطابقت الحالة

  عدم تطابق الأرصدة      reconcile                                    kill + تنبيه بشري
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **S6 --- T4: خريطة الطريق**

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **المرحلة**       **الهدف**           **التسليمات**                                                                                                                                              **DoD قابل للفحص**                                                                                                                                                                                                                    **يعتمد على**
  ------------------------------ -------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------
  P1 (5 أيام عمل)   حلقة paper عاملة    عقود المستوى A، موصل WS لمنصة واحدة (trades+L2+integrity)، Sequencer، سجل، استراتيجية z-score، بوابة مخاطر، OMS، SimExecutor متشائم، سجلات JSON، Compose   \(1\) git clone && make up && make paper تعمل محلياً. (2) 24 ساعة بلا تعطل. (3) قطع الشبكة يدوياً ⇒ رفض أوامر ثم تعافٍ تلقائي. (4) replay لساعة مسجلة يعطي نفس hash الأوامر مرتين. (5) اختبارات وحدة للمخاطر والـ FSM ≥ 90% تغطية فروع   ---

  P2                             backtest موثوق      ReplaySource، الرسوم والانزلاق، تقارير FR-304/305، سجل التجارب، walk-forward، DSR                                                                          backtest على تسجيل P1 = قرارات paper نفسها حرفياً (نفس نموذج التعبئة). التقرير يرفض النشر إذا كان N \< الحد الأدنى                                                                                                                     P1

  P3                             تنفيذ حي آمن        BrokerAdapter حقيقي (testnet إن وُجد **[UNVERIFIED]**)، reconciler، تفعيل حي بخطوتين، kill switch، Telegram                     مجموعة chaos: قطع أثناء submit/cancel × 50 تكراراً ⇒ صفر أوامر مكررة. اختبار kill في أقل من ثانية                                                                                                                                      P1 وT9

  P4                             تشغيل 24/7          ملفا Minimal/Full، chrony، تنبيهات، runbooks، نسخ احتياطي للسجل خارج الخادم                                                                                14 يوم paper بتوفر ≥ 99% وصفر فروق reconcile                                                                                                                                                                                          P3

  P5                             بحث الاستراتيجيات   معايرة FillModel ضد hftbacktest، صناعة سوق مبسطة، Alpaca paper للأسهم اليومية                                                                              تقرير جدوى لكل استراتيجية وفق T8                                                                                                                                                                                                      P2

  P6 (اختياري)      الأداء والـ ML      Rust للدفتر وFillModel إن لزم، وGBM baseline                                                                                                               تحقق معيار Q1 / بوابة FR-306                                                                                                                                                                                                          P5
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[**بوابات Go/No-Go قبل المال الحقيقي** (كلها إلزامية) **[قرار]**]:

**1.** ≥ 30 يوماً متصلة على paper للاستراتيجية نفسها وبالإعدادات نفسها (config hash).

**1.** احتمال DSR ≥ 0.95 على بيانات خارج العينة، مع إعلان عدد التجارب المجرّبة.

**1.** انحراف أداء paper عن backtest على نفس الفترة ضمن نطاق مُعلن مسبقاً.

**1.** صفر فروق reconcile لمدة 7 أيام.

**1.** تمرين kill switch ناجح يدوياً وآلياً.

**1.** [رأس مال أولي يقبل المالك خسارته كاملاً، وحد خسارة يومي ≤ 1% منه **[افتراض]**].

# **S7 --- T5: عقود المستوى A**

[اللغة Python 3.12. كل المقتطفات **[غير مشغّل]**. التنفيذ الكامل والاختبارات مؤجلة إلى P1.]

**#1 الأحداث القياسية.** الغرض: مخطط موحد بزمن ns وتسلسلين. الافتراض: منصة تنشر update ids. المؤجل: حقول خاصة بكل منصة.

events.py
from enum import IntEnum
import msgspec
class Side(IntEnum):
BUY = 1
SELL = -1
class Header(msgspec.Struct, frozen=True, kw_only=True):
venue: str # "okx" | "kraken" | "sim" \...
symbol: str # canonical "BTC-USDT"
tsexchangens: int # t0 (0 = unknown)
tsrecvns: int # t1 from Clock
seq_venue: int # venue trade/update id, -1 if none
seq_local: int = 0 # total order, set ONLY by Sequencer
class Trade(Header, frozen=True, kw_only=True, tag="trade"):
px: int; qty: int; aggressor: Side; trade_id: str
class BookDelta(Header, frozen=True, kw_only=True, tag="book"):
is_snapshot: bool
firstupdateid: int
lastupdateid: int
prevupdateid: int # -1 if venue lacks chaining
bids: list[tuple[int, int]] # (pxticks, qtylots); qty 0 = delete
asks: list[tuple[int, int]]
class Bar(Header, frozen=True, kw_only=True, tag="bar"):
tsopenns: int; interval_ns: int
o: int; h: int; l: int; c: int; v: int
class Timer(Header, frozen=True, kw_only=True, tag="timer"):
name: str
class GapMarker(Header, frozen=True, kw_only=True, tag="gap"):
reason: str # "seq_gap" | "reconnect" | "overflow"
ExecReport/Intent in #6; Event = Trade | BookDelta | Bar | Timer | GapMarker | ExecReport

**#2 تمثيل الأسعار.** القرار: int64 بوحدات tick/lot. السبب: مساواة دقيقة، وحتمية بالبت، وسرعة، ومنع الأسعار الخارجة عن tick. نستخدم float للمؤشرات فقط، وDecimal عند حدود API فقط.

instrument.py
from dataclasses import dataclass
from decimal import Decimal, ROUNDFLOOR, ROUNDCEILING
\@dataclass(frozen=True, slots=True)
class Instrument:
venue: str; symbol: str
tick: Decimal # e.g. Decimal("0.1")
lot: Decimal # e.g. Decimal("0.00001")
min_notional: Decimal
def px_in(self, s: str) -> int: # venue string → ticks (exact or error)
q = Decimal(s) / self.tick
if q != q.tointegralvalue():
raise ValueError(f"off-tick price {s}")
return int(q)
def qty_in(self, s: str) -> int:
q = Decimal(s) / self.lot
if q != q.tointegralvalue():
raise ValueError(f"off-lot qty {s}")
return int(q)
def px_out(self, ticks: int) -> str: return str(ticks * self.tick)
def qty_out(self, lots: int) -> str: return str(lots * self.lot)
def pxfromfloat(self, x: float, side: int) -> int: # strategy float → passive tick
mode = ROUNDFLOOR if side > 0 else ROUNDCEILING
return int((Decimal(repr(x)) / self.tick).tointegralvalue(mode))
def notional_quote(self, ticks: int, lots: int) -> Decimal:
return Decimal(ticks lots) self.tick * self.lot

**#3 الساعة وقياس الانجراف.** مبدأ أساسي: في backtest تُضبط الساعة على tsrecvns وليس على tsexchangens، لأن هذا يمنع lookahead.

clock.py
import time
from collections import deque
from typing import Protocol
class Clock(Protocol):
def now_ns(self) -> int: \...
def mono_ns(self) -> int: \...
class LiveClock:
def nowns(self) -> int: return time.timens()
def monons(self) -> int: return time.monotonicns()
class SimClock:
def init(self) -> None: self._t = 0
def nowns(self) -> int: return self.t
def monons(self) -> int: return self.t
def advance_to(self, t: int) -> None:
if t \< self._t:
raise ValueError("SimClock cannot go backwards")
self._t = t
class DriftMonitor:
"""one-way latency >= 0, so min(recv - exch) \< 0 PROVES local clock is behind venue."""
def init(self, window: int = 4096) -> None:
self._s: deque[int] = deque(maxlen=window)
def update(self, tsexchangens: int, tsrecvns: int) -> None:
if tsexchangens > 0:
self.s.append(tsrecvns - tsexchange_ns)
def lowerboundns(self) -> int | None: # ≈ drift + min latency
return min(self.s) if self.s else None
def breached(self, maxabsns: int) -> bool:
lb = self.lowerboundns()
return lb is not None and (lb \< -maxabsns or lb > maxabsns)

**#4 عقد الـ Bus.** الخصائص: ترتيب كلي، و"تسليم فعلي مرة واحدة" إلى السجل (at-least-once من المصدر + إزالة التكرار)، وضغط عكسي يقطع البيانات ولا يقطع التحكم أبداً.

sequencer.py
import asyncio, msgspec
class Sequencer:
def init(self, mdjournal, ctljournal, handlers, mdcapacity=50000):
self.mdq: asyncio.Queue = asyncio.Queue(mdcapacity) # market data: bounded
self.ctl_q: asyncio.Queue = asyncio.Queue() # exec/commands/timers: never dropped
self.seq = max(mdjournal.lastseq(), ctljournal.lastseq())
self.handlers = handlers # FIXED order: Book → RiskState → OMS → StrategyHost
self.mdj, self.ctlj = mdjournal, ctljournal
self.seen: dict[tuple, None] = {} # bounded LRU in impl
def publish_md(self, ev) -> None:
try:
self.mdq.putnowait(ev)
except asyncio.QueueFull:
self.ctlq.putnowait(("overflow", ev.venue, ev.symbol)) # → book INVALID, risk halts
def publish_ctl(self, ev) -> None:
self.ctlq.putnowait(ev)
async def _next(self):
if not self.ctl_q.empty(): # control has strict priority
return self.ctlq.getnowait(), True
if not self.md_q.empty():
return self.mdq.getnowait(), False
done, _ = await asyncio.wait(
{asyncio.ensurefuture(self.ctlq.get()), asyncio.ensurefuture(self.mdq.get())},
returnwhen=asyncio.FIRSTCOMPLETED) # impl: cancel/requeue the loser
t = done.pop(); return t.result(), False
async def run(self) -> None:
while True:
ev, isctl = await self.next()
key = (getattr(ev, "venue", ""), type(ev).name, getattr(ev, "seq_venue", -1))
if key[2] >= 0:
if key in self.seen: continue
self.seen[key] = None
self.seq += 1
if isinstance(ev, msgspec.Struct):
ev = msgspec.structs.replace(ev, seq_local=self.seq)
(self.ctlj if isctl else self.md_j).append(self.seq, ev) # journal BEFORE dispatch
for h in self.handlers:
h(ev) # synchronous ⇒ deterministic

المؤجل: LRU محدود، ومعالجة المهمة الخاسرة في asyncio.wait، وتجميع الكتابات (batching) لسجل البيانات.

**#5 StrategyPlugin والـ Context.**

strategy_api.py
from typing import Protocol, Literal
import msgspec
from events import Side
class OrderIntent(msgspec.Struct, frozen=True, kw_only=True):
symbol: str; side: Side; qty: int
px: int | None = None # None = market
kind: Literal["limit", "market", "stop"] = "limit"
postonly: bool = False; reduceonly: bool = False
tif: Literal["GTC", "IOC", "FOK"] = "GTC"
tag: str = "" # explainability label
class CancelIntent(msgspec.Struct, frozen=True):
client_id: str
class Context(Protocol):
def now_ns(self) -> int: \...
def bestbidask(self, symbol: str) -> tuple[int, int] | None: \... # None if book invalid
def position(self, symbol: str) -> int: \...
def open_orders(self, symbol: str) -> list[str]: \...
def submit(self, i: OrderIntent) -> str | None: \... # returns client_id or None if risk-rejected
def cancel(self, c: CancelIntent) -> None: \...
def rng(self): \... # seeded from config hash
def note(self, **fields) -> None: \... # decision trace (NFR-208)
class StrategyPlugin(Protocol):
name: str; version: str
def on_start(self, ctx: Context, params: dict) -> None: \...
def on_event(self, ctx: Context, ev) -> None: \...
def on_stop(self, ctx: Context) -> None: \...
RULES: no I/O, no time.time(), no global random, no broker import --- enforced by import-linter in CI.

**#6 آلة حالات الأمر وقاعدة** client_order_id**.**

oms_fsm.py
import hashlib
from enum import Enum
class OS(Enum):
PENDINGNEW = "pendingnew"; ACCEPTED = "accepted"; PARTIAL = "partially_filled"
FILLED = "filled"; PENDINGCANCEL = "pendingcancel"; CANCELLED = "cancelled"
REJECTED = "rejected"; EXPIRED = "expired"; LOST = "lost" # never acked, not at venue
TERMINAL = {OS.FILLED, OS.CANCELLED, OS.REJECTED, OS.EXPIRED, OS.LOST}
ALLOWED = {
OS.PENDINGNEW: {OS.ACCEPTED, OS.PARTIAL, OS.FILLED, OS.REJECTED, OS.PENDINGCANCEL,
OS.CANCELLED, OS.EXPIRED, OS.LOST},
OS.ACCEPTED: {OS.PARTIAL, OS.FILLED, OS.PENDING_CANCEL, OS.CANCELLED, OS.EXPIRED},
OS.PARTIAL: {OS.PARTIAL, OS.FILLED, OS.PENDING_CANCEL, OS.CANCELLED, OS.EXPIRED},
OS.PENDING_CANCEL: {OS.CANCELLED, OS.PARTIAL, OS.FILLED, OS.ACCEPTED, OS.EXPIRED}, # ACCEPTED = cancel-reject
}
class IllegalTransition(Exception): \...
def apply(order, new: OS, cum_filled: int) -> bool:
"""Returns False for late/duplicate reports on terminal orders (logged, ignored)."""
if order.state in TERMINAL:
return False
if new not in ALLOWED[order.state]:
raise IllegalTransition(f"{order.state}->{new}") # → kill switch, human review
if cumfilled \< order.filled or cumfilled > order.qty:
raise IllegalTransition("non-monotonic or over-fill")
if order.state is OS.PENDING_CANCEL and new is OS.ACCEPTED and order.filled > 0:
new = OS.PARTIAL # restore correct pre-cancel state
order.state, order.filled = new, cum_filled
return True
def clientorderid(strategyid: str, epoch: int, intentseq: int, max_len: int = 32) -> str:
"""Deterministic: same journaled intent ⇒ same id on retry, restart and replay.
epoch is persisted in the journal (not wall-clock), intentseq = Sequencer seqlocal."""
h = hashlib.blake2b(f"{strategyid}|{epoch}|{intentseq}".encode(), digest_size=12).hexdigest()
return ("a" + h)[:max_len] # alnum only; per-venue charset/len from Caps

**قاعدة idempotency:** يُسجَّل الأمر (intent + cid) في السجل قبل الإرسال. عند الشك يُستعلم بالـ cid أولاً، وإعادة الإرسال تكون بنفس الـ cid **حصراً**. لا يُولَّد cid جديد لنيّة قديمة أبداً.

**#7 BrokerAdapter.**

broker.py
from typing import Protocol
import msgspec
class Caps(msgspec.Struct, frozen=True):
postonly: bool; reduceonly: bool; stop: bool; iceberg: bool; amend: bool
querybyclientid: bool; cancelall: bool
clientidmaxlen: int; clientid_charset: str # e.g. "a-zA-Z0-9"
dedupesclientid: bool # venue rejects duplicate cid? [UNVERIFIED per venue]
class Unsupported(Exception): \...
class BrokerAdapter(Protocol):
venue: str
caps: Caps
async def connect(self) -> None: \...
async def submit(self, req) -> None: \... # ack/fills arrive as ExecReport via Sequencer
async def cancel(self, client_id: str) -> None: \...
async def queryorder(self, clientid: str): \... # ExecReport | None
async def open_orders(self) -> list: \...
async def balances(self) -> dict[str, str]: \... # Decimal strings at boundary
def check_caps(req, caps: Caps) -> None:
for flag in ("postonly", "reduceonly"):
if getattr(req, flag) and not getattr(caps, flag):
raise Unsupported(flag) # explicit reject, never emulate silently
if req.kind == "stop" and not caps.stop:
raise Unsupported("stop")
if len(req.clientid) > caps.clientidmaxlen:
raise Unsupported("clientidlen")

**#8 بوابة المخاطر.** دالة نقية، وفشلها مغلق. الحدود تُحمَّل من ملف للقراءة فقط، **ولا يوجد API لتعديلها وقت التشغيل**.

risk.py
from dataclasses import dataclass
\@dataclass(frozen=True, slots=True)
class Decision:
ok: bool; reason: str
\@dataclass(frozen=True, slots=True)
class Limits:
maxpos: dict; maxorderqty: dict; maxordernotionalq: int; maxgrossq: int
maxdailylossq: int; maxorderspermin: int; collar_bps: int
maxmdagens: int; maxdrift_ns: int
def check(req, s, L: Limits, now_ns: int) -> Decision:
try:
if s.killed: return Decision(False, "kill_switch")
if not s.valid: return Decision(False, "riskstateinvalid")
if not s.bookvalid[req.symbol]: return Decision(False, "bookinvalid")
if nowns - s.lastmdns[req.symbol] > L.maxmdagens: return Decision(False, "stale_data")
if abs(s.driftns) > L.maxdriftns: return Decision(False, "clockdrift")
if s.orderslastmin >= L.maxordersper_min: return Decision(False, "rate")
if not 0 \< req.qty \<= L.maxorderqty[req.symbol]: return Decision(False, "qty")
mid = s.mid[req.symbol] # KeyError ⇒ reject
px = req.px if req.px is not None else mid
if abs(px - mid) 10_000 > L.collar_bps mid: return Decision(False, "price_collar")
notional = s.notional_q(req.symbol, px, req.qty)
if notional > L.maxordernotional_q: return Decision(False, "notional")
pos = s.position[req.symbol]
worst = pos + int(req.side) * (req.qty + s.opensameside_qty(req.symbol, req.side))
reduces = abs(pos + int(req.side) * req.qty) \< abs(pos)
if req.reduceonly and not reduces: return Decision(False, "notreducing")
if not reduces:
if abs(worst) > L.max_pos[req.symbol]: return Decision(False, "position")
if s.grossq + notional > L.maxgross_q: return Decision(False, "gross")
if s.pnldayq \<= -L.maxdailylossq: return Decision(False, "dailyloss")
return Decision(True, "ok")
except Exception as e: # fail-closed
return Decision(False, f"riskerror:{type(e).name_}")

ما لا يمكن تجاوزه بأي طريق: kill، والحدود، وcollar، وstale. وحده الإنسان يعيد التفعيل بعد kill، عبر أمر محلي وليس عبر واجهة FR-703.

**#9 آلية التكافؤ backtest/paper/live.**

wiring.py
def build(mode: str, cfg):
strat = load_plugin(cfg.strategy) # identical in all modes
oms = OMS(cidrule=clientorder_id) # identical
limits = loadlimitsreadonly(cfg.risk_file) # identical
fm = makefillmodel(cfg.fill_model)
if mode == "backtest":
clock = SimClock()
src = ReplaySource(cfg.recording, clock) # advances clock to tsrecvns
exe = SimExecutor(fm, clock, cfg.simlatencyns, cfg.fees)
elif mode == "paper":
clock = LiveClock()
src = VenueWsSource(cfg.venue, clock)
exe = SimExecutor(fm, clock, cfg.simlatencyns, cfg.fees)
elif mode == "live":
requirelivearming(cfg) # env LIVE=1 AND one-time token typed at console
clock = LiveClock()
src = VenueWsSource(cfg.venue, clock)
exe = BrokerExecutor(make_adapter(cfg.venue), clock)
else:
raise ValueError(mode)
return Engine(clock, src, exe, oms, strat, limits, confighash=hashcfg(cfg))

اختبار التكافؤ (NFR-206): نسجّل جلسة paper، ثم نشغّل backtest على التسجيل بنفس config_hash ونفس FillModel، ونطالب بأن يكون sha256(سلسلة الأوامر) متطابقاً.

**#10 واجهة نموذج التعبئة/الطابور.**

fill_model.py
from typing import Protocol
class FillModel(Protocol):
def on_new(self, o, book) -> None: \...
def on_book(self, d, book) -> None: \...
def ontrade(self, t) -> list: \... # [(clientid, qty, px, is_maker)]
def oncancel(self, clientid: str) -> None: \...
class ConservativeQueue:
"""queue_ahead = visible qty at our price when placed; decreases by trades at our price;
clipped to current visible level qty. A trade THROUGH our price fills us fully."""
def init(self): self.ahead: dict[str, int] = {}; self.o: dict = {}
def on_new(self, o, book):
self.o[o.cid] = o; self.ahead[o.cid] = book.qty_at(o.side, o.px)
def on_book(self, d, book):
for cid, o in self.o.items():
self.ahead[cid] = min(self.ahead[cid], book.qty_at(o.side, o.px))
def on_cancel(self, cid): self.o.pop(cid, None); self.ahead.pop(cid, None)
def on_trade(self, t):
out = []
for cid, o in list(self.o.items()):
through = (o.side > 0 and t.px \< o.px) or (o.side \< 0 and t.px > o.px)
at_px = t.px == o.px and int(t.aggressor) == -int(o.side)
if through:
out.append((cid, o.remaining, o.px, True))
elif at_px:
left = t.qty - self.ahead[cid]
self.ahead[cid] = max(0, self.ahead[cid] - t.qty)
if left > 0:
out.append((cid, min(left, o.remaining), o.px, True))
return out # SimExecutor updates remaining & removes filled orders

المؤجل إلى P5: نماذج احتمالية لتوزيع الإلغاءات، ومعايرتها ضد نماذج hftbacktest.

**#11 الاستمرارية والـ recovery.**

recovery.py
async def recoverandarm(engine, ctl_journal, adapter, cfg) -> bool:
snap = ctljournal.latestsnapshot() # every N events: OMS+positions+epoch
engine.load(snap)
for ev in ctl_journal.read(after=snap.seq): # intents, exec reports, commands
engine.apply(ev, side_effects=False) # rebuild state, NO sends
engine.armed = False
venueopen = {r.clientid: r for r in await adapter.open_orders()}
for cid, o in engine.oms.non_terminal().items():
r = venueopen.pop(cid, None) or await adapter.queryorder(cid)
if r is not None:
engine.sequencer.publish_ctl(r)
elif engine.clock.nowns() - o.createdns \< cfg.resendttlns and o.state.value == "pending_new":
await adapter.submit(o.request) # SAME client_id
else:
engine.sequencer.publishctl(engine.oms.marklost(cid))
for cid in venue_open: # unknown to us ⇒ orphan
await adapter.cancel(cid)
if not engine.portfolio.matches(await adapter.balances(), tol=cfg.recon_tol):
engine.kill("reconcile_mismatch") # human review required
return False
engine.armed = True
return True

**•** التخزين: ctl في SQLite WAL بجدول events(seq PK, ts, kind, payload BLOB) مع synchronous=FULL لأحداث التحكم.

**•** بيانات السوق: ملف msgpack إلحاقي مسبوق بالطول، يُدوَّر يومياً ويُضغط zstd، ثم يتحول إلى Parquet ليلاً.

**#12 حدود اللغات.** القرار: لا FFI في v1. إن احتجنا إليه لاحقاً فالعقد كالتالي: دوال نقية، أعداد صحيحة ومصفوفات numpy فقط، بلا I/O ولا ساعة ولا حالة عامة. التكافؤ يُثبَت باختبار replay-hash نفسه.

hotpath_api.py --- contract any Rust/PyO3 module must satisfy
from typing import Protocol
import numpy as np
class BookKernel(Protocol):
def apply(self, side: int, px: np.ndarray, qty: np.ndarray) -> None: \... # int64 arrays
def best(self) -> tuple[int, int, int, int]: \... # bidpx, bidq, askpx, askq
def qty_at(self, side: int, px: int) -> int: \...
def checksum(self) -> int: \... # must equal pure-Python reference on golden files

**المستوى B (توقيعات فقط):**

**•** class VenueWsSource: async def run(self, publishmd, publishctl) -> None

**•** def rsi(close: np.ndarray, n: int) -> np.ndarray (وبالمثل bollinger/zscore/rv/atr/vwap)

**•** def walkforward(trials: TrialRegistry, folds: int, embargons: int) -> Report

**•** def deflatedsharpe(sr: float, ntrials: int, skew: float, kurt: float, T: int) -> float

**•** def report(fills, equity, benchmark) -> pl.DataFrame

**•** class Alerter: async def send(self, level: str, text: str) -> None

**•** class ControlAPI: submit_intent / pause / status (انظر S9: لا حدود، ولا سحب، ولا تفعيل حي)

# **S8 --- T6 وT8: مصفوفة الصدق والجدوى**

**T6 --- ما لا يمكن مجاناً:**

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **#**   **البند**                          **السبب**                                                                                    **البديل**
  -------- ----------------------------------------------- --------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------
  1        كمون بالميكروثانية                 Python + إنترنت عام. الـ RTT يهيمن (عشرات إلى مئات الـ ms **[UNVERIFIED]**)   آفاق ثوانٍ إلى ساعات

  2        Colocation وfeeds مباشرة           مدفوعة ومؤسسية                                                                               لا بديل، ونعلن ذلك

  3        L2 حي للأسهم الأمريكية             غير مجاني **[UNVERIFIED]**                                                    الأسهم يومية فقط

  4        سحابة مجانية دائمة بلا بطاقة       Oracle تطلب البطاقة (متحقق)، وFly لا طبقة مجانية (متحقق ثانوياً)                              التشغيل محلياً، أو بطاقة تحقق بقرار المالك

  5        ضمان عدم استرداد Oracle للخادم     عتبات خمول 20% (متحقق) والبوت خفيف الحمل                                                     التحويل إلى PAYG (بطاقة، بلا خصم ضمن الحدود حسب مصادر ثانوية) أو نسخ احتياطي خارجي. ممنوع "الحمل الوهمي" لأنه التفاف على الشروط

  6        سعة ARM مضمونة                     الأرقام متعارضة (4/24 أو 2/12) والسعة غير مضمونة                                             الملف Minimal يجب أن يعمل على 1GB

  7        الوصول لكل البورصات                قيود جغرافية وKYC **[UNVERIFIED]**                                            المرحلة 1 مستقلة عن البورصة

  8        دفتر L2 تاريخي مجاني بعمق كامل     الأرشيفات العامة صفقات وklines غالباً **[UNVERIFIED]**                         مسجّل خاص من اليوم الأول (FR-106)

  9        Rebates مثل صنّاع السوق المحترفين   مستويات VIP بأحجام كبيرة **[UNVERIFIED]**                                     لا يُبنى عليها أي شيء

  10       استمرارية المنصة                   BitMEX أُغلقت في 2026 (متحقق)                                                                 BrokerAdapter + منصتان على الأقل في P5
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**نقد مرجعية Bodek (ما ينتقل وما لا ينتقل):**

**•** ينتقل:

**•** (أ) الرسوم ومستوياتها جزء من الاستراتيجية.

**•** (ب) أولوية الطابور price-time، وهي معلنة غالباً في الكريبتو، فقيمتها قابلة للنمذجة.

**•** (ج) الاختيار السلبي، وهو الأقوى انتقالاً.

**•** لا ينتقل: جوهر أطروحته، أي أنواع أوامر غير موثقة تمنح أولوية خفية في بورصات الأسهم الأمريكية 2008--2012.

**•** ما يشبهه في الكريبتو ويستحق الفحص **[UNVERIFIED]**: أوضاع منع التداول الذاتي، وأوامر "تحسين سعر التجزئة"، ومستويات API لكبار العملاء، ومحركات التصفية. وفي Hyperliquid/DEX تتم المطابقة على مستوى الكتلة، وهذه بنية مجهرية مختلفة كلياً.

**•** الخلاصة: نستعمل Bodek كقائمة فحص للمطابقة والرسوم، لا كأطروحة.

**T8 --- أحكام الجدوى** (حساب بالرموز، والأرقام الفعلية **[UNVERIFIED]**):

ليكن fm رسم maker وft رسم taker بنقاط الأساس، وs الفارق، وA تكلفة الاختيار السلبي لكل تعبئة.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **الاستراتيجية**                  **الشرط اللازم للربح**                                                                                                                                                                                        **الحكم**
  ---------------------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------
  صناعة سوق post-only على BTC/ETH   s/2 − fm − A > 0 لكل جانب. على الأزواج الرئيسية الفارق غالباً tick واحد، أي جزء صغير من نقطة أساس **[UNVERIFIED]**، بينما fm للحساب الفردي موجب **[UNVERIFIED]**   سلبي متوقع. ممكن نظرياً فقط على أزواج أقل سيولة، حيث A ومخاطر المخزون أعلى. قيمتها هنا اختبار البنية (الطابور، الإلغاء، الحالات)

  Mean-reversion z-score على 1m     متوسط الارتداد > 2·f_t + الانزلاق (عشرات نقاط الأساس ذهاباً وإياباً بالأسعار الفردية **[UNVERIFIED]**)                                                                                          غير مرجح. يتحسن بدخول maker وأفق أطول. يعامل كاختبار للبنية

  Momentum/trend (ساعات إلى أيام)   دوران منخفض، فالرسوم هامشية                                                                                                                                                                                   الأكثر معقولية، لكن الميزة إن وُجدت تأتي من علاوة الاتجاه/بيتا وليس من الكمون. تحتاج FR-306
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**ما تثبته المنصة فعلاً:** صحة البيانات، والحتمية، وأمان التنفيذ، والقدرة على اختبار الأفكار بصدق. **لا تثبت ربحية.** البنية التحتية السليمة ≠ ميزة ربحية.

# **S9 --- T7: Red Team**

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **#**                    **نمط الفشل**                 **الأثر**                **التخفيف**                                                                                                                                                                  **من يكتشفه**
  ------------------------- ------------------------------------------ ------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------
  1                         انقطاع البورصة أو WS          قرارات على بيانات ميتة   stale ⇒ رفض، وإلغاء الأوامر المعلقة عبر REST بعد مهلة                                                                                                                        heartbeat + بوابة المخاطر

  2                         انجراف الساعة                 lookahead أو رفض خاطئ    chrony + DriftMonitor + حد في البوابة                                                                                                                                        DriftMonitor

  3                         أمر مزدوج                     ضعف التعرض               cid حتمي، وسجل قبل الإرسال، واستعلام قبل إعادة الإرسال                                                                                                                       اختبار chaos + reconcile

  4                         دفتر تالف أو قديم             أسعار خاطئة              FSM للسلامة وchecksum عند توفره **[UNVERIFIED]**                                                                                                              BookStore

  5                         استراتيجية خارجة عن السيطرة   حلقة أوامر               حد الأوامر/دقيقة، والحد الاسمي، وkill آلي عند تجاوز معدل الرفض                                                                                                               المخاطر + التنبيه

  6                         تسرب مفتاح                    سرقة                     مفاتيح تداول بلا سحب، وIP whitelist، وSOPS، وفحص الأسرار في CI                                                                                                               gitleaks + البورصة

  7                         حقن تعليمات عبر وكيل AI       أوامر خبيثة              واجهة FR-703 تقبل نوايا فقط تمر بالبوابة نفسها. لا تعديل للحدود، ولا تفعيل حي، ولا سحب، ولا إلغاء kill. حد نوايا مستقل، وقائمة رموز مسموحة. أسوأ حالة = خسارة ضمن حد اليوم   سجل القرارات + تنبيه

  8                         Overfitting                                خسارة حية                سجل التجارب + DSR + walk-forward + بوابة 30 يوماً                                                                                                                             تقرير FR-306

  9                         تغيّر نظام السوق               انهيار الأداء            مراقبة انحراف الأداء عن نطاق backtest ⇒ إيقاف تلقائي                                                                                                                         مقاييس يومية

  10                        حظر جغرافي أو إغلاق منصة      توقف كامل                BrokerAdapter، ومنصة ثانية، ومراكز صغيرة، وعدم حفظ أموال على المنصة فوق الحاجة                                                                                               الإدارة البشرية

  11 (إضافي)   استرداد Oracle للخادم         توقف صامت                تنبيه "dead-man" خارجي: غياب نبضة لمدة 5 دقائق ⇒ Telegram                                                                                                                  مراقب خارجي
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **S10 --- T9: أسئلة المالك وسجل ADR**

**أسئلة المالك** (لكل منها افتراضي موصى به حتى لا يتوقف العمل):

**1.** ما بلد الإقامة والجنسية لأغراض KYC؟ --- الافتراضي: خارج الولايات المتحدة، والمرحلة 1 مستقلة عن البلد.

**1.** هل تقبل بطاقة تحقق بلا خصم (Oracle، وربما PAYG)؟ --- الافتراضي: لا، والتشغيل محلي حتى P4.

**1.** ما رأس المال الحي المتوقع؟ --- الافتراضي: مبلغ صغير تقبل خسارته كاملاً.

**1.** ما أفق التداول المفضل؟ --- الافتراضي: من دقائق إلى ساعات.

**1.** ما اللغات التي تتقنها؟ --- الافتراضي: Python فقط.

**1.** Spot فقط أم مشتقات أيضاً؟ --- الافتراضي: Spot فقط، فلا رافعة.

**1.** هل الحاسوب المحلي متاح 24/7؟ --- الافتراضي: لا، paper يعمل أثناء التطوير فقط.

**1.** هل الأسهم ضرورية الآن؟ --- الافتراضي: تؤجَّل إلى P5.

**1.** هل تقبل DEX (Hyperliquid) كمنفذ تنفيذ؟ --- الافتراضي: لا حتى تُراجَع قانونياً.

**1.** من يملك صلاحية kill وإعادة التفعيل؟ --- الافتراضي: المالك وحده، محلياً.

**سجل القرارات (ADR):**

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **ADR**   **السياق**                          **القرار**                         **البدائل المرفوضة**        **العواقب**
  --------- ------------------------------------------------ ----------------------------------------------- ---------------------------------------- ----------------------------------------------------------------------
  1         مطوّر واحد، ونطاق L1                 Python أحادية                      Rust/C++ كاملة              سرعة تطوير، وسقف أداء أدنى (P6)

  2         الحتمية والدقة                      ticks int64                                     float، Decimal في كل مكان   تحويل عند الحدود، وأخطاء tick تظهر مبكراً

  3         1GB RAM، والترتيب الكلي             Sequencer داخلي                    Redis، NATS                 لا توزيع أفقي، وهو غير مطلوب

  4         الاستمرارية                         SQLite WAL + سجل ثنائي             Postgres، QuestDB           خفيف، ونسخ احتياطي بنسخ ملف

  5         Nautilus 2.0 RC وتغييراته الكاسرة   نواة خاصة + hftbacktest للمعايرة   تبنّي Nautilus الآن          جهد أكبر، وفهم كامل للعقود. إعادة تقييم عند 2.0 النهائي

  6         الجغرافيا مجهولة                    P1 على بيانات عامة + محاكاة        البدء بحساب حي              لا توقف، والحي في P3

  7         السحابة = بطاقة                     محلي أولاً                          Oracle إلزامياً              قرار للمالك (س2)

  8         التسمية                             "منخفض الكمون" وليس HFT          HFT                                      توقعات صادقة
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# **S11 --- المصادر المفتوحة فعلاً (مقتطفات بحث، أكتوبر 2026)**

**1.** Oracle --- Oracle Cloud Infrastructure Free Tier، docs.oracle.com/iaas/Content/FreeTier/freetier.htm: البطاقة مطلوبة لمعظم المستخدمين وبلا خصم، وحد A1 4 OCPU/24GB.

**1.** Oracle --- Always Free Resources، docs.oracle.com/en-us/iaas/Content/FreeTier/resourceref.htm: عتبات الخمول 20% على 7 أيام، وE2.1.Micro = ⅛ OCPU و1GB.

**1.** Site2US --- Oracle Cloud Always Free (2026 Limits)، site2us.com (حوالي سبتمبر 2026، ثانوي): خفض إلى 2 OCPU/12GB، وPAYG معفى من الاسترداد.

**1.** temps.sh --- Temps vs Fly.io 2026 (ثانوي): انتهاء طبقة Fly المجانية في 7/10/2024.

**1.** saaspricepulse.com --- Fly.io Free Tier 2026 (ثانوي): تجربة قصيرة فقط للحسابات الجديدة.

**1.** apis.io --- Alpha Vantage Rate Limits (ثانوي): 25/يوم و5/دقيقة.

**1.** nkaz001/hftbacktest --- docs/index.rst (GitHub): الطابور والكمون وL2/L3 ونواة Rust وبوت حي.

**1.** nautechsystems/nautilus_trader --- Releases (GitHub): 2.0.0rc6 بتاريخ 4/10/2026، وحذف BitMEX بعد إغلاقها في 23/9/2026.

**1.** nautilustrader.io/open-source: نواة Rust، وتكافؤ backtest/live، وrc7 إصدار تجريبي.

**1.** lib.rs --- nautilus-trading: محرك Rust-native، حتمي، ويعمل بالأحداث.

**لم تُفتح** (فلا يُستشهد بها): أوراق Avellaneda--Stoikov، وCont وآخرون، وBailey--López de Prado، وDeepLOB، وأي عمل 2024--2026. هذه بذور للتحقق في P2/P5.