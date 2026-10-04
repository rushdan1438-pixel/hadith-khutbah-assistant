# الإعداد والتشغيل

## المتطلبات

لا يوجد أي متطلبات تثبيت. الحاجة الوحيدة: متصفح ويب حديث (Chrome, Safari, Edge, Firefox).

## التشغيل محليًا (نسخة كاملة بدون إنترنت تقريبًا)

```bash
git clone https://github.com/<your-username>/hadith-khutbah-assistant.git
cd hadith-khutbah-assistant
```

افتح `index.html` مباشرة من مستكشف الملفات، أو:

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# أو شغّل خادمًا محليًا بسيطًا (اختياري، لتفادي قيود CORS على بعض المتصفحات):
python3 -m http.server 8000
# ثم افتح http://localhost:8000
```

## التشغيل عبر الرابط المباشر (يشمل كل الميزات)

https://claude.ai/artifact/UtyggpQn9mwB6gYfexQt4M

هذا الرابط يشغّل نفس كود `index.html` داخل بيئة Claude Artifacts، وهو المكان الوحيد الذي تعمل فيه خاصية "تجهيز مسودة خطبة" (الطبقة الثالثة) بالكامل، لأنها تستدعي نموذجًا لغويًا عبر واجهة تلك البيئة.

## الأدوات المستخدمة في التطوير

| الأداة | الغرض |
|---|---|
| HTML5 / CSS3 | البنية والتنسيق |
| JavaScript (ES6+, Vanilla، بدون أطر عمل) | منطق التطبيق بالكامل |
| Google Fonts API (Amiri, Cairo) | الخطوط العربية |
| Claude (Anthropic) | التوليد المقيّد لمسودة الخطبة (الطبقة الثالثة فقط) |
| `localStorage` (متصفح المستخدم) | حفظ سجل العمليات محليًا، دون أي خادم خارجي |

## بنية الكود داخل `index.html`

- قاعدة بيانات الأحاديث: مصفوفة ثابتة `DB` (نص، درجة، مصدر، ملاحظة).
- دوال التطبيع والمطابقة: `normalize()`, `scoreMatch()`, `findBestMatch()`.
- دوال الواجهة: `checkSingle()`, `checkKhutbah()`, `prepareKhutbah()`.
- دوال السجل المحلي: `saveHistoryEntry()`, `renderHistory()`, `clearHistory()`.

لا توجد تبعيات خارجية (npm packages) ولا خطوة بناء (build step) — الملف جاهز للتشغيل كما هو.

## الترخيص

راجع [`../LICENSE`](../LICENSE) — رخصة MIT.
