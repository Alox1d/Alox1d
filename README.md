<img src="assets/banner-en.svg" width="100%" alt="A/B Apps - Alexander Baranov. Android. Attention to detail." />

<p align="center">
  <a href="https://kotlinlang.org/docs/home.html"><img src="assets/badges/kotlin.svg" alt="Kotlin" height="28" /></a>
  <a href="https://developer.android.com/"><img src="assets/badges/android.svg" alt="Android" height="28" /></a>
  <a href="https://developer.android.com/compose"><img src="assets/badges/compose.svg" alt="Jetpack Compose" height="28" /></a>
  <a href="https://www.jetbrains.com/kotlin-multiplatform/"><img src="assets/badges/kmp.svg" alt="Kotlin Multiplatform" height="28" /></a>
</p>

Android developer working with **Kotlin**, **Jetpack Compose**, **Kotlin Multiplatform** and the details that make an app feel right.

- **Now:** Android fintech at **Wildberries** - installment payments, financial calculations and reliable UI state.
- **Previously:** **VK ID** - authentication flows and Android integration.
- **Open source:** [**DateParser Kotlin**](https://github.com/Alox1d/dateparser-kotlin), an offline date/time parser published on Maven Central.
- **On my workbench:** **Chatevent**, a commercial planner where tasks live in chats.

`Java` · `Coroutines / Flow` · `Room`

<p align="center">
  <a href="https://t.me/Alox1d"><b>Telegram ↗</b></a>
  &nbsp; · &nbsp;
  <a href="https://habr.com/ru/users/alox1d/"><b>Habr ↗</b></a>
  &nbsp; · &nbsp;
  <a href="https://habr.com/ru/companies/vk/articles/780194/"><b>My VK ID article ↗</b></a>
</p>

### [DateParser Kotlin ↗](https://github.com/Alox1d/dateparser-kotlin)

*Offline natural-language date and time parsing for Kotlin Multiplatform.*

English and Russian · Android, JVM and iOS.

[![Maven Central](https://img.shields.io/maven-central/v/io.github.alox1d/dateparser-kotlin?strategy=releaseProperty&style=for-the-badge&label=Maven%20Central&color=7928CA)](https://central.sonatype.com/artifact/io.github.alox1d/dateparser-kotlin)
[![CI main](https://img.shields.io/github/actions/workflow/status/Alox1d/dateparser-kotlin/ci.yml?branch=main&event=push&style=for-the-badge&label=CI%20main&color=7928CA)](https://github.com/Alox1d/dateparser-kotlin/actions/workflows/ci.yml?query=branch%3Amain%20event%3Apush)
[![MIT license](https://img.shields.io/github/license/Alox1d/dateparser-kotlin?style=for-the-badge&label=License&color=7928CA)](https://github.com/Alox1d/dateparser-kotlin/blob/main/LICENSE)

[Latest release ↗](https://github.com/Alox1d/dateparser-kotlin/releases/latest) · [Documentation ↗](https://alox1d.github.io/dateparser-kotlin/en/) · [KMP demo ↗](https://alox1d.github.io/dateparser-kotlin/en/kmp-reminder-demo/) · [klibs.io ↗](https://klibs.io/project/Alox1d/dateparser-kotlin)

**`Buy milk tomorrow at 7pm` → `Buy milk` + tomorrow at 19:00.**

<p align="center">
  <a href="https://github.com/Alox1d/dateparser-kotlin"><img src="assets/dateparser-reminder-preview.png" width="220" alt="DateParser Kotlin Android demo: review the extracted reminder title, date and time." /></a>
  &nbsp;
  <a href="https://github.com/Alox1d/dateparser-kotlin"><img src="assets/dateparser-reminder-saved.png" width="220" alt="DateParser Kotlin Android demo: edited and confirmed reminder in the session-only list." /></a>
</p>

Use it in `commonMain` with a reference instant, an explicit timezone and US/European date order. The runnable KMP consumer and Android Compose demo show how to review and edit the result before saving. No API keys or network calls.

### Apps

#### Chatevent

A chat-shaped planner: tasks, notes, folders and a calendar in one place.

**Commercial product · In development**  
Private source · Kotlin · Compose · Room · Glance

<p align="center"><a href="assets/chatevent.webp"><img src="assets/chatevent.webp" width="180" alt="Chatevent Android screenshot: chats, folders and upcoming tasks, with demonstration data." /></a></p>

#### WordNote

Notes, tasks and reminders with English voice input, OCR and date/time extraction.

**Historical graduation project · Huawei Cup 2020 APP student winner**  
Ivanovo State Power Engineering University · Kotlin / Java · SQLite · Huawei HMS

<p align="center"><a href="assets/wordnote.webp"><img src="assets/wordnote.webp" width="225" alt="WordNote Android screenshot: task lists and reminders." /></a></p>

[Source code ↗](https://github.com/Alox1d/wordnote) · [AppGallery ↗](https://appgallery.huawei.com/app/C103198375) · [Video demo ↗](https://www.youtube.com/watch?v=rDJz7HMdjpE)

### Writing & milestones

- **Huawei Cup 2020:** winner of the **APP student category**. [Official Huawei results, March 26, 2021 ↗](https://www.huawei.ru/news/obyavleny-luchshie-razrabotchiki-mobilnykh-prilozheniy-v-ramkakh-sorevnovaniya-huawei-cup-2020/)
- **SmartFlow: a new authentication flow for VK ID** - my article on Android authentication, published in the VK engineering blog on **February 22, 2024**. [Read on Habr (RU) ↗](https://habr.com/ru/companies/vk/articles/780194/)

### Open-source tools

#### [CSPSigner ↗](https://github.com/Alox1d/act-signer)

A Windows PowerShell desktop tool for batch signing files with CryptoPro CSP. Creates detached CAdES-BES signatures without changing the source files, verifies signatures, and avoids signing the same file twice with the selected certificate.

[Download latest release ↗](https://github.com/Alox1d/act-signer/releases/latest) · [Documentation (EN) ↗](https://github.com/Alox1d/act-signer/blob/main/README.en.md)

#### [PCBCalc ↗](https://github.com/Alox1d/PCBCalc)

<p align="center"><a href="https://github.com/Alox1d/PCBCalc"><img src="assets/pcbcalc.png" width="400" alt="PCBCalc - circuits meet mechanics" /></a></p>

My 2018 graduation project at Ivanovo Energy College: educational PCB vibration and reliability calculations, with Word export.

Java · 7 calculation/export tests · Original report templates

### Public Android samples

Small Android samples and experiments, from custom drawing to voice recording.

- [**vkvoicenotes**](https://github.com/Alox1d/vkvoicenotes) - Voice recording and playback with Android Views, Room, Dagger, RxJava and ExoPlayer.
- [**CustomViewTest**](https://github.com/Alox1d/CustomViewTest) - Custom Android Views: Canvas drawing, bitmap shaders, XML attributes and saved state.
- [**AndroidCore**](https://github.com/Alox1d/AndroidCore) - Java/Kotlin fundamentals, concurrency, collections, Coroutines/Flow and Handler/Looper experiments.

### Course-based learning

Exercises I followed and adapted while learning Android.

- [VKNewsApp](https://github.com/Alox1d/VKNewsApp) - a learning VK news client with Compose, MVVM, Flow, Dagger, Retrofit and pagination.
- [ComposeAnimations](https://github.com/Alox1d/ComposeAnimations) - Compose animation exercises: content, size, shape, color, alpha and rotation.
- [MVI-Weather-App](https://github.com/Alox1d/MVI-Weather-App) - an unfinished exploration of MVIKotlin, Decompose, Room and Retrofit.

