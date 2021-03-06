---
layout: classic-docs
title: راه اندازی تپسل در یونیتی (Android)
lang: fa
permalink: /tapsell-sdk/unity/initialize-android/index.html
toc: true # table of contents
---


## دریافت SDK تپسل
ابتدا فایل `unitypackage` مربوط به SDK تپسل را از آدرس زیر دانلود کرده و مطابق روش گفته شده در مراحل بعد در پروژه خود import نمایید.
[دریافت فایل](https://github.com/tapsellorg/TapsellSDK-UnitySample/releases/download/v4.3.0.1/Tapsell-Unity-4.3.0.1.unitypackage)


## تنظیمات اولیه Sdk
برای اضافه کردن کتابخانه‌های مورد نیاز ۲ روش وجود دارد از هرکدام که مایل هستید استفاده کنید.


### استفاده از Gradle

هنگام import یونیتی‌پکیج تپسل تیک قسمت `playServicesResolver` و `TapsellPlusDependencies.xml` را بردارید.

خط زیر را در بخش `dependencies` فایل `mainTemplate.gradle` در مسیر `Assets/Plugins/Android` اضافه کنید. توجه داشته باشید که ۲ قسمت `dependencies` وجود دارد، این تغییرات باید در قسمت دوم انجام شود.

```gradle
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    ...
    implementation 'ir.tapsell.sdk:tapsell-sdk-unity:4.3.8'
    ...
**DEPS**}
```

در نسخه‌های قدیمی یونیتی ممکن هست `implementation` شناخته نشود در این صورت از `compile` استفاده کنید.  
  
هر یک از خطوط زیر که در بخش `allprojects -> repositories` فایل `mainTemplate.gradle` وجود ندارد اضافه کنید.

```gradle
allprojects {
    repositories {
        google()
        jcenter()

        maven {
            url 'https://dl.bintray.com/tapsellorg/maven'
        }
    }
}
```

### استفاده از Resolver
هنگام import کردن unityPackage تپسل تیک تمامی قسمت‌ها را بزارید.
در صورتی که تنظیمات Resolver بر روی حالت `auto-resolution` میباشد، لایبراری‌های تپسل به صورت خودکار اضافه میشود. در غیر اینصورت به صورت دستی Resolve را انجام دهید.
فعال یا غیر فعال کردن `auto-resolution` از مسیر زیر انجام میشود.

```console
Assets > Play Services Resolver > Android Resolver > Settings
```

برای Resolve دستی نیز از این مسیر اقدام نمایید.

```console
Assets > Play Services Resolver > Android Resolver > Resolve
Assets > Play Services Resolver > Android Resolver > Force Resolve
```

## مقداردهی اولیه
ابتدا برای دسترسی به کدهای تپسل از تکه کد زیر استفاده کنید.

```c#
using TapsellSDK;
```

سپس تابع زیر را در یکی از اسکریپت‌های برنامه‌ی خود که در ابتدای برنامه اجرا می‌شود فراخوانی کنید.

```c#
Tapsell.Initialize(TAPSELL_KEY);
```

`TAPSELL_KEY` کلید تپسل هست و برای هر اپلیکیشن که میسازید در [پنل تپسل](https://dashboard.tapsell.ir/) ساخته میشود، میتوانید از پنل کپی کنید.

اکنون میتوانید با توجه به نیاز خود و توضیحات به هر نوع تبلیغ، تبلیغ مورد نظر را نمایش دهید.
