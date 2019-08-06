---
layout: classic-docs
title: کال‌بک
lang: fa
permalink: /faq/callbacks/index.html
toc: true # table of contents
---

## اگر بخواهم نصب‌ها یا رخدادها را به صورت سیستماتیک دریافت کنم چه‌کار کنم؟

متریکس به شما این امکان را می‌دهد تا به صورت خودکار توانایی دریافت هر رخداد مربوط به نصب و کلیک را داشته باشید. برای این کار لازم است مشابه تصویر زیر ابتدا از صفحه کاربری خودتان *کال‌بک* تعریف کنید. 

<img src="{{ '/images/set-callback.jpg' | relative_url }}" alt="callback window"/>

## چطور می‌توانم برای نصب‌ها و رخدادها کال‌بک تعریف کنم؟

در صفحه **سازمان‌ها** در داشبورد پس از کلیک روی علامت سه نقطه اپلیکیشن مورد نظر، صفحه **تنظیمات** یا **setting** به قسمت **callbacks** بروید و. در این قسمت می‌توانید برای هر نصب یا هر رخدادی که تعریف می‌کنید یا event، یوآرال کال‌بک خود را به همراه پارامترهای مورد نیاز ثبت کنید.

## چه پارامترهایی را می‌توانم برای تعریف URL کال‌بک اضافه کنم؟

این پارامترها در جدول‌ زیر قابل مشاهده هستند. هر کدام از این پارامترها را به دلخواه خودتان می‌توانید انتخاب کنید و آنها را به صورت ماکرو تو urlاتون اضافه کنید تا متریکس بتواند برای شما تو کال‌بک به سرور شما ارسال کند :
- android_id شناسه دستگاه اندروید
- gps_adid شناسه تبلیغاتی گوگل پلی سرویس
- device_name مدل دستگاه
- device_manufacturer برند دستگاه
- installed_at زمان نصب
- ip_address آی‌پی کاربر
- tracker_code شناسه ترکر
- network_name نام شبکه تبلیغاتی
- campaign_name نام کمپین
- adgroup_name نام گروه تبلیغاتی
- creative_name نام خلاقه
 

ضمنا اگر پارامتری customای دارید که زمان کلیک توسط شما پر می‌شود، و نیاز دارید تا زمان نصب بهتون برگردد به صورت placeholder تو لینک کال‌بک خودتون می‌توانید وارد کنید.
یک نمونه از کال‌بک نصب می‌تواند به صورت زیر  باشد:

```
http://callbacks.myserver.com/path?clickId={clickId}&tracker_name={tracker_name}&ip_address={ip_address}
```

برای کال بک مربوط به ایونت‌ها، زمان رخداد{created_at} و پارامتر اکشن تعریف شده توسط شما {actionName}  نیز قابلیت ارسال دارد و همراه موارد بالا  و پارامترهای ست شده توسط شما درون sdk، قابلیت ارسال به سرور شما را خواهد داشت.
