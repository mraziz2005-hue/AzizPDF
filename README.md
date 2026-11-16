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

## 🐧 Install locally from source / التشغيل من المصدر

Requirements: Linux desktop, **Python 3.12+**, Tkinter, venv and an internet connection to install dependencies the first time.

On Ubuntu / Linux Mint:

```bash
sudo apt install python3-tk python3-venv
./run.sh
```

The launcher creates a local `.venv` environment in the project folder. To open a PDF, use the app's **Open PDF** button or drag a PDF file into the window. No documents or saved signatures are included in this repository.

## 📦 Build/install as Snap / إنشاء حزمة Snap

Snapcraft 9 and LXD are required for the build. From the repository root:

```bash
snapcraft pack --use-lxd
sudo snap install --dangerous ./azizpdf_0.1.7_amd64.snap
```

Open **AzizPDF** from the Linux application menu or run `azizpdf`.

`--dangerous` means this is a **local, unsigned package**, not a package verified or distributed through the Snap Store. Packaging is configured for `core24`, `amd64`, `strict` confinement and `grade: devel`. A successfully built Snap is **not** a confirmed public Store release.

When using strict Snap confinement, signed images and settings are stored inside the Snap's app-specific data directory; an older signature from a non-Snap installation is not migrated automatically. Access to removable media may require connecting the relevant Snap interface.

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

For updates, see [CHANGELOG.md](CHANGELOG.md). For Store-release tasks, see [RELEASE_CHECKLIST.md](RELEASE_CHECKLIST.md).
