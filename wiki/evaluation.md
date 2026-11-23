# 名義 1M Context，不等於有效理解 1M

**Lost in the Middle：** 將線索放在序列前、中、後，顯示模型可能較不擅長利用中間位置資訊。[S04](sources.md)

**RULER：** 用多種長文本合成任務（例如檢索、聚合、追蹤），避免僅以單一 Needle-in-a-Haystack 測試判斷理解品質。[S03](sources.md)

**∞Bench：** 含多種長文任務；解讀分數時需注意實際輸入是否截斷、模型長度與測試設定。[S06](sources.md)

評估至少區分：
1. **Advertised Context**：模型配置可接受多少 Token；
2. **Resource Cost**：顯存、TTFT、吞吐量與 GPU 資源；
3. **Effective Context**：不同位置、不同任務和長度下，模型能否可靠利用資訊。