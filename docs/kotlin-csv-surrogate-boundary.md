# UTF-8 corruption at a CSV buffer boundary

[Pull request: kotlin-csv #189](https://github.com/jsoizo/kotlin-csv/pull/189) · Status: **open for maintainer review**, November 2, 2026.

## Failure mode

The CSV writer flushes after a buffer of 8,192 UTF-16 code units. Supplementary Unicode characters are represented as a high/low surrogate pair. If the high surrogate lands in the final slot, encoding each buffer separately loses the pair and can corrupt the output.

A reproducing input is a field whose last units are `"a".repeat(8191) + "\uD83D\uDE00"`: the emoji straddles the flush boundary even though the input itself is valid.

## Fix and test

The [focused patch](https://github.com/jsoizo/kotlin-csv/pull/189/files) keeps a trailing high surrogate when flushing and joins it to the next chunk. It retains a bounded buffer and preserves the rest of the writer's behavior.

Regressions cover both `write` and `writeNullable` through a real `kotlinx.io.Buffer`. These tests first failed on the unchanged implementation. After the change, `./gradlew jvmTest` completed with **258 passing tests**, no failures or skips, in the author's local verification environment.

## Boundaries

This is a proposed upstream fix, not a merged contribution or a release. JVM tests were run; JS, Wasm and Kotlin/Native target tests were **not** run locally. The upstream maintainer must review the change and may request additional tests.

The broader lesson is that UTF-8 encoders operating on UTF-16 chunks must not split a surrogate pair across independent encoding calls. For production libraries, a regression at an exact boundary is more useful than a generic Unicode sample that never crosses the buffer limit.
