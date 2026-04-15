# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-0132
**Name:** Nguyễn Anh Quân
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Du lieu sau ETL giu lai record hop le, category duoc chuan hoa, gia tri price hop ly nen agent chon dung san pham electronics co gia cao nhat trong tap du lieu sach. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Agent bi "danh lua" boi outlier gia tri qua lon, khong co co che xu ly anomaly/validation truoc khi suy luan nen dua ra ket qua phi thuc te. |


---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai vi du lieu rac lam huong suy luan don gian cua agent. Thu nhat, co outlier "Nuclear Reactor" voi price = 999999 trong category electronics, nen khi agent lay gia cao nhat thi record nay luon thang va che lap cac san pham hop ly nhu Laptop. Thu hai, co duplicate id (id=1 xuat hien 2 lan) lam giam do tin cay cua tap du lieu. Thu ba, co wrong data type ("ten dollars") co the gay loi tinh toan hoac lam sai ket qua thong ke neu pipeline xu ly so hoc. Cuoi cung, null/missing values (id rong, category rong, price = 0) cho thay du lieu khong duoc validation chat che. Tong hop lai, agent khong sai ve mat code truy van, nhung sai do "garbage in, garbage out": dau vao kem chat luong dan den dau ra phi thuc te.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Dong y. Prompt tot chi giup agent dien dat hoac suy luan tren nhung gi no "nhin thay"; neu du lieu nen bi nhiem outlier, sai kieu, trung lap, thieu truong quan trong thi cau tra loi van sai. Trong thi nghiem nay, cung mot prompt nhung clean data cho ket qua hop ly (Laptop $1200), con garbage data day agent den ket luan vo ly (Nuclear Reactor $999999). Vi vay, dam bao data quality la dieu kien tien quyet truoc khi toi uu prompt.
