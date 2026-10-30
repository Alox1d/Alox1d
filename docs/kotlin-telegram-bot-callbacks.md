# Handling game callbacks in a Kotlin Telegram client

**Status:** [Upstream PR #374](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/374) is open as of October 30, 2026. It addresses [issue #329](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/issues/329).

## The contract and the failure

Telegram's [`CallbackQuery` contract](https://core.telegram.org/bots/api#callbackquery) distinguishes ordinary callbacks carrying `data` from game callbacks carrying `game_short_name`. Exactly one of these fields is present.

The client previously declared `data` as a non-null `String` and did not model the game name. Its [dispatch check](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/blob/392ddb772a6e9394cac9f103e49475eff2513c38/telegram/src/main/kotlin/com/github/kotlintelegrambot/dispatcher/handlers/CallbackQueryHandler.kt) rejected any callback whose data was absent, before checking whether the handler had a data filter. A valid game callback therefore could not reach even an unfiltered handler.

## The change and its invariant

The [updated model](https://github.com/Alox1d/kotlin-telegram-bot/blob/ee0ef742cbe2d187819bd34ea0708ce0f11465a1/telegram/src/main/kotlin/com/github/kotlintelegrambot/entities/CallbackQuery.kt) makes `data` nullable and adds nullable `gameShortName`, mapped to `game_short_name` with Gson's `SerializedName`.

The dispatch check separates the existence of a callback from the existence of callback data:

```kotlin
val query = update.callbackQuery ?: return false
return when {
    callbackData == null -> true
    else -> query.data?.contains(callbackData, ignoreCase = true) == true
}
```

An unfiltered handler accepts both callback forms. A handler with a data filter still requires matching data; a game name does not become an accidental substitute for that data. Updates without a callback remain excluded. The dispatcher sample also handles nullable data explicitly.

## Compatibility consequences

The model change is visible to callers. Kotlin code that treated `data` as always present must now handle its absence. Adding a property to the data class changes its generated constructor and `copy` signatures, so the patch changes the binary API as well. The [PR diff](https://github.com/kotlin-telegram-bot/kotlin-telegram-bot/pull/374/files) includes the updated public API dump.

## Regression coverage

The added cases exercise both deserialization and dispatch:

| Case | Expected result |
| --- | --- |
| Game JSON without `data` | Null data and the parsed game name |
| Ordinary callback JSON without `game_short_name` | Parsed data and a null game name |
| Game callback, unfiltered handler | Accepted |
| Game callback, data-filtered handler | Rejected |

## Verification

The full build initially caught formatting violations in two test files. After those corrections, the revised patch passed the full build on October 30, 2026, including ktlint, API checks and all sample builds. Its test reports contain **614 tests across 178 suites**, with no failures, errors or skipped tests.

Verified revision: [`ee0ef742`](https://github.com/Alox1d/kotlin-telegram-bot/commit/ee0ef742cbe2d187819bd34ea0708ce0f11465a1). All 513 tracked file blobs in the published tree match the source used for this build.

The cloud run used JDK 17 and the official Gradle 8.3 distribution. The command below shows the executed options with the machine-specific Gradle and cache paths replaced by variables:

```sh
bash "$GRADLE_83/bin/gradle" \
  --gradle-user-home "$GRADLE_CACHE" \
  --no-daemon --max-workers=2 --console=plain \
  -Pkotlin.compiler.execution.strategy=in-process \
  --stacktrace build
```

The run retained existing compiler and deprecation warnings. These are local cloud build results; upstream GitHub Actions and maintainer review are separate.

