# 改變記憶方式：Linear / State Space / Hybrid

傳統 Softmax Attention 讓 Query 對歷史位置配對。Mamba 等選擇性狀態空間模型改為更新內部 State，成本形態不同於保存完整歷史 KV；固定狀態不保證能精確記住每個細節。[S10](sources.md)

公開研究提出不同混合路線：

- **Qwen3-Next**：Gated DeltaNet + Gated Attention。[S11](sources.md)
- **NVIDIA Nemotron 3**：Hybrid Mamba-Transformer。[S13](sources.md)
- **Kimi Linear**：Kimi Delta Attention + MLA。[S14](sources.md)
- **MiniMax-Text-01**：Lightning Attention + Softmax Attention。[S15](sources.md)

混合架構希望在效率與精確 Attention 能力間折衷，但不能跨不同硬體與評測把效能數字直接排名。