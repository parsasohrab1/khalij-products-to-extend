# Khalij-Karoun-Isocyanate-Safety-Color-Quality-Digital-Twin-System (Khalij-KISQ)

## سامانه هوشمند هشدار پیش‌گیرانه واکنش‌های فرار گرمایی (Thermal Runaway) در راکتورهای نیتراسیون/هیدروژناسیون و حسگر مجازی رنگ و درصد NCO محصولات TDI/MDI — محصول اختصاصی شرکت پتروشیمی کارون

> این سند یک محصول **اختصاصی** برای شرکت پتروشیمی کارون است — نخستین و تنها تولیدکننده ایزوسیانات‌ها (TDI، MDI، PMI) در خاورمیانه. این شرکت با زنجیره فرایندی کاملاً متفاوت از سایر شرکت‌های هلدینگ (نیتراسیون آروماتیک → هیدروژناسیون → فسژناسیون) نیازمند محصولی اختصاصی است.

---

## ۰. شناخت شرکت پتروشیمی کارون و شکاف فنی

**منابع:** [ویکی‌پدیا فارسی — پتروشیمی کارون](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%DA%A9%D8%A7%D8%B1%D9%88%D9%86)، [سایت رسمی krnpc.ir](https://krnpc.ir/)

### محصولات و ماهیت فرایند

| ویژگی | مقدار |
|---|---|
| محصولات | TDI (تولوئن دی‌ایزوسیانات)، MDI (متیلن دی‌فنیل دی‌ایزوسیانات)، گریدهای PMDI |
| جایگاه | نخستین تولیدکننده ایزوسیانات‌ها در خاورمیانه |
| تأسیس/افتتاح | ۱۳۸۱ / اسفند ۱۳۸۷ |
| محل | بندرامام خمینی — سایت ۲ منطقه ویژه اقتصادی پتروشیمی |

**زنجیره فرایندی فنی (پایه طراحی محصول):** تولید TDI/MDI شامل دو مرحله بحرانی متفاوت است:
1. **نیتراسیون آروماتیک** (تولوئن→دی‌نیتروتولوئن برای TDI؛ یا تراکم آنیلین-فرمالدهید برای MDA) و سپس **هیدروژناسیون** به آمین — واکنش‌های شدیداً گرمازا با ریسک واقعی **فرار گرمایی (Thermal Runaway)** و انفجار ترکیبات نیترو آروماتیک (یکی از خطرناک‌ترین دسته واکنش‌های صنعت شیمیایی).
2. **فسژناسیون** آمین (TDA/MDA) به ایزوسیانات — همانند خوزستان، از فسژن استفاده می‌شود اما محصول و شیمی پایین‌دستی کاملاً متفاوت است (رنگ و درصد NCO محصول نهایی، نه وزن مولکولی پلیمر).

### شکاف فنی نسبت به محصولات ۱ تا ۴ هلدینگ و محصول خوزستان

| محصول | چرا برای کارون کافی نیست |
|---|---|
| محصولات ۱-۴ هلدینگ | هیچ‌کدام واکنش نیتراسیون/هیدروژناسیون آروماتیک یا محصول ایزوسیانات را پوشش نمی‌دهند |
| محصول اختصاصی خوزستان (Khalij-KPSI) | روی **تعادل جرمی فسژن** (نشت) و کیفیت **پلیمر** (وزن مولکولی PC) تمرکز دارد؛ ریسک اصلی کارون **فرار گرمایی واکنش نیتراسیون** است (فیزیک ایمنی کاملاً متفاوت: انفجار گرمازا در برابر نشت گاز) و کیفیت هدف آن **رنگ/NCO% مونومر ایزوسیانات** است، نه وزن مولکولی پلیمر |

**نتیجه:** کارون نیاز به لایه ایمنی اختصاصی «فرار گرمایی نیتراسیون» دارد که در هیچ محصول دیگر هلدینگ (شامل محصول خوزستان) پوشش داده نشده، به‌همراه حسگر مجازی کیفیت رنگ/NCO مخصوص ایزوسیانات.

---

## ۱. سابقه ثبت اختراع و تحلیل رقابتی

| ردیف | اختراع/فناوری موجود | محدودیت اصلی | تفاوت این محصول |
|---|---|---|---|
| ۱ | مطالعه AIChE — *A Machine Learning Tool for Thermal Runaway Prediction of Chemical Reactors* (Random Forest) | مدل عمومی برای راکتورهای batch/بستر ثابت؛ به زنجیره خاص نیتراسیون-هیدروژناسیون-فسژناسیون TDI/MDI متصل نیست | تطبیق و اتصال مستقیم به زنجیره فرایندی واقعی تولید TDI/MDI با داده DCS صنعتی |
| ۲ | **Soft-sensor development for product quality estimation... in industrial MDI production** (ScienceDirect، تحقیقاتی) | فقط حسگر مجازی کیفیت (تأخیر زمانی/انتخاب ویژگی)؛ فاقد لایه ایمنی فرار گرمایی و فاقد ثبت اختراع رسمی | ترکیب لایه ایمنی فرار گرمایی + حسگر مجازی کیفیت در یک محصول صنعتی واحد با ثبت اختراع |
| ۳ | **US 10,189,945** – *Method for producing light-coloured TDI-polyisocyanates* | راهکار شیمیایی/فرایندی برای بهبود رنگ (تغییر فرمولاسیون)؛ رویکرد ماده‌ای نه پیش‌بینی نرم‌افزاری بلادرنگ | پیش‌بینی و کنترل پیش‌بین بلادرنگ رنگ محصول از پارامترهای فرایند موجود، بدون تغییر فرمولاسیون |
| ۴ | **US 8,748,655** – *Process for preparing light-coloured isocyanates of the diphenylmethane series* | مشابه فوق، راهکار فرایندی/شیمیایی ثابت | مکمل: لایه نرم‌افزاری پیش‌بینی و هشدار زودهنگام رنگ برای هر دسته تولید |

### نوآوری اصلی قابل ثبت اختراع (Core Patentable Claim)

> **"سامانه دوقلوی دیجیتال زنجیره‌ای ایزوسیانات که برای نخستین‌بار هشدار پیش‌گیرانه فرار گرمایی در واکنش‌گاه‌های نیتراسیون/هیدروژناسیون آروماتیک (بر مبنای روند اختلاف نرخ تولید-دفع گرما) را با حسگر مجازی بلادرنگ رنگ (Hazen/APHA) و درصد NCO محصول نهایی فسژناسیون، در یک مدل ریسک-کیفیت یکپارچه با حلقه بازخورد بسته ترکیب می‌کند."**

---

## ۲. سند SRS – محصول اختصاصی پتروشیمی کارون

### ۲-۱. مقدمه
**هدف:** افزایش ایمنی فرایندی واکنش‌های نیتراسیون/هیدروژناسیون از طریق هشدار پیش‌گیرانه فرار گرمایی، و تضمین کیفیت رنگ/NCO محصولات TDI/MDI از طریق حسگر مجازی بلادرنگ.

**چالش‌های میدانی:**
- واکنش‌های نیتراسیون آروماتیک به‌شدت گرمازا هستند و کنترل ناکافی می‌تواند به فرار گرمایی (Thermal Runaway) و حادثه فاجعه‌بار منجر شود.
- رنگ محصول TDI/MDI (شاخص Hazen/APHA) و درصد NCO معمولاً با تأخیر آزمایشگاهی اندازه‌گیری می‌شود، در حالی‌که کیفیت رنگ مستقیماً روی ارزش فروش محصول (خصوصاً برای کاربرد فوم صلب و پوشش) اثر دارد.

**دامنه:** مجتمع کارون، سایت ۲ بندرامام؛ اتصال به DCS واحدهای نیتراسیون، هیدروژناسیون و فسژناسیون.

### ۲-۲. نیازمندی‌های کلی

| شناسه | نیاز | اولویت |
| :--- | :--- | :--- |
| R-GEN-01 | دریافت داده لحظه‌ای دما/فشار/نرخ تخلیه گرما راکتورهای نیتراسیون و هیدروژناسیون | بحرانی (HSE) |
| R-GEN-02 | دریافت داده فرایندی واحد فسژناسیون (نسبت فسژن/آمین، دما، زمان ماند) | بالا |
| R-GEN-03 | داشبورد ایمنی-کیفیت مجزا مشابه ساختار محصول خوزستان اما با مدل‌های اختصاصی این شرکت | بالا |

### ۲-۳. نیازمندی‌های عملکردی

| شناسه | نیاز | قابلیت ثبت اختراع |
| :--- | :--- | :--- |
| FR-SAFE-01 | هشدار پیش‌گیرانه فرار گرمایی از روند اختلاف نرخ تولید/دفع گرما در راکتورهای نیتراسیون/هیدروژناسیون | **پیش‌بینی فرار گرمایی زنجیره‌ای اختصاصی ایزوسیانات (نوآوری اصلی)** |
| FR-QUAL-01 | حسگر مجازی بلادرنگ رنگ (Hazen/APHA) و درصد NCO محصول فسژناسیون | حسگر مجازی کیفیت رنگ/NCO بدون انتظار آزمایشگاه |
| FR-CHAIN-01 | مدل ترکیبی ریسک-کیفیت که اثر انحراف ایمنی مرحله اول را روی کیفیت محصول نهایی برآورد می‌کند | **مدل یکپارچه ریسک-کیفیت (نوآوری اصلی)** |
| FR-ALERT-01 | هشدار سطح‌بندی‌شده HSE با اولویت بحرانی مجزا از هشدار کیفیت | توصیه‌گر دوگانه |
| FR-LOOP-01 | ثبت نتایج واقعی آزمایشگاهی و رویدادهای ایمنی برای بازآموزی مدل | یادگیری بسته |

### ۲-۴. نیازمندی‌های غیرعملکردی

| شناسه | نیاز | مقدار هدف |
| :--- | :--- | :--- |
| NFR-SAFE-01 | تأخیر هشدار فرار گرمایی | کمتر از ۲ ثانیه (بحرانی) |
| NFR-PER-01 | دقت پیش‌بینی رنگ محصول (MAPE) | کمتر از ۱۰٪ |
| NFR-AVAIL-01 | در دسترس بودن ماژول ایمنی | ۹۹.۹۹٪ |

### ۲-۵. معماری فنی

```
┌──────────────────┐
│   API Gateway     │ (RBAC + 2FA)
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Nitration/       ││ Runaway Early- ││ Color/NCO Soft-  │
│Hydrogenation/   ││ Warning Model  ││ Sensor +         │
│Phosgenation     ││ (Random Forest)││ Risk-Quality Link│
│Ingestion        ││                ││                  │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| مسیر پیشنهادی | توضیح |
| :--- | :--- |
| `services/nitration-safety-ingestion/` | اتصال DCS نیتراسیون/هیدروژناسیون با اولویت پیام بحرانی |
| `services/runaway-early-warning/` | مدل Random Forest/LSTM هشدار فرار گرمایی |
| `services/color-nco-soft-sensor/` | حسگر مجازی رنگ و NCO |
| `shared/` | بازاستفاده از محصولات ۱-۴ و الگوی ایمنی محصول خوزستان |

---

## ۳. کد تولید داده‌های سنتتیک

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(seconds=i*2) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# ۱. راکتور نیتراسیون - نرخ تولید گرما در برابر دفع گرما
heat_generation_rate_kw = 850 + 40 * np.sin(t * 0.2) + np.random.normal(0, 10, NUM_RECORDS)
heat_removal_rate_kw = 860 + 35 * np.sin(t * 0.2 - 0.1) + np.random.normal(0, 12, NUM_RECORDS)
heat_balance_deviation_kw = heat_generation_rate_kw - heat_removal_rate_kw
# تزریق چند رویداد شبیه‌سازی‌شده افزایش خطر فرار گرمایی
risk_idx = np.random.choice(NUM_RECORDS, size=12, replace=False)
heat_balance_deviation_kw[risk_idx] += np.random.uniform(30, 70, size=12)
reactor_temp_c = 55 + 0.05 * heat_balance_deviation_kw + np.random.normal(0, 1, NUM_RECORDS)

# ۲. واحد فسژناسیون
phosgene_amine_molar_ratio = 3.2 + 0.1 * np.sin(t * 0.1) + np.random.normal(0, 0.03, NUM_RECORDS)
phosgenation_temp_c = 130 + 4 * np.sin(t * 0.08) + np.random.normal(0, 0.8, NUM_RECORDS)

# ۳. کیفیت محصول نهایی
product_color_hazen = 25 + 3 * (phosgene_amine_molar_ratio - 3.2) * 10 + 0.5 * (phosgenation_temp_c - 130) + np.random.normal(0, 2, NUM_RECORDS)
product_color_hazen = np.clip(product_color_hazen, 10, 80)
nco_content_percent = 33.5 - 0.02 * (product_color_hazen - 25) + np.random.normal(0, 0.15, NUM_RECORDS)

# ۴. برچسب‌ها
thermal_runaway_risk = (heat_balance_deviation_kw > 25).astype(int)
off_spec_color_risk = (product_color_hazen > 40).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'heat_generation_rate_kw': np.round(heat_generation_rate_kw, 2),
    'heat_removal_rate_kw': np.round(heat_removal_rate_kw, 2),
    'heat_balance_deviation_kw': np.round(heat_balance_deviation_kw, 2),
    'reactor_temp_c': np.round(reactor_temp_c, 2),
    'phosgene_amine_molar_ratio': np.round(phosgene_amine_molar_ratio, 3),
    'phosgenation_temp_c': np.round(phosgenation_temp_c, 2),
    'product_color_hazen': np.round(product_color_hazen, 1),
    'nco_content_percent': np.round(nco_content_percent, 3),
    'thermal_runaway_risk': thermal_runaway_risk,
    'off_spec_color_risk': off_spec_color_risk,
})

df.to_csv("karoun_isocyanate_safety_quality_data_10k.csv", index=False)
print(f"✅ ذخیره شد. رکوردها: {len(df):,} - متغیرها: {len(df.columns)}")
print(df.describe())
```

---

## ۴. توجیه اقتصادی

| شاخص | وضعیت فعلی | با Khalij-KISQ | اثر مالی/ایمنی تقریبی |
| :--- | :--- | :--- | :--- |
| ایمنی واکنش نیتراسیون/هیدروژناسیون | نظارت دستی بر پارامترهای عملیاتی | هشدار پیش‌گیرانه از روند اختلاف گرمایی | کاهش ریسک حادثه فرار گرمایی/انفجار — بحرانی برای تنها تولیدکننده ایزوسیانات منطقه |
| کیفیت رنگ TDI/MDI | اندازه‌گیری آزمایشگاهی با تأخیر | پیش‌بینی بلادرنگ و اصلاح فوری فسژناسیون | کاهش ضایعات/فروش با تخفیف محصولات تیره‌رنگ زیر مشخصه |

**Payback:** با توجه به ریسک فاجعه‌بار فرار گرمایی و جایگاه انحصاری کارون در تولید ایزوسیانات منطقه، این محصول اولویت ایمنی و اقتصادی هم‌زمان دارد.

---

## ۵. نقشه تکامل پیشنهادی (Phase 1-5)

| فاز | قابلیت |
| :--- | :--- |
| ۱ | زیرساخت پایه + شبیه‌ساز داده |
| ۲ | مدل هشدار پیش‌گیرانه فرار گرمایی نیتراسیون/هیدروژناسیون (اولویت اول HSE) |
| ۳ | حسگر مجازی رنگ/NCO محصول فسژناسیون |
| ۴ | مدل یکپارچه ریسک-کیفیت |
| ۵ | داشبورد + پایلوت عملیاتی با نظارت تیم HSE |

---

## ۶. جمع‌بندی نوآوری‌های قابل ثبت اختراع

1. **هشدار پیش‌گیرانه فرار گرمایی اختصاصی زنجیره نیتراسیون-هیدروژناسیون ایزوسیانات**.
2. **حسگر مجازی بلادرنگ رنگ Hazen/APHA و NCO% محصول فسژناسیون**.
3. **مدل یکپارچه ریسک-کیفیت** که اثر انحراف ایمنی مرحله اول را روی کیفیت محصول نهایی پیوند می‌دهد.

---

## ۷. منابع

- [ویکی‌پدیا فارسی — پتروشیمی کارون](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%DA%A9%D8%A7%D8%B1%D9%88%D9%86)
- [سایت رسمی پتروشیمی کارون](https://krnpc.ir/)
- [AIChE — A Machine Learning Tool for Thermal Runaway Prediction of Chemical Reactors](https://proceedings.aiche.org/conferences/aiche-annual-meeting/2020/proceeding/paper/314b-machine-learning-tool-thermal-runaway-prediction-chemical-reactors)
- [Soft-sensor development for product quality estimation in industrial MDI production — ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2666821125000481)
- [US10189945 — Method for producing light-coloured TDI-polyisocyanates](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/10189945)
- [US8748655 — Process for preparing light-coloured isocyanates of the diphenylmethane series](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/8748655)
- [Runaway Reaction Hazards in Processing Organic Nitro Compounds — ACS](https://pubs.acs.org/doi/abs/10.1021/op970035s)
