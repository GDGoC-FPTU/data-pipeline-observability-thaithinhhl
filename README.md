[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574201&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** tranthaithinh258@gmail.com
**Name:** Trần Thái Thịnh

---

## Mô tả

Lab này xây dựng ETL pipeline gồm 4 bước: Extract, Validate, Transform, Load.  
Pipeline loại bỏ bản ghi lỗi, tính giá sau giảm 10%, thêm timestamp và xuất ra `processed_data.csv`.  
Sau đó mô phỏng Agent để so sánh ảnh hưởng của clean data và garbage data.

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

- ETL xử lý `5` records từ `raw_data.json`.
- Sau validate: `3` records hợp lệ, `2` records bị loại.
- Agent với clean data trả lời hợp lý (`Laptop`).
- Agent với garbage data bị lệch kết quả (`Nuclear Reactor`), cho thấy tầm quan trọng của data quality.
