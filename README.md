[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112861&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** vuh120604@gmail.com  
**Student ID:** dragonboy1206  
**Name:** dragonboy1206

---

## Mo ta

Bai lab nay xay dung mot ETL pipeline don gian bang Python va pandas. Pipeline doc du lieu san pham tu `raw_data.json`, loai cac record khong hop le, chuan hoa du lieu, them cot giam gia va timestamp xu ly, sau do ghi ket qua ra `processed_data.csv`. Bai lam cung co phan stress test de so sanh tac dong cua clean data va garbage data len mot agent mo phong.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

Ket qua mong doi:
- Doc 5 records tu `raw_data.json`
- Giu lai 3 records hop le
- Loai 2 records loi: price <= 0 va category rong
- Tao file `processed_data.csv`

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

Hoac chay truc tiep ham simulation:
```bash
python -c "from agent_simulation import simulate_agent_response; print(simulate_agent_response('What is the best electronic product?', 'processed_data.csv')); print(simulate_agent_response('What is the best electronic product?', 'garbage_data.csv'))"
```

### Chay test local
```bash
pytest
```

---

## Cau truc thu muc

```text
solution.py              # ETL Pipeline script
raw_data.json            # Du lieu nguon
processed_data.csv       # Output cua pipeline
generate_garbage.py      # Tao garbage_data.csv
garbage_data.csv         # Du lieu ban cho stress test
agent_simulation.py      # Agent mo phong doc CSV va tra loi
experiment_report.md     # Bao cao thi nghiem
README.md                # File nay
tests/test_autograder.py # Test cham diem tu dong
```

---

## Ket qua

Pipeline da xu ly thanh cong 5 records dau vao, giu lai 3 records hop le va loai 2 records khong dat dieu kien validation. File output co them `discounted_price = price * 0.9`, category da duoc chuan hoa Title Case, va cot `processed_at` de theo doi thoi diem xu ly. Stress test cho thay agent tra loi dung hon voi clean data, nhung bi anh huong manh boi outlier trong garbage data.
