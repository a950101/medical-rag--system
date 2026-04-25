# 系統架構（Architecture）

## 🔁 系統整體流程

資料來源 → ETL → Chunking → Embedding → Vector Database → Retrieval → Reranking → LLM → 回答

---

## 📥 Data Ingestion（ETL）

資料來源：
- 醫療文獻（PubMed）
- 診療指引（WHO / CDC）

處理流程：
1. PDF / HTML 轉文字
2. 清洗雜訊
3. 結構化（標題、段落）

---

## ✂️ Chunking Strategy

採用 Hybrid Chunking：
- 固定長度（512 tokens）
- 語義切分（依段落）

原因：
醫療文本語意強，需保留上下文。

---

## 🧠 Embedding Model

使用：
- BGE-M3

理由：
- 支援多語
- 對專業文本效果佳

---

## 🗄️ Vector Database

使用：
- FAISS

結構：
- Dense Vector Index
- Metadata filtering（疾病分類）

---

## 🔍 Retrieval Strategy

採用 Hybrid Search：
- BM25（關鍵字）
- 向量檢索（語意）

---

## 🔁 Reranking

使用 Cross Encoder 進行重排序。

位置：
Retrieval → Reranking → LLM

---

## 🤖 LLM 回答生成

根據檢索內容生成答案，
並限制只能使用檢索到的資訊。

---

## ⚠️ 關鍵設計

- 非結構化 → 向量化：Embedding 階段
- 提升準確度：Reranking
- 降低 hallucination：RAG Grounding
