---
tags:
  - dacn/DACN-261-Markov/AnhDuy
---

# make\_tfidf\_similarity(catalog)
Similarity trực tuyến offline: **cosine** trên TF-IDF của toàn bộ text ontology.
## similarity(text\_a, text\_b)
Tính cosine similarity của 2 text.
# make\_ollama\_similarity()
Similarity dense qua Ollama (cần Ollama đang chạy)
# build\_matrix(backend="local", catalog_path="data/catalog.json")
- Gọi `make_tfidf_similarity(catalog)` và `make_ollama_similarity()`
- Tính $\rho(A|B)$ cho các cặp kiến trúc.
# main