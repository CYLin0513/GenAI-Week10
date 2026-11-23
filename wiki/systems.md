# 算得動：FlashAttention 與多 GPU 分工

**FlashAttention：** 分塊運算搭配 Online Softmax，減少將完整中間 Attention 矩陣寫入高頻寬記憶體（HBM）的成本，仍執行精確 Attention；不等於把計算漸近成本改為線性，也不是直接消除 Decode 的全部 KV Cache。[S05](sources.md)

**Context Parallelism：** 將長序列資料切分到多張 GPU，透過通訊與合併完成處理。MLSys 2025 有大規模多 GPU 系統研究；可行的分散式實驗不表示一般單卡能執行同樣工作量。[S01](sources.md)

**注意：** 記憶體容量、HBM IO、跨卡通訊、Prefill 延遲與 Decode 吞吐應分開衡量。