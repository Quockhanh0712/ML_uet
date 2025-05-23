# Phân loại ảnh CIFAR-100 với ResNet18

Dự án này triển khai một mạng nơ-ron ResNet18 từ đầu để phân loại ảnh trong tập dữ liệu CIFAR-100.  Nó tránh sử dụng các mô hình được huấn luyện trước, tập trung vào việc xây dựng và huấn luyện mô hình chỉ dựa trên dữ liệu CIFAR-100.

## Mục tiêu dự án

Mục tiêu chính là đạt được độ chính xác cao trên tập kiểm tra CIFAR-100.  Notebook của dự án trình bày chi tiết kiến trúc mô hình, quá trình huấn luyện và kết quả đánh giá.

## Chi tiết triển khai

* **Mô hình:** Kiến trúc ResNet18 được xây dựng bằng PyTorch. Mô hình bao gồm các BasicBlock và sử dụng các kỹ thuật như chuẩn hóa theo batch, dropout và lớp gộp trung bình thích ứng.
* **Tập dữ liệu:** Sử dụng tập dữ liệu CIFAR-100, bao gồm 100 lớp với 50.000 ảnh huấn luyện và 10.000 ảnh kiểm tra.
* **Tăng cường dữ liệu:** Dữ liệu huấn luyện được tăng cường bằng cách cắt ngẫu nhiên, lật ngang, thay đổi màu sắc và xóa ngẫu nhiên. Điều này giúp cải thiện khả năng khái quát hóa và tính mạnh mẽ của mô hình.
* **Chuẩn hóa:** Ảnh đầu vào được chuẩn hóa bằng cách sử dụng giá trị trung bình và độ lệch chuẩn được tính toán từ tập huấn luyện CIFAR-100.
* **Trình tối ưu:** Sử dụng trình tối ưu AdamW với bộ lập lịch tốc độ học (CosineAnnealingLR) để điều chỉnh tốc độ học trong suốt quá trình huấn luyện.
* **Hàm mất mát:** Sử dụng hàm mất mát cross-entropy cho phân loại nhiều lớp.
* **Huấn luyện:** Mô hình được huấn luyện trong một số epoch nhất định và mất mát huấn luyện và độ chính xác được theo dõi theo từng epoch.
* **Đánh giá:** Hiệu suất của mô hình được huấn luyện được đánh giá trên tập kiểm tra CIFAR-100 bằng một hàm đánh giá riêng. Độ chính xác kiểm tra được báo cáo là số liệu hiệu suất cuối cùng.

## Kết quả

Notebook hiển thị các đường cong mất mát và độ chính xác huấn luyện.  Độ chính xác kiểm tra cuối cùng đạt được là khoảng 74%, chứng minh tính hiệu quả của mô hình ResNet18 được triển khai trên nhiệm vụ phân loại CIFAR-100
