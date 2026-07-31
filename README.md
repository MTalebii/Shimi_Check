# آزمون تعاملی شیمی دوازدهم (Chem12 Final Exam)

اپلیکیشن تحت وب مرور امتحان نهایی شیمی ۳ — ۲ نسخه (متوسط / سخت)، ۳۲ سؤال تشریحی با پاسخ‌نامهٔ گام‌به‌گام، کاملاً RTL و بهینه‌شده برای موبایل.

## ساختار فایل‌ها

```
index.html      صفحهٔ انتخاب نسخه + نمایش پیشرفت (کوکی)
exam-a.html     نسخهٔ متوسط (۱۶ سؤال · ۲۰ نمره)
exam-b.html     نسخهٔ سخت  (۱۶ سؤال · ۲۰ نمره)
server.js       وب‌سرور ایستای بدون وابستگی (Node)
package.json    اسکریپت start برای Railway
railway.json    تنزیمات دیپلوی Railway (healthcheck: /healthz)
Dockerfile      گزینهٔ دوم دیپلوی (اختیاری)
```

هر سه فایل HTML کاملاً مستقل (self-contained) هستند؛ هیچ build یا وابستگی npm لازم نیست.

## اجرای محلی

```bash
node server.js
# http://localhost:3000
```

یا فقط `index.html` را با مرورگر باز کن.

## آپلود روی GitHub

```bash
git init
git add .
git commit -m "feat: chem12 interactive final exam (medium + hard)"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

## دیپلوی روی Railway

1. در [railway.app](https://railway.app) → **New Project** → **Deploy from GitHub repo**
2. ریپوزیتوری را انتخاب کن؛ Railway خودش Node را تشخیص می‌دهد (Nixpacks).
3. نیاز به هیچ متغیر محیطی نیست؛ پورت از `process.env.PORT` خوانده می‌شود.
4. در بخش **Settings → Networking** گزینهٔ **Generate Domain** را بزن تا لینک عمومی بگیری.

Start command: `node server.js` · Healthcheck: `/healthz`

## ذخیرهٔ پیشرفت کاربر

- درون هر آزمون، وضعیت دقیق جلسه در `localStorage` ذخیره می‌شود.
- همزمان خلاصهٔ پیشرفت در کوکی نوشته می‌شود تا صفحهٔ انتخاب نسخه بتواند آن را نشان دهد:
  - `chem12_progress_a` و `chem12_progress_b` → `{done,total,strong,shaky,weak,i,mode,ts}`
  - `chem12_last_exam` → `a` یا `b` (برای دکمهٔ «ادامهٔ آخرین آزمون»)
- عمر کوکی: ۱ سال · `SameSite=Lax` · بدون ارسال هیچ داده‌ای به سرور.
- دکمهٔ «پاک کردن پیشرفت» در صفحهٔ اول هم کوکی‌ها و هم localStorage را پاک می‌کند.

## منبع علمی

سؤال‌ها و پاسخ‌ها براساس بانک سؤال ۳۳ دوره امتحان نهایی شیمی دوازدهم (۹۷ تا ۱۴۰۵) و راهنمای تصحیح رسمی بازبینی و بازنویسی شده‌اند.

---

توسعه‌دهنده: [@forkcode](https://t.me/forkcode) · ارتباط مستقیم: [@Oxmit](https://t.me/Oxmit)
