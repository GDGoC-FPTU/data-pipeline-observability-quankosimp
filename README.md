[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572458&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** quananhxyz@gmail.com
**Student ID:** AI20K-0132
**Name:** Nguyễn Anh Quân

---

## Mo ta

Bai lab xay dung ETL pipeline co 4 buoc Extract - Validate - Transform - Load cho du lieu san pham.
Trong bai lam, toi da:
- Doc du lieu tu `raw_data.json`
- Loai bo record khong hop le (price <= 0 hoac category rong)
- Chuan hoa category ve Title Case, tinh `discounted_price` giam 10%, them `processed_at`
- Luu ket qua ra `processed_data.csv`

Ngoai ra, toi thuc hien stress test voi agent mo phong de so sanh tac dong cua clean data va garbage data, sau do tong hop nhan xet trong `experiment_report.md`.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- ETL tu `raw_data.json`: tong 5 records
- Sau validation: 3 valid, 2 dropped
- Output `processed_data.csv`: 3 records da duoc transform day du
- Stress test agent:
  - Clean data: Agent chon `Laptop` gia `$1200` (hop ly)
  - Garbage data: Agent chon `Nuclear Reactor` gia `$999999` (bi outlier chi phoi)
