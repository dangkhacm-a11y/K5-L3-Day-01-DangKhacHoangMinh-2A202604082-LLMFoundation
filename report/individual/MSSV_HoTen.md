# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV:**2A202604082
- **Họ và tên:**Đặng Khắc Hoàng Minh
- **SEED** (in ở ô đầu notebook):1488

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | Có |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | Có |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | Có |

## 2. Kết quả chính

                                 precision  recall  F1 (test)  F1 (SUB 40)  \
1. BoW + LogReg (tự code)            0.987   0.817      0.894        0.857   
2. BoW + MLP (deep learning)         0.966   0.914      0.939        0.923   
3a. Encoder (MiniLM) + kNN           0.850   0.914      0.881        0.900   
3b. Encoder (MiniLM) + LogReg        0.935   0.935      0.935        0.950   
3c. Encoder (MiniLM) + MLP head      0.946   0.935      0.941        0.923   

                                 train (s)  tin/s (cả lô)  p50 ms/tin  \
1. BoW + LogReg (tự code)            2.348      51631.623       0.053   
2. BoW + MLP (deep learning)         4.836      46491.664       0.189   
3a. Encoder (MiniLM) + kNN          86.475         25.368      50.944   
3b. Encoder (MiniLM) + LogReg       86.913         37.615      26.963   
3c. Encoder (MiniLM) + MLP head     87.435         40.365      26.243   

                                 p95 ms/tin  USD / 1k tin  
1. BoW + LogReg (tự code)             0.077           0.0  
2. BoW + MLP (deep learning)          0.308           0.0  
3a. Encoder (MiniLM) + kNN           69.540           0.0  
3b. Encoder (MiniLM) + LogReg        39.263           0.0  
3c. Encoder (MiniLM) + MLP head      40.859           0.0  
• Hàng LLM chỉ đo trên SUB (40 tin) → so sánh chất lượng công bằng bằng cột 'F1 (SUB 40)'.
• SUB chỉ 40 tin: 1 tin sai đổi F1 vài điểm. Chênh < ~0.05 F1 coi như HOÀ — đừng xếp hạng theo số lẻ.
• Inference đo TỪ VĂN BẢN THÔ → NHÃN (gồm cả vectorize / encode). p50/p95 = gọi từng tin một, như một request thật.
• train (s) của 3a/3b/3c = thời gian encoder MiniLM encode tập train (+ train đầu LogReg / MLP); LLM = 0 vì không train. Số đo phụ thuộc CPU/GPU của Colab.

## 3. Dự đoán và thực tế

*Chọn 3 dự đoán `predict(...)` lệch nhiều nhất so với kết quả. Mỗi cái: bạn đoán gì, ra gì, vì sao lệch.*
Dự đoán loss của learningrate = 50 sẽ giao lệch rất xa điểm hội tụ nhuwg thực tế loss lại rất thấp thấp nhất trong các learningrate test

## 4. Phân tích 50 case khó

*Model nào tụt nhiều nhất, ở nhóm case nào? Nêu 2 case cụ thể và cơ chế khiến model sai.*

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học

*Mỗi lần dùng AI: hỏi gì, nhận gì, bạn sửa gì. Sau đó 2–3 câu: điều bạn hiểu ra hôm nay mà trước đó chưa hiểu.*
