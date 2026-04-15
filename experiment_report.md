# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600310

**Name:** Trần Thái Thịnh

**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "Agent: Based on my data, the best choice is Laptop at $1200." | 10/10 | Kết quả hợp lý. |
| Garbage Data (`garbage_data.csv`) | "Agent: Based on my data, the best choice is Nuclear Reactor at $999999." | 2/10 | Agentt bị dẫn bởi outlier lớn. |

Bo sung log ETL de doi chieu chat luong dau vao:
- `Validation summary: 3 kept, 2 dropped.`
- `Errors found: [{'id': 3, 'reason': 'Price <= 0'}, {'id': 4, 'reason': 'Missing Category'}]`
- `Pipeline completed! 3 records saved.`

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent đang chọn sản phẩm có giá cao nhất trong nhóm "electronics". Khi dữ liệu bị nhiễu, bản ghi bất thường (Nuclear Reactor giá 999999) bị chọn sai làm kết quả tốt nhất. Điều này cho thấy chất lượng dữ liệu ảnh hưởng trực tiếp đến độ chính xác của Agent. Vì vậy, ngoài validate cơ bản, cần thêm kiểm soát outlier và quy tắc domain.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

Đồng ý. Prompt tốt chỉ cải thiện cách hỏi, còn dữ liệu sai thì kết quả vẫn sai. Thực nghiệm cho thấy cùng một câu hỏi, dữ liệu sạch cho đáp án hợp lý, còn dữ liệu bẩn cho đáp án vô lý. Do đó, chất lượng dữ liệu là ưu tiên số một.
