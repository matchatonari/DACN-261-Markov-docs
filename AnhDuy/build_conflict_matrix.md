---
tags:
  - dacn/DACN-261-Markov/AnhDuy
---

# make_tfidf_similarity(catalog)
Similarity trực tuyến offline: **cosine** trên TF-IDF của toàn bộ text ontology.
## similarity(text_a, text_b)
Tính cosine similarity của 2 text.
# make_ollama_similarity()
Similarity dense qua Ollama (cần Ollama đang chạy)
# build_matrix(backend="local", catalog_path="data/catalog.json")
- Gọi `make_tfidf_similarity(catalog)` và `make_ollama_similarity()`
- Tính $\rho(A|B)$ cho các cặp kiến trúc.
# main