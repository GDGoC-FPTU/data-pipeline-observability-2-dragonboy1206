# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** dragonboy1206  
**Name:** dragonboy1206  
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200.0. | 9 | Du lieu da duoc validate, category duoc chuan hoa thanh Title Case, price hop le va co timestamp xu ly. Agent tim dung nhom electronics va chon san pham co gia cao nhat trong du lieu sach. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Du lieu co duplicate ID, sai kieu du lieu, null value va outlier rat lon. Agent khong co buoc validate nen bi outlier "Nuclear Reactor" danh lua ket qua. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai voi garbage data vi logic cua no tin truc tiep vao file CSV ma khong co lop kiem tra chat luong du lieu truoc khi suy luan. Trong `garbage_data.csv`, ID bi trung lap lam mat do tin cay cua khoa dinh danh, price co gia tri `"ten dollars"` lam cot gia bi pha tron kieu du lieu, record null thieu ID/category tao ra thong tin khong day du, va dac biet outlier `Nuclear Reactor` co price `999999` nam trong category electronics. Vi agent chi loc category electronics roi chon record co price cao nhat, outlier nay lap tuc tro thanh "best choice" du khong phu hop voi bo san pham thong thuong. Dieu nay cho thay prompt tot khong the bu dap hoan toan cho data pipeline yeu: neu dau vao bi nhieu, thieu, sai kieu hoac chua outlier, agent se dua ra cau tra loi co ve hop ly ve mat cu phap nhung sai ve nghia vu nghiep vu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y. Prompt giup agent hieu cau hoi, nhung chat luong du lieu quyet dinh nen tang cua cau tra loi. Neu pipeline co validation, transform va logging ro rang, agent co co hoi tra loi dung va de audit hon. Neu bo du lieu bi poison boi duplicate, null, wrong type va outlier, cau tra loi se sai ngay ca khi cau hoi va prompt duoc viet tot.
