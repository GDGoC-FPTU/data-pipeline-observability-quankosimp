[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572458&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** quananhxyz@gmail.com
**Student ID:** AI20K-0132
**Name:** Nguyễn Anh Quân

---

## Mô tả

Bài lab xây dựng ETL pipeline có 4 bước Extract - Validate - Transform - Load cho dữ liệu sản phẩm.
Trong bài làm, tôi đã:
- Đọc dữ liệu từ `raw_data.json`
- Loại bỏ record không hợp lệ (`price <= 0` hoặc `category` rỗng)
- Chuẩn hóa `category` về Title Case, tính `discounted_price` giảm 10%, thêm `processed_at`
- Lưu kết quả ra `processed_data.csv`

Ngoài ra, tôi thực hiện stress test với agent mô phỏng để so sánh tác động của clean data và garbage data, sau đó tổng hợp nhận xét trong `experiment_report.md`.

---

## Cách chạy (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chạy ETL Pipeline
```bash
python solution.py
```

### Chạy Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

---

## Cấu trúc thư mục

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output của pipeline
├── experiment_report.md     # Báo cáo thí nghiệm
└── README.md                # File này
```

---

## Kết quả

- ETL từ `raw_data.json`: tổng 5 records
- Sau validation: 3 valid, 2 dropped
- Output `processed_data.csv`: 3 records đã được transform đầy đủ
- Stress test agent:
  - Clean data: Agent chọn `Laptop` giá `$1200` (hợp lý)
  - Garbage data: Agent chọn `Nuclear Reactor` giá `$999999` (bị outlier chi phối)
