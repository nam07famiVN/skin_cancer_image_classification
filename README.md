🩺 Skin Cancer Classification using SVM & HOG

- Dự án nghiên cứu và xây dựng hệ thống hỗ trợ chẩn đoán ung thư da dựa trên bộ dữ liệu HAM10000. 

- Hệ thống sử dụng thuật toán Support Vector Machine (SVM) kết hợp với kỹ thuật trích xuất đặc trưng HOG (Histogram of Oriented Gradients) và Thông tin màu sắc.

📌 Tổng quan dự án

Dự án được chia làm hai giai đoạn chính:

- Phân loại Nhị phân (Binary Classification): Phân loại nốt ruồi thành 2 nhóm Lành tính (Benign) và Ác tính (Malignant). Mục tiêu tối ưu hóa chỉ số Recall để không bỏ sót bệnh nhân.

- Phân loại Đa lớp (Multi-class Classification): Chẩn đoán chi tiết 7 loại bệnh lý da liễu có trong tập dữ liệu.

📊 Bộ dữ liệu (Dataset)

- Nguồn: HAM10000 (Human Against Machine).

- Số lượng: 10,015 ảnh da liễu.

- Các lớp bệnh lý:

- akiec: Actinic keratoses.

- bcc: Basal cell carcinoma.

- bkl: Benign keratosis-like lesions.

- df: Dermatofibroma.mel: Melanoma.

- nv: Melanocytic nevi.

- vasc: Vascular lesions.

🛠 Quy trình thực hiện (Pipeline)

- 1. Tiền xử lý dữ liệu

  + Resize ảnh về kích thước chuẩn (64x64).

Chuyển đổi ảnh sang không gian màu xám cho HOG và giữ nguyên kênh màu RGB cho đặc trưng màu sắc.

Sử dụng SMOTE kết hợp RandomUnderSampler để giải quyết vấn đề mất cân bằng dữ liệu nghiêm trọng giữa các lớp.

2. Trích xuất đặc trưng (Feature Extraction)

Hệ thống sử dụng vector đặc trưng kết hợp:

HOG Features: Trích xuất thông tin về hình dạng và cấu trúc biên của nốt ruồi.

Color Features: Tính toán giá trị Trung bình (Mean) và Độ lệch chuẩn (Std) của các kênh màu nhằm nhận diện sắc tố đặc trưng của ung thư.

3. Huấn luyện mô hình (Model Training)Thuật toán:

SVM với Kernel RBF.

Tối ưu hóa: GridSearchCV để tìm bộ thông số C và gamma tốt nhất.

Chiến lược đa lớp: One-vs-Rest (OvR).

Scoring: Sử dụng f1_macro và Recall để đảm bảo tính khách quan giữa các lớp.

📈 Kết quả đạt được

Phân loại Nhị phân (Sàng lọc)

Recall (Ác tính): ~92% (Phát hiện hầu hết các ca nguy hiểm).

Accuracy: ~62% (Đã đánh đổi độ chính xác tổng thể để ưu tiên an toàn bệnh nhân).

Phân loại Đa lớp (7 lớp)

Mô hình phân biệt tốt các lớp có đặc trưng mạnh như vasc và nv.

Chỉ số F1-macro ổn định sau khi cân bằng dữ liệu bằng SMOTE.

🚀 Hướng dẫn cài đặt & Chạy

Yêu cầu hệ thống

pip install numpy pandas scikit-learn scikit-image opencv-python matplotlib seaborn imbalanced-learn

Chạy dự án

Clone dự án: git clone https://github.com/your-username/skin-cancer-svm.git

Mở file notebook trên Google Colab.

Thay đổi đường dẫn dataset và chạy toàn bộ các cell.

Sử dụng file skin_cancer_svm_model.pkl để dự đoán ảnh mới.

🖼 Minh họa kết quảConfusion Matrix:

Hiển thị chi tiết các ca đoán đúng/sai cho 7 lớp.

ROC Curve: AUC đạt mức ấn tượng cho các lớp bệnh lý ác tính.

⚖️ Giấy phép & Tuyên bố miễn trừ

Dự án được xây dựng cho mục đích học thuật và nghiên cứu.

Lưu ý: Kết quả từ mô hình chỉ mang tính chất tham khảo, không thay thế cho chẩn đoán chuyên môn của bác sĩ da liễu.
