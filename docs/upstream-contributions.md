# Upstream contributions

This is a selected record of changes submitted to projects outside my own repositories, checked on **November 3, 2026**. The linked pull requests are authoritative for current status and maintainer feedback. An **open** PR is proposed work, not an accepted or shipped change; a **draft** is not ready for review.

## Merged

| Project | Contribution | Outcome |
| --- | --- | --- |
| [awesome-kotlin #1204](https://github.com/Heapy/awesome-kotlin/pull/1204) | Added DateParser Kotlin to the Kotlin library catalogue. | **Merged** October 30, 2026 (catalogue entry, not a code change) |
| [fast-compose #2](https://github.com/fast-compose/fast-compose/pull/2) | Preserved mixed named and positional argument order in the Kotlin/Compose interpreter. | **Merged** November 3, 2026 (19 focused regressions) |

## Proposed changes

These PRs remain **open**. Their tests and review outcomes are documented in each linked PR; a mergeable branch or passing local tests does not imply upstream acceptance.

| Project | Proposed change | Status |
| --- | --- | --- |
| [Koin #2476](https://github.com/InsertKoinIO/koin/pull/2476) | Handle null assignment in `ParametersHolder.set`. | Open |
| [Kotlin Telegram Bot #373](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/373) | Deserialize invite-link responses correctly. | Open |
| [Kotlin Telegram Bot #374](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/374) | Support game callbacks without callback data ([case study](kotlin-telegram-bot-callbacks.md)). | Open |
| [Kotlin Telegram Bot #375](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/375) | Optional reminder sample using published DateParser Kotlin 0.1.3, without changing the core library dependencies. | Open |
| [ktlint-gradle #1129](https://github.com/JLLeitschuh/ktlint-gradle/pull/1129) | Invalidate stale lint results after source deletion. | Open |
| [nemo-editor #38](https://github.com/Ma7moud3ly/nemo-editor/pull/38) | Preserve Kotlin identifiers starting with keywords. | Open |
| [ktoml #399](https://github.com/orchestr7/ktoml/pull/399) | Reject malformed TOML integer literals. | Open |
| [Hoplite #609](https://github.com/sksamuel/hoplite/pull/609) | Track consumed Hikari configuration entries correctly. | Open |
| [ksvg #19](https://github.com/nwillc/ksvg/pull/19) | Emit the XML declaration only for standalone SVG documents. | Open |
| [cron-descriptor #118](https://github.com/Salamek/cron-descriptor/pull/118) | Preserve Monday-start weekday steps under zero-based numbering. | Open |
| [kotlin-csv #189](https://github.com/jsoizo/kotlin-csv/pull/189) | Keep surrogate pairs intact across UTF-8 buffer flushes ([case study](kotlin-csv-surrogate-boundary.md)). | Open |
| [cronsim #8](https://github.com/cuu508/cronsim/pull/8) | Fix reverse iteration from fractional starting times. | Open |
| [biweekly #136](https://github.com/mangstadt/biweekly/pull/136) | Use a 24-hour clock for timezone observance boundaries. | Open |

## Draft (not completed)

[Telegram Desktop #31523](https://github.com/telegramdesktop/tdesktop/pull/31523) proposes Markdown shortcuts inside article toggles, but remains **draft**. Full application build and UI verification have not been completed. It is listed for status tracking, not as a finished contribution.

## Verification notes

Some examples of reported local checks: [kotlin-csv #189](https://github.com/jsoizo/kotlin-csv/pull/189) passed 258 JVM tests; JS, Wasm and Native tests were not run locally. [cronsim #8](https://github.com/cuu508/cronsim/pull/8) passed 113 tests and strict mypy. [biweekly #136](https://github.com/mangstadt/biweekly/pull/136) passed 1,158 tests with one skip. The optional [Telegram reminder sample #375](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/375) reports 43 new tests and a full project build. These checks belong to the respective proposed revisions, and none establishes a merge or production release.

For shipped library maintenance, see [DateParser Kotlin's CI and publishing case study](dateparser-cross-platform.md).
