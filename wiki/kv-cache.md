# KV Cache：為什麼 1M Token 會造成負擔？

## Prefill 與 Decode
Prefill 對輸入提示進行處理；Decode 逐步生成新 Token。KV Cache 保存歷史 Token 在各層的 Key 與 Value，避免解碼時重算相同歷史表示，代價是需要儲存記憶體。

## 容量公式
標準密集 Transformer 的近似 KV Cache 容量為：

`M = 2 × N × L × H_KV × d_h × b`

N：Token 數，L：層數，H_KV：KV Head 數，d_h：Head 維度，b：每個元素的位元組數。

假設 N=1,000,000、L=32、d_h=128、FP16=2 bytes：1 個 KV Head 約 **16.384 GB**，8 個 KV Heads 約 **131.072 GB**（只計算 KV Cache，不含權重或其他開銷）。

密集因果 Attention 的 Prefill 有約 N(N+1)/2 次 Q–K 配對；這與 KV Cache 對 N 線性成長，是不同的瓶頸。FlashAttention 減少 HBM 中間暫存，不表示長期 KV Cache 被消除。

來源：[S01、S02、S05](sources.md)；有效理解另見 [評測](evaluation.md)。