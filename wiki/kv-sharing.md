# 每個 Token 變窄：MQA、GQA 與 MLA

**MHA**：每個 Query Head 有自己的 KV Heads。**MQA**：多個 Query Heads 共用單一 KV Head。**GQA**：多個 Query Heads 分組共用少量 KV Heads。其他條件相同時，KV 容量與 KV Heads 數量成正比。[S07](sources.md)

**MLA（Multi-head Latent Attention）**：透過低秩表示壓縮 Key/Value 的潛在表徵，降低儲存負擔；DeepSeek-V2 與 Kimi K2 等公開技術資料描述其採用情形。[S08、S16](sources.md)

用表格想像歷史 KV：每列是一個歷史位置，每欄是該位置保存的表示。MQA/GQA 減少重複的 KV Heads；MLA 透過壓縮讓每個位置的有效儲存表示變窄。這只是教學類比，不等於實際 MLA 張量布局。

**限制**：KV 儲存降低不代表 Full Attention 預填充的二次配對消失。這些是不同架構選擇，不是所有模型都依序套用。