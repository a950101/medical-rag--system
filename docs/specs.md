# 系統規格（Specs）

## 📊 資料規格（Chunking Strategy）

- Chunk 大小：512 tokens
- Overlap：50 tokens
- 切分方式：
  - 固定長度切分
  - 語義切分（依段落）

---

## ⚡ 系統性能指標

| 指標 | 目標 |
|------|------|
| Latency | < 2 秒 |
| Top-K 準確度 | > 85% |
| Recall | > 90% |

---

## 🔍 檢索策略

- Hybrid Search：
  - BM25（關鍵字檢索）
  - Dense Retrieval（向量檢索）

- Top-K：取前 5 筆結果

- Reranking：
  使用 Cross Encoder 進行排序

---

## 📏 評估機制

使用以下工具：

### 1️⃣ RAGAS
評估：
- Faithfulness（忠實度）
- Relevance（相關性）
- Answer Completeness（完整性）

---

### 2️⃣ TruLens
用於分析：
- 模型回應品質
- 檢索與生成關係

---

## 🎯 系統目標

建立一個：
- 高準確度
- 可解釋
- 低 hallucination

的醫療問答系統。
