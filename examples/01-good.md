# Handoff — session 003 to 004

> Synthetic example. All names, identifiers and paths are fictional.

## 事实

- The indexing job `idx-build` finished at 14:02 with 12,480 entries. —— 证据：`logs/idx-build-1402.log:88` 【有据】
- The retrieval endpoint returns p95 = 210 ms at k=5. —— 证据：`bench/run-0712.json` 【有据】
- Segment-level vectors were not rebuilt after the schema change. —— 证据：`stage/seg-meta.json` mtime 【有据】

## 证据锚点

- 文件：`src/retrieve.js` sha256 前 12 位 = `a1b2c3d4e5f6`，字节数 25,104
- 命令：`node bench/run.js --k 5` ⇒ `p95=210ms`
- 留痕：`CHG-0712` / 快照 `snapshots/0712-1400.json`

## 未决

- Whether the segment layer must be rebuilt before the next release —— 未决原因：schema 变更影响面未评估 —— 需要：一次只读的索引一致性检查
- Whether p95 210 ms holds at k=20 —— 未决原因：未压测 —— 需要：`bench/run.js --k 20` 的结果

## 红线

- 索引目录在本轮只读。 —— 依据：`AGENTS.md §2`
- 未经核实的推断不得写入交接件。 —— 依据：`ledger-983`

## 本件自指

- 出件线程 `T-003` / 接续线程 `T-004` / 出件时刻 `2026-07-12 14:05 +08:00`
- 本件的 sha256 在写入前不可知，故不自嵌。
