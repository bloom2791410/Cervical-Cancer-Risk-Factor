# Cervical-Cancer-Risk-Factor
## THÔNG TIN THÀNH VIÊN NHÓM VÀ CÔNG VIỆC

### 1. Thông tin thành viên và phân công nhiệm vụ

| STT | Họ và tên | MSV | Nhiệm vụ chính | Hoàn thành |
|---|---|---|---|---|
| 1 | Nguyễn Thị Ngọc Hân *(Trưởng nhóm)* | 23000118 | Tổng hợp nội dung báo cáo, làm slide thuyết trình, xây dựng và đánh giá mô hình KNN, SVM; thực hiện xử lý mất cân bằng dữ liệu bằng SMOTE; Code. | 100% |
| 2 | Lại Thị Huế | 23000122 | Cài đặt và trình bày phương pháp giảm chiều PCA, LDA, phương pháp Elbow Method và Silhouette Score; Đưa ra kết quả thực nghiệm (train:validation: 4:1 , 7:3, 6:4) | 100% |
| 3 | Mẫn Thị Ngân An | 23000088 | Tiền xử lý dữ liệu, xây dựng mô hình Logistic Regression, K-Means; hỗ trợ viết báo cáo và làm slide. | 100% |

---

### 2. Hướng dẫn tổ chức và vận hành chương trình

#### a. Môi trường cài đặt

- **Ngôn ngữ lập trình:** Python  
- **Thư viện sử dụng:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `imblearn`  
- **Công cụ thực hiện:** Google Colab, Visual Studio Code, LaTeX.

#### b. Quy trình thực hiện

1. **Nạp dữ liệu:**  
   Tải file `risk_factors_cervical_cancer.csv` vào môi trường làm việc.

2. **Tiền xử lý dữ liệu:**  
   Chuyển các giá trị `"?"` thành `NaN`, ép kiểu dữ liệu về dạng số và kiểm tra số lượng giá trị thiếu.

3. **Xử lý giá trị thiếu:**  
   Loại bỏ hai thuộc tính có tỷ lệ thiếu quá cao:

   - `STDs: Time since first diagnosis`
   - `STDs: Time since last diagnosis`

   Sau đó, điền giá trị thiếu của các thuộc tính còn lại bằng **trung vị**.

4. **Tách biến đầu vào và biến mục tiêu:**  

   - `X`: các thuộc tính đầu vào  
   - `y`: biến mục tiêu `Biopsy`

5. **Chia dữ liệu:**  
   Chia dữ liệu thành tập Train, Validation và Test theo các tỷ lệ thực nghiệm khác nhau. Tập Test được giữ cố định để đánh giá cuối cùng.

6. **Chuẩn hóa dữ liệu:**  
   Sử dụng `StandardScaler` để đưa các thuộc tính về cùng thang đo.

7. **Xử lý mất cân bằng dữ liệu:**  
   Áp dụng **SMOTE** trên tập Train nhằm cân bằng số lượng mẫu giữa hai lớp của biến `Biopsy`.

8. **Giảm chiều dữ liệu:**  
   Thực hiện:

   - **PCA** với `n_components = 0.95`, dữ liệu được giảm còn 18 chiều.
   - **LDA** với `n_components = 1`, do bài toán có 2 lớp.

9. **Huấn luyện mô hình:**  
   Xây dựng và đánh giá các mô hình:

   - KNN
   - Logistic Regression
   - SVM
   - K-Means

10. **Tối ưu tham số:**  
    Sử dụng Grid Search/Cross Validation để lựa chọn tham số phù hợp cho các mô hình phân loại, đặc biệt ưu tiên chỉ số **Recall** do bài toán thuộc lĩnh vực y tế.

11. **Xuất kết quả:**  
    Hiển thị các chỉ số đánh giá:

    - Accuracy
    - Precision
    - Recall
    - F1-score
    - Confusion Matrix

---

### 3. Các kịch bản thực nghiệm

| Kịch bản | Mô tả thiết lập | Mục tiêu |
|---|---|---|
| Kịch bản 1 | Dữ liệu gốc sau tiền xử lý và SMOTE + KNN/Logistic/SVM | Thiết lập kết quả cơ sở để so sánh với các phương pháp giảm chiều. |
| Kịch bản 2 | Dữ liệu sau PCA + KNN/Logistic/SVM | Đánh giá việc giảm chiều và giữ lại 95% phương sai có giúp cải thiện hiệu quả phân loại hay không. |
| Kịch bản 3 | Dữ liệu sau LDA + KNN/Logistic/SVM | Kiểm tra khả năng tách lớp của LDA và tác động đến các chỉ số Precision, Recall, F1-score. |
| Kịch bản 4 | Thay đổi tỷ lệ Train:Validation gồm 4:1, 7:3 và 6:4 | Đánh giá độ ổn định của mô hình khi thay đổi cách chia dữ liệu. |
| Kịch bản 5 | Thay đổi tham số K trong KNN | Tìm giá trị K phù hợp, hạn chế overfitting và cải thiện khả năng dự đoán. |
| Kịch bản 6 | Áp dụng K-Means trên dữ liệu sau giảm chiều | Quan sát cấu trúc cụm tiềm ẩn và so sánh tương đối với nhãn thực tế. |

---

### 4. Link lấy dữ liệu và tổ chức thư mục thực nghiệm

#### 4.1. Link lấy dữ liệu

Dữ liệu được lấy từ nguồn mở của **UCI Machine Learning Repository**:

- **Tên bộ dữ liệu:** Cervical Cancer (Risk Factors) Data Set  
- **Link tải:** <https://archive.ics.uci.edu/dataset/383/cervical+cancer+risk+factors>  
- **File dữ liệu:** `risk_factors_cervical_cancer.csv`

#### 4.2. Hướng dẫn tổ chức thư mục

Nhóm tổ chức thư mục dự án theo cấu trúc sau:

```{text}
DỰ ÁN UNG THƯ CỔ TỬ CUNG/
├── risk_factors_cervical_cancer.csv
├── NguyenThiNgocHan_8_report.pdf
├── NguyenThiNgocHan_8_presentation.pdf
├── NguyenThiNgocHan_8_readme.md
└── NguyenThiNgocHan_8_Main_model.ipynb

```
#### 4.3. Hướng dẫn thực thi chương trình

1. Mở file `main_model.ipynb` bằng **Google Colab** hoặc **Visual Studio Code**.

2. Tải file dữ liệu `risk_factors_cervical_cancer.csv` vào thư mục `data/`.

3. Cài đặt các thư viện cần thiết nếu môi trường chưa có:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
```

4. Kiểm tra lại đường dẫn đọc dữ liệu trong code.

5. Chạy toàn bộ chương trình theo thứ tự:

   - Tiền xử lý dữ liệu
   - Chia tập Train/Validation/Test
   - Chuẩn hóa dữ liệu
   - Xử lý mất cân bằng dữ liệu bằng SMOTE
   - Giảm chiều dữ liệu bằng PCA/LDA
   - Huấn luyện mô hình
   - Đánh giá kết quả

6. Quan sát kết quả thông qua:

   - `Classification Report`
   - `Confusion Matrix`
   - Các biểu đồ trực quan hóa
