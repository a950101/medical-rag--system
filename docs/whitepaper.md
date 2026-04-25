# 白皮書（Whitepaper）

## 🧠 問題背景

醫療知識具有高度專業性與複雜性，
傳統大型語言模型（LLM）容易產生錯誤資訊（hallucination），
在醫療場景中風險極高。

---

## 📌 知識轉換挑戰（Representation Problem）

醫療文本具有以下特性：

- 專有名詞多（疾病、藥物）
- 同義詞複雜（例：心肌梗塞 = 心臟病發作）
- 症狀與疾病非一對一對應

👉 因此單純向量化容易失真。

---

## ⚠️ Hallucination 問題

LLM 可能產生：
- 不存在的診斷
- 錯誤治療建議
- 未經證實的醫療資訊

---

## 🛠️ 解決方案

### 1️⃣ Retrieval-Augmented Generation（RAG）

透過檢索外部醫療資料，
限制模型只能根據資料回答。

---

### 2️⃣ Reranking 機制

提高檢索結果品質：
- 先 Retrieval
- 再 Cross Encoder 排序

---

### 3️⃣ Prompt 約束

強制模型：

> 僅能根據提供資料回答，若無資料則說「無法判斷」

---

## ❄️ Cold Start 問題

新疾病或新醫學名詞可能尚未出現在資料庫中。

解法：
- 定期更新資料來源
- 使用多語 embedding 模型
- 建立同義詞對照表

---

## 🚀 系統創新點

- Hybrid Search（BM25 + Vector）
- Reranking 提升準確度
- 可追溯來源（Explainable AI）
- 降低 hallucination

---

## 🎯 結論

本系統透過 RAG 架構，
有效提升醫療問答的準確性與可靠性，
適合作為醫療輔助決策工具的基礎系統。
