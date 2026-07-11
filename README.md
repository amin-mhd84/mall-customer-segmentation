<div align="center">

# 🛍️ Mall Customer Segmentation

### خوشه‌بندی مشتریان مرکز خرید با K-Means برای کمپین‌های بازاریابی هدفمند

<p>
  <img alt="python" src="https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white">
  <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-KMeans-F7931E?logo=scikitlearn&logoColor=white">
  <img alt="pandas" src="https://img.shields.io/badge/pandas-data%20wrangling-150458?logo=pandas&logoColor=white">
  <img alt="status" src="https://img.shields.io/badge/status-completed-brightgreen">
  <img alt="license" src="https://img.shields.io/badge/license-MIT-lightgrey">
  <img alt="silhouette" src="https://img.shields.io/badge/Silhouette%20Score-0.43-9cf">
</p>

<p><i>یک پروژه‌ی سرتاسری Unsupervised Learning: از داده‌ی خام تا بینش قابل‌اجرا برای تیم بازاریابی 🎯</i></p>

</div>

---

## 📖 فهرست مطالب

- [معرفی پروژه](#-معرفی-پروژه)
- [پیش‌نمایش نتیجه](#️-پیش‌نمایش-نتیجه)
- [یافته‌های کلیدی](#-یافته‌های-کلیدی)
- [ساختار پروژه](#-ساختار-پروژه)
- [روش انجام کار](#️-روش-انجام-کار)
- [اجرای پروژه](#-اجرای-پروژه)
- [تکنولوژی‌ها](#-تکنولوژی‌ها)
- [دیتاست](#-دیتاست)
- [مراحل بعدی پیشنهادی](#-مراحل-بعدی-پیشنهادی)
- [مشارکت](#-مشارکت)
- [مجوز](#-مجوز)

---

## 📌 معرفی پروژه

این پروژه مشتریان یک مرکز خرید را بر اساس **سن**، **جنسیت**، **درآمد سالانه** و **امتیاز خرج‌کرد** به گروه‌های معنادار (خوشه) تقسیم می‌کند. هدف، شناخت رفتار بخش‌های مختلف مشتریان است تا تیم بازاریابی به‌جای اجرای یک کمپین یکسان برای همه، برای هر گروه پیشنهاد و کمپین اختصاصی طراحی کند.

مدل مورد استفاده **K-Means** است؛ تعداد بهینه‌ی خوشه‌ها هم به‌جای حدس دستی، از ترکیب **Elbow Method** و **Silhouette Score** به‌صورت کاملاً داده‌محور به دست آمده است.

**چرا این پروژه؟**
- 🔍 EDA کامل قبل از مدل‌سازی (توزیع‌ها، همبستگی‌ها، بررسی داده‌ی گمشده)
- 🧩 پایپلاین پیش‌پردازش ماژولار و قابل استفاده‌ی مجدد (`Preprocessor`)
- 📈 انتخاب k به روش علمی، نه حدسی
- 🏷️ تفسیر کسب‌وکاری واقعی برای هر خوشه، نه فقط عدد خام

## 🖼️ پیش‌نمایش نتیجه

<div align="center">
  <img width="863" height="642" alt="imagescluster_scatter png" src="https://github.com/user-attachments/assets/6a421525-76ee-4322-994a-dd23e3da40fb" />
  <p><sub>خوشه‌بندی نهایی مشتریان بر اساس درآمد سالانه و امتیاز خرج‌کرد</sub></p>
</div>

<details>
<summary>📊 نمودارهای بیشتر (کلیک کنید)</summary>
<br>

| Elbow & Silhouette | توزیع ویژگی‌ها |
|:---:|:---:|
| <img width="693" height="241" alt="Screenshot 2026-07-11 113242" src="https://github.com/user-attachments/assets/b6d8bfd4-078e-4c31-b9ac-ff8081a7b114" /> | <img width="1248" height="322" alt="Screenshot 2026-07-11 113434" src="https://github.com/user-attachments/assets/614c4372-fa51-4e07-9b45-0dec3f555ba0" /> |

</details>

## 🧠 یافته‌های کلیدی

با اجرای پایپلاین روی دیتاست، **۶ خوشه‌ی بهینه** با **Silhouette Score ≈ 0.43** شناسایی شد:

| خوشه | میانگین سن | میانگین درآمد سالانه (k$) | میانگین امتیاز خرج‌کرد | تعداد | برچسب کسب‌وکاری |
|:---:|:---:|:---:|:---:|:---:|---|
| 3 | ۳۲.۷ | ۸۶.۵ | ۸۲.۱ | ۳۹ |  **VIP** — درآمد و خرج‌کرد بالا |
| 0 | ۴۱.۹ | ۸۸.۹ | ۱۷.۰ | ۳۳ |  توان خرید بالا، جذب‌نشده |
| 2 | ۲۵.۲ | ۲۵.۸ | ۷۶.۹ | ۲۴ |  جوان و پرخرج، درآمد کم |
| 5 | ۴۵.۵ | ۲۶.۳ | ۱۹.۴ | ۲۱ |  درآمد و خرج‌کرد پایین |
| 1 | ۵۶.۳ | ۵۴.۳ | ۴۹.۱ | ۴۵ |  میانسال، متعادل |
| 4 | ۲۶.۷ | ۵۷.۶ | ۴۷.۸ | ۳۸ |  جوان، متعادل |

>  این جدول خروجی واقعی سلول تفسیر خوشه‌ها در نوت‌بوک است. چون `random_state=42` ثابت است، اجرای مجدد نوت‌بوک همین اعداد را بازتولید می‌کند.

**پیشنهادهای عملیاتی برای بازاریابی:**
- خوشه‌ی VIP (۳) → برنامه‌ی وفاداری و دسترسی زودهنگام به تخفیف‌ها
- خوشه‌ی «توان بالا/جذب‌نشده» (۰) → کمپین‌های ترغیبی و ایمیل‌های شخصی‌سازی‌شده
- خوشه‌ی «جوان پرخرج» (۲) → پیشنهادهای اقساطی و محصولات مقرون‌به‌صرفه

## 📁 ساختار پروژه

```
mall-customer-segmentation/
├── data/
│   ├── Mall_Customers.csv                  # داده‌ی خام
│   └── mall_customers_with_clusters.csv    # خروجی نهایی همراه با برچسب خوشه
├── notebooks/
│   └── mall_customer_segmentation.ipynb    # نوت‌بوک اصلی تحلیل و مدل‌سازی
├── src/
│   └── preprocessor.py                     # کلاس پیش‌پردازش قابل استفاده‌ی مجدد
├── models/
│   └── kmeans_model.joblib                 # مدل نهایی آموزش‌دیده
├── images/                                  # نمودارهای تولیدشده توسط نوت‌بوک
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md
```

## ⚙️ روش انجام کار

| مرحله | توضیح |
|---|---|
| ۱. EDA | بررسی توزیع سن/درآمد/خرج‌کرد، توزیع جنسیت، ماتریس همبستگی، بررسی داده‌ی گمشده |
| ۲. پیش‌پردازش | انکود کردن جنسیت + نرمال‌سازی ویژگی‌های عددی با `StandardScaler` از طریق کلاس `Preprocessor` |
| ۳. انتخاب k | ترکیب Elbow Method و Silhouette Score برای k از ۲ تا ۱۰ |
| ۴. آموزش مدل | `KMeans` با `k-means++`، `n_init=12`، `random_state=42` برای پایداری و تکرارپذیری |
| ۵. ارزیابی | محاسبه‌ی Silhouette Score نهایی |
| ۶. تفسیر کسب‌وکاری | پروفایل‌سازی هر خوشه و تبدیل آن به بینش قابل‌اقدام برای تیم بازاریابی |

## اجرای پروژه

```bash
# ۱. کلون کردن ریپازیتوری
git clone https://github.com/<username>/mall-customer-segmentation.git
cd mall-customer-segmentation

# ۲. ساخت محیط مجازی (اختیاری ولی توصیه‌شده)
python -m venv venv
source venv/bin/activate      # ویندوز: venv\Scripts\activate

# ۳. نصب وابستگی‌ها
pip install -r requirements.txt

# ۴. اجرای نوت‌بوک
jupyter notebook notebooks/mall_customer_segmentation.ipynb
```

## 🧰 تکنولوژی‌ها

<p>
  <img src="https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/-Pandas-150458?logo=pandas&logoColor=white">
  <img src="https://img.shields.io/badge/-NumPy-013243?logo=numpy&logoColor=white">
  <img src="https://img.shields.io/badge/-scikit--learn-F7931E?logo=scikitlearn&logoColor=white">
  <img src="https://img.shields.io/badge/-Matplotlib-11557C?logo=plotly&logoColor=white">
  <img src="https://img.shields.io/badge/-Seaborn-3776AB">
  <img src="https://img.shields.io/badge/-Jupyter-F37626?logo=jupyter&logoColor=white">
</p>

- **pandas / NumPy** — پردازش و مهندسی داده
- **scikit-learn** — `KMeans`، `StandardScaler`، `silhouette_score`
- **Matplotlib / Seaborn** — نمایش بصری
- **Joblib** — ذخیره‌سازی و بارگذاری مدل

## 📊 دیتاست

[Mall Customer Segmentation Data](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python) — شامل ۲۰۰ رکورد مشتری با ستون‌های `CustomerID`، `Gender`، `Age`، `Annual Income (k$)` و `Spending Score (1-100)`.

## مراحل بعدی پیشنهادی

- [ ] افزودن ویژگی‌های رفتاری بیشتر (دفعات بازدید، سبد خرید، دسته‌بندی محصولات)
- [ ] مقایسه با الگوریتم‌های دیگر (DBSCAN، Gaussian Mixture، Hierarchical Clustering)
- [ ] ساخت داشبورد زنده با Streamlit برای تیم بازاریابی
- [ ] استقرار مدل به‌صورت API برای پیش‌بینی خوشه‌ی مشتریان جدید

## 🤝 مشارکت

مشارکت‌ها همیشه خوش‌آمدند! برای مشارکت:

1. ریپازیتوری را Fork کنید
2. یک برنچ جدید بسازید (`git checkout -b feature/awesome-feature`)
3. تغییرات را کامیت کنید (`git commit -m 'Add awesome feature'`)
4. برنچ را Push کنید (`git push origin feature/awesome-feature`)
5. یک Pull Request باز کنید

## مجوز

این پروژه تحت مجوز [MIT](LICENSE) منتشر شده است — استفاده، تغییر و توزیع آزاد است.

---

<div align="center">

</div>
