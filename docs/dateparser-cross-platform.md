# Building and verifying DateParser Kotlin across platforms

[Repository](https://github.com/Alox1d/dateparser-kotlin) · [Maven Central](https://central.sonatype.com/artifact/io.github.alox1d/dateparser-kotlin) · [Documentation](https://alox1d.github.io/dateparser-kotlin/en/)

## The problem

Natural-language date input is convenient for reminders, but a wrong interpretation can silently schedule something at the wrong time. Parsing is also different from scheduling: a match needs an explicit reference time and timezone, and an app must let the person review the result before saving.

DateParser Kotlin is my maintained Kotlin Multiplatform adaptation of Alexey Orazov's date-parser. The library handles English and Russian expressions offline on JVM, Android and iOS.

## Engineering decisions

- Keep parsing in shared Kotlin code; do not require Android Context or network access.
- Accept an explicit reference instant, timezone and date-order setting so behavior does not depend on device defaults.
- Return structured matches, rather than silently creating reminders or claiming complete natural-language coverage.
- Treat invalid and ambiguous input conservatively. [PR #16](https://github.com/Alox1d/dateparser-kotlin/pull/16) tightened short slash-year parsing; [PR #17](https://github.com/Alox1d/dateparser-kotlin/pull/17) rejects malformed explicit clock expressions after date cues.
- Separate the parser from UI and scheduler ownership. The [Android demo](https://alox1d.github.io/dateparser-kotlin/en/kmp-reminder-demo/) includes an editable confirmation step.

## Independent verification

The project's [CI workflow](https://github.com/Alox1d/dateparser-kotlin/actions/workflows/ci.yml) tests JVM and Android code, produces local Maven publications, checks consumers in separate builds and runs iOS simulator tests on macOS runners.

For the [November 2, 2026 main-branch run](https://github.com/Alox1d/dateparser-kotlin/actions/runs/41423133298), JVM and Android checks passed immediately. The first macOS job was cancelled before execution because GitHub could not allocate a hosted runner; rerunning failed jobs produced a complete green result, including the Apple job. This distinguishes infrastructure scheduling from a code/test failure.

The published [0.1.3 release](https://github.com/Alox1d/dateparser-kotlin/releases/tag/v0.1.3) and [external sample PR](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/375) are separate evidence: the first is a released library; the second is a proposed, **not yet merged**, reminder-bot integration.

## Limits and lessons

A parser can return a plausible date without understanding every instruction around it. Real applications should preserve the original text, display the resolved timezone and calendar time, and require confirmation for consequential actions. A successful parser test does not establish successful reminder delivery or alarm behavior on a physical device.

The cross-platform test matrix also matters operationally: checking independent consumers catches publishing/configuration errors that unit tests inside the library itself cannot find.
