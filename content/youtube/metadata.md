# YouTube upload metadata

Copy-paste metadata per locale. Durations are the narration timeline measured from the
generated subtitles (`storyboard.md`); the rendered video adds a short tail, so round up by
about two seconds. Chapter timestamps are the English timeline (2:47); other locales shift by
a few seconds — the chapter *labels* stay valid, only the numbers need adjusting if you upload
a non-English cut as the primary video.

Full metadata (title + description + tags) is provided for the ten uploads with the widest
reach; the remaining 27 locales get a compact table with localized titles and durations.
Every locale's subtitles are in `subtitles/`, and every narrated locale's audio track is in
the master MKV (`build/video/master-multiaudio.mkv`).

## Thumbnail

Text overlay on a dark slide: **"Close the laptop. Keep the agent working."** — pair it with a
mock WhatsApp chat showing the 08:00 summary, or the report file path
(`/workspace/cross-border-ops/overnight-summary-2026-09-19.txt`).

***

## English (`en`) — 2:47

### Title

```text
Close your laptop. Keep the agent working: always-on cloud ops with WhatsApp
```

### Description

```text
An always-on agent pattern for cloud operations: an OpenClaw agent on a Lighthouse instance,
driven from a WhatsApp chat, watching prices and stock overnight while your laptop stays
closed. Based on Tencent Cloud's walkthrough, with the prompt clauses, guardrails, and the
morning verification loop spelled out.

This video ships with narration in 20 languages and subtitles in 37.

Code + prompt cookbook: https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

Chapters:
0:00 Close your laptop. Keep the agent working.
0:11 The half-open laptop problem
0:33 The overnight window is the point
0:44 Three planes, one instance
0:57 Where should the agent live?
1:11 Step one: deploy and connect
1:38 Step two: the prompt is the program
1:54 Monitor and recommend only
2:10 Step three: the morning report
2:25 The trade-offs, honestly
2:38 Steal the pattern

What the video covers:
- Why a closed lid, sleep, and a dropped network pause an agent mid-run
- The control plane (WhatsApp), compute plane (cloud instance), evidence plane (files)
- The 3-step setup: OpenClaw template (2 vCPU / 2 GB / 40 GB), region outside the
  mainland, model API key, WhatsApp QR link
- The overnight prompt: fixed scope, price drop or stock under 50, deduplicated alerts,
  08:00 UTC+8 zero-report, saved log path, degradation alarm
- Guardrails: monitor and recommend only; no price changes, no purchase orders, no
  customer contact; read-only credentials; a human on every decision
- The morning verification loop, and the trade-offs stated honestly

Stack: macOS say + ffmpeg + headless Chromium pipeline; 37 locale subtitle tracks; MIT
```

### Tags

```text
ai agent, always on, cloud ops, whatsapp bot, openclaw, lighthouse, tencent cloud,
monitoring, price tracking, inventory, prompt engineering, agent guardrails, devops,
automation, cloud server, llm agent, chatops
```

***

## Hindi (`hi`) — 3:18

### Title

```text
लैपटॉप बंद करें। एजेंट काम करता रहे: WhatsApp से चलने वाला ऑलवेज़-ऑन क्लाउड एजेंट
```

### Description

```text
WhatsApp से चलने वाला ऑलवेज़-ऑन क्लाउड एजेंट: OpenClaw को Lighthouse इंस्टेंस पर तैनात
करें, रात भर कीमत और स्टॉक पर नज़र रखें, और सुबह रिपोर्ट पढ़ें — लैपटॉप बंद रहने के
दौरान भी। प्रॉम्प्ट, गार्डरेल और सुबह की जाँच का पूरा तरीका शामिल है।

कोड और प्रॉम्प्ट कुकबुक: https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

अध्याय (अंग्रेज़ी टाइमलाइन):
0:00 लैपटॉप बंद करें। एजेंट काम करता रहे।
0:11 आधा खुला लैपटॉप, पूरी समस्या
0:33 असली मुद्दा रात का समय है
0:44 तीन परतें, एक इंस्टेंस
0:57 एजेंट कहाँ रहे?
1:11 पहला कदम: तैनात करें और जोड़ें
1:38 दूसरा कदम: प्रॉम्प्ट ही प्रोग्राम है
1:54 सिर्फ़ निगरानी और सलाह
2:10 तीसरा कदम: सुबह की रिपोर्ट
2:25 समझौते, ईमानदारी से
2:38 पैटर्न चुरा लें

स्टैक: macOS say + ffmpeg + headless Chromium पाइपलाइन; 37 भाषाओं में सबटाइटल; MIT
```

### Tags

```text
ai एजेंट, whatsapp बॉट, क्लाउड, ऑलवेज़ ऑन, निगरानी, प्रॉम्प्ट इंजीनियरिंग, ऑटोमेशन, devops, hindi
```

***

## Malayalam (`ml`) — 2:36 (silent video; subtitles only)

### Title

```text
ലാപ്‌ടോപ്പ് അടയ്ക്കൂ. ഏജന്റ് ജോലി തുടരട്ടെ: WhatsApp-ൽ നിന്ന് നിയന്ത്രിക്കുന്ന ക്ലൗഡ് ഏജന്റ്
```

### Description

```text
WhatsApp-ൽ നിന്ന് നിയന്ത്രിക്കുന്ന ഓൾവേയ്‌സ്-ഓൺ ക്ലൗഡ് ഏജന്റ്: OpenClaw ഒരു Lighthouse
ഇൻസ്റ്റൻസിൽ വിന്യസിച്ച് രാത്രി മുഴുവൻ വിലയും സ്റ്റോക്കും നിരീക്ഷിച്ച് രാവിലെ റിപ്പോർട്ട്
വായിക്കുക — ലാപ്‌ടോപ്പ് അടച്ചിട്ടും. പ്രോംപ്റ്റ്, ഗാർഡ്‌റെയിലുകൾ, രാവിലത്തെ പരിശോധന
എന്നിവയെല്ലാം ഉൾപ്പെടുന്നു.

കോഡും പ്രോംപ്റ്റ് കുക്ക്ബുക്കും: https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

ഈ വീഡിയോയിൽ ശബ്ദം ഇല്ല — മലയാളം വോയ്‌സ് റെക്കോർഡിംഗ് ഉടൻ ചേർക്കും.
സബ്‌ടൈറ്റിലുകൾ ലഭ്യമാണ്.

സ്റ്റാക്ക്: macOS say + ffmpeg + headless Chromium പൈപ്പ്‌ലൈൻ; 37 ഭാഷകളിൽ സബ്‌ടൈറ്റിലുകൾ; MIT
```

### Tags

```text
ai ഏജന്റ്, whatsapp ബോട്ട്, ക്ലൗഡ്, ഓൾവേയ്‌സ് ഓൺ, നിരീക്ഷണം, പ്രോംപ്റ്റ്, ഓട്ടോമേഷൻ, devops, malayalam
```

***

## Tamil (`ta`) — 3:33

### Title

```text
மடிக்கணினியை மூடுங்கள். முகவர் வேலை செய்யட்டும்: WhatsApp-இல் இயங்கும் கிளவுட் முகவர்
```

### Description

```text
WhatsApp-இல் இருந்து இயக்கப்படும் எப்போதும்-இயங்கும் கிளவுட் முகவர்: OpenClaw-ஐ ஒரு
Lighthouse இன்ஸ்டன்ஸில் நிறுவி, இரவு முழுவதும் விலையையும் ஸ்டாக்கையும் கண்காணித்து,
காலையில் அறிக்கையைப் படியுங்கள் — மடிக்கணினி மூடியிருந்தாலும். ப்ராம்ப்ட், கார்ட்ரெயில்கள்,
காலை சரிபார்ப்பு அனைத்தும் அடங்கும்.

குறியீடு மற்றும் ப்ராம்ப்ட் குக்க்புக்:
https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

அத்தியாயங்கள் (ஆங்கில நேரக்கோடு):
0:00 மடிக்கணினியை மூடுங்கள். முகவர் தொடர்ந்து வேலை செய்யட்டும்.
0:11 பாதி திறந்த மடிக்கணினியே பிரச்சினை
0:33 உண்மையான விஷயம் இரவு நேரம்
0:44 மூன்று அடுக்குகள், ஒரு இன்ஸ்டன்ஸ்
0:57 முகவர் எங்கு தங்க வேண்டும்?
1:11 முதல் படி: வரிசைப்படுத்தி இணைக்கவும்
1:38 இரண்டாம் படி: ப்ராம்ப்டே நிரல்
1:54 கண்காணிப்பும் ஆலோசனையும் மட்டும்
2:10 மூன்றாம் படி: காலை அறிக்கை
2:25 சமரசங்கள், நேர்மையாக
2:38 வடிவத்தை திருடுங்கள்

ஸ்டாக்: macOS say + ffmpeg + headless Chromium பைப்லைன்; 37 மொழிகளில் வசன வரிகள்; MIT
```

### Tags

```text
ai முகவர், whatsapp பாட், கிளவுட், எப்போதும் இயங்கும், கண்காணிப்பு, ப்ராம்ப்ட், ஆட்டோமேஷன், devops, tamil
```

***

## Kannada (`kn`) — 3:49

### Title

```text
ಲ್ಯಾಪ್‌ಟಾಪ್ ಮುಚ್ಚಿ. ಏಜೆಂಟ್ ಕೆಲಸ ಮಾಡುತ್ತಿರಲಿ: WhatsApp ನಿಂದ ನಿಯಂತ್ರಿತ ಕ್ಲೌಡ್ ಏಜೆಂಟ್
```

### Description

```text
WhatsApp ನಿಂದ ನಿಯಂತ್ರಿಸಲ್ಪಡುವ ಸದಾ-ಚಾಲು ಕ್ಲೌಡ್ ಏಜೆಂಟ್: OpenClaw ಅನ್ನು ಒಂದು Lighthouse
ಇನ್‌ಸ್ಟೆನ್ಸ್‌ನಲ್ಲಿ ನಿಯೋಜಿಸಿ, ರಾತ್ರಿಯಿಡೀ ಬೆಲೆ ಮತ್ತು ಸ್ಟಾಕ್ ಅನ್ನು ಗಮನಿಸಿ, ಬೆಳಿಗ್ಗೆ ವರದಿ
ಓದಿ — ಲ್ಯಾಪ್‌ಟಾಪ್ ಮುಚ್ಚಿದ್ದರೂ ಸಹ. ಪ್ರಾಂಪ್ಟ್, ಗಾರ್ಡ್‌ರೇಲ್‌ಗಳು, ಬೆಳಗಿನ ಪರಿಶೀಲನೆ ಎಲ್ಲವೂ ಸೇರಿವೆ.

ಕೋಡ್ ಮತ್ತು ಪ್ರಾಂಪ್ಟ್ ಕುಕ್ಬುಕ್:
https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

ಅಧ್ಯಾಯಗಳು (ಇಂಗ್ಲಿಷ್ ಟೈಮ್‌ಲೈನ್):
0:00 ಲ್ಯಾಪ್‌ಟಾಪ್ ಮುಚ್ಚಿ. ಏಜೆಂಟ್ ಕೆಲಸ ಮಾಡುತ್ತಿರಲಿ.
0:11 ಅರ್ಧ ತೆರೆದ ಲ್ಯಾಪ್‌ಟಾಪ್ ಸಮಸ್ಯೆ
0:33 ರಾತ್ರಿಯ ಸಮಯವೇ ನಿಜವಾದ ವಿಷಯ
0:44 ಮೂರು ಪದರಗಳು, ಒಂದು ಇನ್‌ಸ್ಟೆನ್ಸ್
0:57 ಏಜೆಂಟ್ ಎಲ್ಲಿ ಇರಬೇಕು?
1:11 ಮೊದಲ ಹೆಜ್ಜೆ: ನಿಯೋಜನೆ ಮತ್ತು ಸಂಪರ್ಕ
1:38 ಎರಡನೇ ಹೆಜ್ಜೆ: ಪ್ರಾಂಪ್ಟ್‌ಐ ಪ್ರೋಗ್ರಾಂ
1:54 ಕೇವಲ ಮೇಲ್ವಿಚಾರಣೆ ಮತ್ತು ಸಲಹೆ
2:10 ಮೂರನೇ ಹೆಜ್ಜೆ: ಬೆಳಗಿನ ವರದಿ
2:25 ರಾಜಿಗಳು, ಪ್ರಾಮಾಣಿಕವಾಗಿ
2:38 ಪ್ಯಾಟರ್ನ್ ಕದಿಯಿರಿ

ಸ್ಟಾಕ್: macOS say + ffmpeg + headless Chromium ಪೈಪ್‌ಲೈನ್; 37 ಭಾಷೆಗಳಲ್ಲಿ ಉಪಶೀರ್ಷಿಕೆಗಳು; MIT
```

### Tags

```text
ai ಏಜೆಂಟ್, whatsapp ಬಾಟ್, ಕ್ಲೌಡ್, ಸದಾ ಚಾಲು, ಮೇಲ್ವಿಚಾರಣೆ, ಪ್ರಾಂಪ್ಟ್, ಆಟೊಮೇಷನ್, devops, kannada
```

***

## Arabic (`ar`) — 4:33

### Title

```text
أغلق الحاسوب المحمول. واصل الوكيل العمل: وكيل سحابي دائم التشغيل عبر واتساب
```

### Description

```text
وكيل سحابي دائم التشغيل يُدار من محادثة واتساب: انشر OpenClaw على نسخة Lighthouse،
وراقب الأسعار والمخزون طوال الليل، واقرأ التقرير صباحًا — بينما يبقى حاسوبك مغلقًا.
يتضمن التوجيه وحدود الصلاحيات وخطوات التحقق الصباحية.

الكود وكتاب التوجيهات: https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

الفصول (الخط الزمني الإنجليزي):
0:00 أغلق الحاسوب المحمول. واصل الوكيل العمل.
0:11 الحاسوب نصف المفتوح هو المشكلة
0:33 المسألة الحقيقية هي الليل
0:44 ثلاث طبقات، نسخة واحدة
0:57 أين يعيش الوكيل؟
1:11 الخطوة الأولى: النشر والربط
1:38 الخطوة الثانية: التوجيه هو البرنامج
1:54 المراقبة والنصيحة فقط
2:10 الخطوة الثالثة: تقرير الصباح
2:25 المقايضات، بصراحة
2:38 اسرق النمط

التقنيات: macOS say + ffmpeg + headless Chromium؛ ترجمات بـ37 لغة؛ MIT
```

### Tags

```text
وكيل ذكاء اصطناعي, واتساب, سحابة, دائم التشغيل, مراقبة, هندسة التوجيه, أتمتة, devops, arabic
```

***

## Spanish (`es`) — 2:57

### Title

```text
Cierra el portátil. El agente sigue trabajando: ops en la nube con WhatsApp
```

### Description

```text
Un patrón de agente siempre encendido para operaciones en la nube: OpenClaw en una instancia
Lighthouse, controlado desde un chat de WhatsApp, vigilando precios y stock de noche mientras
el portátil sigue cerrado. Incluye el prompt, los límites de autoridad y el bucle de
verificación matutino.

Código y recetario de prompts:
https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

Capítulos (línea de tiempo en inglés):
0:00 Cierra el portátil. El agente sigue trabajando.
0:11 El portátil entreabierto es el problema
0:33 El verdadero problema es la noche
0:44 Tres capas, una instancia
0:57 ¿Dónde debería vivir el agente?
1:11 Paso uno: desplegar y conectar
1:38 Paso dos: el prompt es el programa
1:54 Solo observar y recomendar
2:10 Paso tres: el informe matutino
2:25 Compensaciones, con honestidad
2:38 Roba el patrón

Stack: macOS say + ffmpeg + headless Chromium; subtítulos en 37 idiomas; MIT
```

### Tags

```text
agente de ia, whatsapp, nube, siempre encendido, monitoreo, prompts, automatización, devops, español
```

***

## Portuguese (`pt`) — 3:47

### Title

```text
Feche o portátil. O agente continua trabalhando: ops na nuvem com WhatsApp
```

### Description

```text
Um padrão de agente sempre ligado para operações na nuvem: OpenClaw numa instância
Lighthouse, controlado por um chat de WhatsApp, vigiando preços e estoque durante a noite
enquanto o portátil fica fechado. Inclui o prompt, os limites de autoridade e o ciclo de
verificação da manhã.

Código e livro de receitas de prompts:
https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

Capítulos (linha do tempo em inglês):
0:00 Feche o portátil. O agente continua trabalhando.
0:11 O portátil entreaberto é o problema
0:33 O verdadeiro problema é a noite
0:44 Três camadas, uma instância
0:57 Onde o agente deveria morar?
1:11 Passo um: implantar e conectar
1:38 Passo dois: o prompt é o programa
1:54 Apenas observar e recomendar
2:10 Passo três: o relatório da manhã
2:25 Trade-offs, com honestidade
2:38 Roube o padrão

Stack: macOS say + ffmpeg + headless Chromium; legendas em 37 idiomas; MIT
```

### Tags

```text
agente de ia, whatsapp, nuvem, sempre ligado, monitoramento, prompts, automação, devops, português
```

***

## Russian (`ru`) — 3:23

### Title

```text
Закройте ноутбук. Агент продолжит работу: облачные операции через WhatsApp
```

### Description

```text
Паттерн постоянно работающего агента для облачных операций: OpenClaw на инстансе
Lighthouse, управляемый из чата WhatsApp, следит за ценами и запасами ночью, пока
ноутбук закрыт. Включены промпт, границы полномочий и утренний цикл проверки.

Код и кулинарная книга промптов:
https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

Главы (английский таймлайн):
0:00 Закройте ноутбук. Агент продолжит работу.
0:11 Полуоткрытый ноутбук — вот проблема
0:33 Настоящая проблема — ночь
0:44 Три слоя, один инстанс
0:57 Где должен жить агент?
1:11 Шаг первый: развернуть и подключить
1:38 Шаг второй: промпт — это программа
1:54 Только наблюдать и рекомендовать
2:10 Шаг третий: утренний отчёт
2:25 Компромиссы, честно
2:38 Украдите шаблон

Стек: macOS say + ffmpeg + headless Chromium; субтитры на 37 языках; MIT
```

### Tags

```text
ии агент, whatsapp, облако, всегда включён, мониторинг, промпты, автоматизация, devops, русский
```

***

## Japanese (`ja`) — 4:06

### Title

```text
ノートPCを閉じても、エージェントは働き続ける：WhatsAppで動く常時稼働クラウドエージェント
```

### Description

```text
WhatsAppのチャットから操作する常時稼働のクラウドエージェント：OpenClawをLighthouse
インスタンスにデプロイし、一晩中価格と在庫を監視して、朝にレポートを読む — ノートPCは
閉じたまま。プロンプト、権限の境界、朝の検証ループまで解説します。

コードとプロンプトクックブック:
https://github.com/baneeishaque-ompventure/ai-agent-cloud-ops-demo

チャプター（英語タイムライン）:
0:00 ノートPCを閉じても、エージェントは働き続ける。
0:11 半開きのノートPCこそ問題
0:33 本当の問題は夜の時間帯
0:44 3つの層、1つのインスタンス
0:57 エージェントはどこに住むべきか
1:11 ステップ1：デプロイして接続する
1:38 ステップ2：プロンプトがプログラム
1:54 監視と提案だけ
2:10 ステップ3：朝のレポート
2:25 トレードオフを正直に
2:38 パターンを盗もう

スタック: macOS say + ffmpeg + headless Chromium パイプライン; 37言語の字幕; MIT
```

### Tags

```text
aiエージェント, whatsapp, クラウド, 常時稼働, 監視, プロンプト, 自動化, devops, 日本語
```

***

## Compact locales (27)

Titles below are each locale's own slide-1 title from `translations/<locale>.json`; append
`— always-on agent demo` when uploading. For descriptions, reuse the English description with
a translated first line; the repo URL, stack line, and chapter labels carry over. "Subtitles
only" means the video has no narration track (no system voice ships for that language).

| Locale | Language | Duration | Suggested title | Audio |
| ------ | -------- | -------- | --------------- | ----- |
| `as` | অসমীয়া | 3:13 | লেপটপ বন্ধ কৰক। এজেণ্ট চলি থাকক। | subtitles only |
| `bn` | বাংলা | 3:53 | ল্যাপটপ বন্ধ করুন। এজেন্ট কাজ চালিয়ে যাক। | narrated |
| `brx` | बड़ो | 2:54 | ल्यापटप बन्द खालाम। एजेन्टा खामानि खालामनो थाथार। | subtitles only |
| `de` | Deutsch | 3:36 | Laptop zuklappen. Der Agent arbeitet weiter. | narrated |
| `doi` | डोगरी | 3:42 | लैपटॉप बंद करो। एजेंट कम्म करदा रौ। | subtitles only |
| `fr` | Français | 3:17 | Fermez le portable. L'agent continue de travailler. | narrated |
| `gu` | ગુજરાતી | 3:18 | લેપટોપ બંધ કરો. એજન્ટ કામ કરતો રહે. | subtitles only |
| `id` | Bahasa Indonesia | 3:49 | Tutup laptop. Agen tetap bekerja. | narrated |
| `it` | Italiano | 3:11 | Chiudi il portatile. L'agente continua a lavorare. | narrated |
| `ko` | 한국어 | 3:30 | 노트북을 닫으세요. 에이전트는 계속 일합니다. | narrated |
| `kok` | कोंकणी | 2:55 | लॅपटॉप बंद करात. एजेंट काम करत रावूं. | subtitles only |
| `ks` | کٲشُر | 3:38 | لیپ ٹاپ بند کریو۔ ایجنٹ کٲم کران روزٕ۔ | subtitles only |
| `mai` | मैथिली | 3:28 | लैपटॉप बन्द करू। एजेन्ट काज करैत रहौ। | subtitles only |
| `mni` | মৈতৈলোন্ | 3:02 | ꯂꯦꯞꯇꯣꯞ ꯄꯥꯟꯊꯣꯛꯎ꯫ ꯑꯦꯖꯦꯟꯇ ꯊꯕꯛ ꯇꯧꯕ ꯉꯝꯍꯧ꯫ | subtitles only |
| `mr` | मराठी | 2:57 | लॅपटॉप बंद करा. एजंट काम करत राहू द्या. | subtitles only |
| `ne` | नेपाली | 2:57 | ल्यापटप बन्द गर्नुहोस्। एजेन्ट काम गरिरहोस्। | subtitles only |
| `or` | ଓଡ଼ିଆ | 2:55 | ଲାପଟପ୍ ବନ୍ଦ କରନ୍ତୁ। ଏଜେଣ୍ଟ କାମ କରୁଥାଉ। | subtitles only |
| `pa` | ਪੰਜਾਬੀ | 3:39 | ਲੈਪਟਾਪ ਬੰਦ ਕਰੋ। ਏਜੰਟ ਕੰਮ ਕਰਦਾ ਰਹੇ। | subtitles only |
| `sa` | संस्कृतम् | 2:30 | लैपटॉपं पिधायताम्। प्रतिनिधिः कार्यरतः भवतु। | subtitles only |
| `sat` | ᱥᱟᱱᱛᱟᱲᱤ | 3:26 | ᱞᱟᱯᱴᱚᱯ ᱵᱚᱸᱫᱽ ᱢᱮ᱾ ᱮᱡᱮᱸᱴ ᱠᱟᱹᱢᱤ ᱛᱮᱜᱮ ᱛᱟᱦᱮᱸᱱᱟ᱾ | subtitles only |
| `sd` | سنڌي | 3:46 | ليپ ٽاپ بند ڪريو. ايجنٽ ڪم ڪندو رهي. | subtitles only |
| `te` | తెలుగు | 3:44 | ల్యాప్‌టాప్ మూసేయండి. ఏజెంట్ పని చేస్తూనే ఉంటుంది. | narrated |
| `th` | ไทย | 3:59 | ปิดแล็ปท็อปได้ เอเจนต์ยังทำงานต่อ | narrated |
| `tr` | Türkçe | 3:33 | Dizüstü bilgisayarı kapat. Ajan çalışmaya devam etsin. | narrated |
| `ur` | اردو | 3:54 | لیپ ٹاپ بند کریں۔ ایجنٹ کام کرتا رہے۔ | subtitles only |
| `vi` | Tiếng Việt | 3:28 | Gập laptop lại. Tác nhân vẫn tiếp tục làm việc. | narrated |
| `zh` | 中文 | 3:30 | 合上笔记本，智能体继续工作。 | narrated |

## Playlist suggestion

Create one playlist — **"Always-on agent — full walkthrough"** — and start it with the
primary locales in locale order (`en`, `hi`, `ml`, `ta`, `kn`, `ar`), then the major global
narrations (`es`, `pt`, `ru`, `ja`, and the rest of the 20 narrated locales). Add the English
video as the playlist thumbnail source and the repository link in the playlist description.
The 17 subtitle-only locales can be uploaded as unlisted variants for search coverage.
