# 百萬 Token 長上下文 LLM Wiki

本 Wiki 以技術問題而非公司發展史來整理長上下文 LLM 的研究，區分**存得下、算得動、用得好**三個目標。內容對應一份 17 頁的 HTML 教學簡報。

## 知識地圖

- [KV Cache 與記憶體估算](kv-cache.md)
- [MQA、GQA 與 MLA：壓縮每個 Token 的 KV](kv-sharing.md)
- [KV 壓縮與 Sparse Attention：少留、少讀歷史](sparse-compression.md)
- [Mamba、Linear Attention 與 Hybrid](linear-hybrid.md)
- [FlashAttention 與 Context Parallelism](systems.md)
- [長上下文的實際理解評測](evaluation.md)
- [公開模型技術對照](models.md)
- [原始論文與官方技術報告：16 份來源](sources.md)
- [17 頁 HTML 與 Wiki 的逐頁對照](slide-map.md)

## Ingest 與查核原則

原始 Codex v1 留有 S01–S06 六份閱讀與摘錄紀錄；S07–S16 根據公開論文摘要、出版頁或官方技術報告資訊整理，**沒有宣稱全文精讀**。所有知識頁面以來源 ID 對應原始資料，避免將不同廠商的路線誤認成單一路線。

**三個不同問題：** KV Cache 的容量、Attention 的計算與 IO 開銷、模型實際使用超長上下文的能力。減少其中一項成本不必然改善另外兩項。