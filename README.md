# 🐧 AzizPDF

**A friendly, free, offline PDF reader and editor for Linux.**  
**قارئ ومحرّر PDF للينكس — بسيط، كووول، ومريح.**

![AzizPDF interface](assets/screenshot.png)

AzizPDF is a lightweight desktop application for reading, annotating, signing and filling in PDF documents — without an account, cloud upload, or paid subscription. The interface is designed to make everyday PDF tasks simple.

**AzizPDF** برنامج مكتبي لفتح ملفات PDF وتصفحها، والكتابة عليها وتوقيعها وحفظها، بواجهة عربية سهلة ومن دون الحاجة إلى حساب أو اتصال بخدمة سحابية.

> **Status / الحالة:** Version **0.1.7 (early release)**. The Snap build has been tested on Ubuntu 26.04 by the project owner; other distributions and desktop environments may need testing. This is not a full Adobe Acrobat replacement.

## ✨ Features — المميزات

- 📂 **Open PDF files / فتح الملفات:** file picker, drag-and-drop, multi-page navigation and thumbnails.
- 🔎 **Read / القراءة:** zoom and search in text-based PDF documents.
- 📝 **Add text / إضافة نص:** click an exact location or drag to define a text box; supports Arabic and English input.
- ↔️ **Move and edit your added text / تحريك وتعديل النص المضاف:** drag it, or double-click to edit it, even after saving and reopening a PDF created with newer AzizPDF versions.
- 🟡 **Highlight / التظليل:** highlight searchable text; apply a translucent mark to image-only pages.
- ✏️ **Draw and annotate / الرسم والتعليقات:** add drawings, notes, shapes and images.
- ✍️ **Reusable signature / التوقيع المحفوظ:** draw once, save it locally, insert it into PDFs, move and resize it.
- 📑 **Organize pages / إدارة الصفحات:** rotate, move, remove and merge PDF pages.
- 💾 **Save and Save As / الحفظ:** save a new copy and undo recent edits.
- 🔒 **Offline / محلي:** no account and no PDF uploads from the app.

### ⚠️ Important limitations / ملاحظات مهمة

- Editing *existing* document text is **experimental**: the original formatting may change. Use **Save As** with important documents.
- Moving and double-click editing works for **AzizPDF-added editable text**, not arbitrary text already embedded in a PDF.
- Image-only/scanned PDFs do not gain OCR automatically.
- A saved drawn signature is a **visual signature image**, not a cryptographic digital certificate.
- Mixed Arabic and English layouts may still have edge cases.
- The exact experience can vary across Linux distributions and window managers.

## 📦 تحميل وتثبيت AzizPDF على Linux

### الملف المتاح والتوافق

حمّل [azizpdf_0.1.7_amd64.snap](https://github.com/mraziz2005-hue/AzizPDF/releases/download/v0.1.7/azizpdf_0.1.7_amd64.snap)، أو افتح [إصدار v0.1.7](https://github.com/mraziz2005-hue/AzizPDF/releases/tag/v0.1.7) ثم **Assets**.

| النظام / المعمارية | الحالة |
|---|---|
| Ubuntu 26.04 | اختبار حزمة Snap موثق سابقًا بواسطة صاحب المشروع |
| Fedora المكتبي التقليدي | تعليمات تجهيز Snap أدناه؛ تجربة AzizPDF عليه لم تتأكد بعد |
| Debian / Linux Mint | تعليمات تجهيز Snap متاحة؛ لم يُوثق اختبار التطبيق على جميع إصداراتهما |
| توزيعات أخرى | يلزم دعم Snap؛ لا نضمن جميع التوزيعات دون اختبار |
| x86_64 / AMD64 | الحزمة الحالية مناسبة لمعالجات Intel وAMD ذات 64 بت |
| ARM / aarch64 / 32 بت | حزمة amd64 الحالية غير مناسبة |

نفس حزمة التطبيق يمكن استخدامها على توزيعات Linux متعددة تدعم Snap؛ تختلف أوامر تجهيز Snap حسب التوزيعة.

**AzizPDF يستخدم strict confinement وفق وصف الحزمة الحالي؛ أمر تثبيته لا يحتاج `--classic`.** لا تنسخ خيارات تثبيت AzizDB أو AzizIDE إليه تلقائيًا.

تحتاج واجهة سطح مكتب وصلاحية `sudo` للتثبيت واتصال إنترنت لتنزيل الحزمة واعتماديات Snap. لا تحتاج Python أو Tkinter أو Snapcraft أو LXD لتثبيت الحزمة الجاهزة.

تحقق من توزيعتك ومعمارية الجهاز:

```bash
cat /etc/os-release
uname -m
```

الناتج `x86_64` يطابق الحزمة الحالية.

### 1. تجهيز Snap — مرة واحدة

```bash
snap version
```

إذا ظهرت إصدارات snap وsnapd، انتقل إلى الخطوة 2. **إذا سبق تجهيز Snap لتطبيق آخر، فلا تحتاج إعادة تجهيزه.**

إذا ظهر `command not found`، اتبع قسم توزيعتك فقط.

#### Ubuntu

إذا كان Snap غير مثبت:

```bash
sudo apt update
sudo apt install snapd
sudo systemctl enable --now snapd.socket
```

سجّل خروجًا وادخل مجددًا، أو أعد تشغيل الجهاز.

#### Fedora Workstation / KDE التقليدي

Fedora يستخدم `dnf`، وليس `apt`:

```bash
sudo dnf install snapd
sudo systemctl enable --now snapd.socket
```

سجّل خروجًا من جلسة سطح المكتب وادخل مجددًا، أو أعد تشغيل الجهاز، ثم تحقق:

```bash
snap version
```

إغلاق الطرفية وحده لا يُحدّث جلسة سطح المكتب. **لا تحتاج خطوة رابط Classic لتثبيت حزمة AzizPDF هذه.**

هذه التعليمات لفيدورا التقليدي، وليست وصفة مؤكدة لـ Silverblue أو Kinoite.

#### Debian

```bash
sudo apt update
sudo apt install snapd
sudo systemctl enable --now snapd.socket
```

سجّل خروجًا وادخل مجددًا، ثم نفّذ خطوة snapd الموصى بها في دليل Snap لـ Debian:

```bash
sudo snap install snapd
```

#### Linux Mint

قد يمنع Mint تثبيت Snap بملف `nosnap.pref`. إذا اخترت تفعيل Snap، انقل ملف المنع إلى نسخة احتياطية إن كان موجودًا:

```bash
if [ -f /etc/apt/preferences.d/nosnap.pref ]; then
    sudo mv -n /etc/apt/preferences.d/nosnap.pref /etc/apt/preferences.d/nosnap.pref.azizpdf-backup
fi
```

هذا يغيّر تفضيل Mint الذي يمنع تثبيت Snap. إذا بقي الملف الأصلي بسبب وجود نسخة احتياطية بالاسم نفسه، اختر اسم نسخة احتياطية آخر قبل المتابعة.

ثم:

```bash
sudo apt update
sudo apt install snapd
sudo systemctl enable --now snapd.socket
```

سجّل خروجًا وادخل مجددًا، أو أعد تشغيل الجهاز.

#### بقية التوزيعات

اتبع [دليل Snap الرسمي الخاص بتوزيعتك](https://snapcraft.io/docs/installing-snapd/)، ثم أكمل تثبيت التطبيق أدناه.

### 2. تثبيت الحزمة الجاهزة

حمّل ملف Snap إلى مجلد التنزيلات ثم:

```bash
cd ~/Downloads
ls -lh azizpdf_0.1.7_amd64.snap
```

إذا كان مجلد التنزيل باسم مختلف، افتحه في مدير الملفات واختر **فتح الطرفية هنا** بدل أمر `cd ~/Downloads`.

بعد التأكد من وجود الملف:

```bash
sudo snap install --dangerous ./azizpdf_0.1.7_amd64.snap
```

تحقق:

```bash
snap list azizpdf
```

الخيار `--dangerous` يسمح بتثبيت ملف محلي دون التحقق من توقيعه عبر المتجر؛ حمّل الملف من إصدار المشروع الموثوق. هذه تعليمات تثبيت محلي من GitHub، وليست تأكيدًا لتوفر التطبيق في Snap Store.

### 3. التشغيل

```bash
snap run azizpdf
```

أو ابحث عن **AzizPDF** في قائمة التطبيقات. شغّل البرنامج بحسابك العادي دون `sudo`.

يمكن حذف ملف التنزيل `.snap` بعد نجاح التثبيت؛ التطبيق المثبت لا يعتمد على بقاء ملف التنزيل.

### 4. إذا اشتغل ولم يظهر في قائمة التطبيقات

سجّل خروجًا وادخل مجددًا أولًا. إذا لم يظهر، افحص اختصارات الحزمة:

```bash
ls -l /var/lib/snapd/desktop/applications/azizpdf*.desktop
```

إذا ظهر الملف باسم `azizpdf_azizpdf.desktop`، أضف رابطًا له في قائمة حسابك:

```bash
if [ -f /var/lib/snapd/desktop/applications/azizpdf_azizpdf.desktop ]; then
    mkdir -p "$HOME/.local/share/applications"
    ln -sfnT /var/lib/snapd/desktop/applications/azizpdf_azizpdf.desktop "$HOME/.local/share/applications/azizpdf_azizpdf.desktop"
else
    printf '%s\n' 'لم يوجد الاختصار بهذا الاسم؛ راجع نتيجة ls قبل إنشاء الرابط.'
fi
```

إذا سبق تخصيص اختصار محلي بنفس الاسم، احتفظ بنسخة منه قبل استبداله.

أغلق القائمة وافتحها وابحث عن AzizPDF. إذا لم تتحدث، سجّل خروجًا وادخل مجددًا.

إذا ظهر اسم ملف آخر، استخدم الاسم الفعلي بدل تخمينه. إذا لم يوجد أي اختصار، لا تنشئ رابطًا لملف مفقود؛ أرفق نتيجة `snap list azizpdf` في بلاغ المشكلة.

## 📄 فتح الملفات والحفظ والوصول للفلاش

ابدأ بملف PDF تجريبي داخل مجلد `Documents` في مجلدك الشخصي، وافتحه من زر **Open PDF**. جرّب إضافة نص ثم **Save As** لحفظ نسخة جديدة وإعادة فتحها.

بسبب عزل Snap، قد يختلف الوصول إلى الملفات والإعدادات عن نسخة Python العادية.

افحص الواجهات الفعلية التي توفرها الحزمة:

```bash
snap connections azizpdf
```

### ملفات المجلد الشخصي

إذا ظهرت واجهة `azizpdf:home` وكان عمود Slot لها `-`، يمكنك وصلها:

```bash
sudo snap connect azizpdf:home
```

واجهة home تتيح عادة الوصول لملفات المستخدم غير المخفية داخل مجلده الشخصي، ولا تعني الوصول لكل ملفات النظام.

### الفلاش والأقراص الخارجية

إذا احتجت فتح الملفات مباشرة من وسيط خارجي، وكانت الحزمة تعرض واجهة `azizpdf:removable-media`، يمكنك وصلها:

```bash
sudo snap connect azizpdf:removable-media
```

هذا يمنح التطبيق وصولًا للوسائط الخارجية ضمن صلاحيات المستخدم. ليس مطلوبًا لاستخدام ملف داخل Documents.

إذا لم تظهر الواجهة في نتيجة الفحص، فلا تفترض أن الأمر سيضيفها للحزمة؛ انسخ ملفًا تجريبيًا إلى Documents، أو أبلغ عن الحاجة إلى دعم هذا المسار. لا تعالج مشكلة الوصول بتشغيل التطبيق كـ root.

الإعدادات والتوقيعات المحفوظة في نسخة Snap تُحفظ داخل بيانات التطبيق بحسب وصف الحزمة؛ توقيع نسخة Python القديمة لا ينتقل تلقائيًا. التوقيع المرسوم صورة مرئية، وليس شهادة توقيع رقمي مشفرة.

## 🛠️ المشاكل الشائعة

| المشكلة | الخطوة المناسبة |
|---|---|
| `snap: command not found` | اتبع قسم تجهيز Snap لتوزيعتك |
| `apt: command not found` على Fedora | استخدم dnf |
| ملف التثبيت غير موجود | افحص المجلد والاسم باستخدام `pwd` و`ls` |
| خطأ معمارية / `Exec format error` | افحص `uname -m`؛ الحزمة تحتاج x86_64 |
| يعمل ولا يظهر في القائمة | اتبع خطوة فحص وربط الاختصار أعلاه |
| لا يستطيع فتح ملف أو حفظه | افحص مكان الملف وصلاحياته وواجهات Snap، وجرّب Documents |
| البحث لا يجد نصًا في PDF مصوّر | لا توجد إضافة OCR تلقائية للملفات المصوّرة |
| النص الأصلي يتغير تنسيقه | تحرير النص الأصلي تجريبي؛ استخدم Save As |
| توقيع النسخة القديمة غير ظاهر | لا توجد هجرة تلقائية من بيانات نسخة Python إلى Snap |

إذا ظهر `snapd unavailable` أو `cannot communicate with server` على نظام تقليدي مما سبق:

```bash
sudo systemctl enable --now snapd.socket
systemctl status snapd.socket --no-pager
snap version
```

إذا لم يفتح البرنامج أو أغلق فورًا، شغّله من الطرفية وانسخ رسالة الخطأ:

```bash
snap run azizpdf
```

عند فتح [بلاغ مشكلة](https://github.com/mraziz2005-hue/AzizPDF/issues)، اذكر التوزيعة وإصدارها والمعمارية والخطوات والخطأ، مع:

```bash
snap version
snap list azizpdf
snap connections azizpdf
```

لا ترفق مستندات شخصية أو صور توقيعات؛ استخدم ملفًا تجريبيًا خاليًا من البيانات الحساسة.

## 🔄 التحديث والإزالة

الإصدارات الجديدة في [Releases](https://github.com/mraziz2005-hue/AzizPDF/releases). حمّل الحزمة الجديدة واتبع تعليمات إصدارها؛ التثبيت المحلي من GitHub لا يعني تحديث التطبيق تلقائيًا من GitHub.

لإزالة التطبيق، احفظ عملك واحتفظ بما تحتاجه من إعدادات وتوقيعات ثم:

```bash
sudo snap remove azizpdf
```

إذا أضفت رابط الاختصار يدويًا بالطريقة أعلاه، أزله:

```bash
if [ -L "$HOME/.local/share/applications/azizpdf_azizpdf.desktop" ]; then
    rm -- "$HOME/.local/share/applications/azizpdf_azizpdf.desktop"
fi
```

هذه ليست أوامر حذف ملفات PDF التي حفظتها خارج بيانات الحزمة.

## 🧑‍💻 التشغيل من المصدر وبناء الحزمة

**هذا قسم للمطورين، وليس مطلوبًا لتثبيت الملف الجاهز.**

وقت تحديث الدليل، المستودع يحتوي README فقط، والإصدار يرفق ملف Snap فقط. أرشيف المصدر الكامل وملفات `run.sh` و`snapcraft.yaml` غير متاحة هنا؛ ZIP التلقائي من GitHub ليس نسخة كاملة من التطبيق.

لمن يملك أرشيف المصدر الكامل سابقًا، متطلبات التشغيل الموثقة هي Linux وPython **3.12+** وTkinter وvenv واتصال إنترنت لتنزيل المكتبات أول مرة. تعليمات Ubuntu / Linux Mint السابقة، من داخل مجلد المصدر الفعلي:

```bash
sudo apt update
sudo apt install python3-tk python3-venv
python3 --version
bash run.sh
```

تحقق أن إصدار Python يحقق المتطلب؛ تثبيت الحزم وحده لا يضمن ذلك على كل إصدار توزيعة. وفق التعليمات السابقة، ينشئ المشغّل `.venv` داخل مجلد المشروع.

البناء الموثق سابقًا يحتاج Snapcraft 9 وLXD وملفات التغليف الكاملة، ثم من جذر المصدر:

```bash
snapcraft pack --use-lxd
```

وصف التغليف السابق يحدد `core24` و`amd64` و`strict` و`grade: devel`. لا يلزم بناء البرنامج لاستخدام ملف Snap المرفق، ونجاح البناء لا يعني نشرًا في المتجر.

## 📚 مراجع تجهيز Snap

رُوجعت التعليمات بتاريخ **17 نوفمبر 2026**:

- [Ubuntu](https://snapcraft.io/docs/tutorials/install-the-daemon/ubuntu/)
- [Fedora](https://snapcraft.io/docs/tutorials/install-the-daemon/fedora/)
- [Debian](https://snapcraft.io/docs/tutorials/install-the-daemon/debian/)
- [Linux Mint](https://snapcraft.io/docs/tutorials/install-the-daemon/linux-mint/)
- [صلاحية ملفات المجلد الشخصي](https://snapcraft.io/docs/reference/interfaces/home-interface/)
- [صلاحية الوسائط الخارجية](https://snapcraft.io/docs/reference/interfaces/removable-media-interface/)

هذه مراجع إعداد Snap، وليست إثباتًا لاختبار AzizPDF على كل توزيعة.

## 🌍 English installation quick start

Download the **azizpdf_0.1.7_amd64.snap** release asset. Prepare snapd for your distribution using the detailed instructions above, log out and back in if newly installed, then:

```bash
cd ~/Downloads
sudo snap install --dangerous ./azizpdf_0.1.7_amd64.snap
snap run azizpdf
```

This is a local **strict** Snap; do not add `--classic`. The build targets x86_64 / AMD64. No manual Python, Tkinter, Snapcraft or LXD setup is needed to install the prebuilt package.

If the app runs but is absent from the menu, inspect its actual desktop-file name and follow the conditional shortcut procedure above.

File access depends on the interfaces the package declares. Check `snap connections azizpdf` before connecting home or removable-media access. The full source archive is not currently attached; GitHub's automatic source ZIP is not a substitute.


## 🛠️ Built with

- Python + Tkinter
- [PyMuPDF](https://pymupdf.io/) (PDF processing)
- [Pillow](https://python-pillow.github.io/)
- `python-bidi`, `arabic-reshaper` (Arabic display)
- `tkinterdnd2` (file drag-and-drop)

## 📜 Licensing / الترخيص

**Important before public release:** PyMuPDF offers an **AGPLv3** or commercial license. The planned public, source-available release should use **GNU AGPLv3** for AzizPDF and include the complete `LICENSE` text along with applicable third-party notices, provided the publisher agrees to these terms. See [PyMuPDF licensing](https://pymupdf.io/licensing) and the [GNU AGPLv3 license](https://www.gnu.org/licenses/agpl-3.0.html).

**Before you publish this repository publicly, create its `LICENSE` file using GitHub's `GNU Affero General Public License v3.0` template.** This prepared source ZIP intentionally does not make a new license choice on behalf of the project owner. Review third-party attribution and licensing requirements before distributing the Snap publicly.

**قبل نشر المستودع للعامة:** اختر ترخيص **AGPL-3.0** وأضف ملف `LICENSE` كاملًا من قالب GitHub الرسمي، ثم راجع تراخيص المكتبات المستخدمة.

## 🧩 Known issues and contributions

Version 0.1.7 focuses on basic usability. Bug reports should include the Linux distribution, app version, steps to reproduce, and the exact error message — **without uploading personal PDFs or signatures**.

For published downloads, see [Releases](https://github.com/mraziz2005-hue/AzizPDF/releases). The previously referenced CHANGELOG.md and RELEASE_CHECKLIST.md are not currently present in this repository.
