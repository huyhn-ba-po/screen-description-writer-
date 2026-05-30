---
name: screen-description-writer
description: |
  Hiện thực kỹ thuật Interface Analysis (BABOK v3 §10.24) cho user interface, trên
  một prototype giao diện (Prototyping §10.36): từ ảnh screenshot/wireframe, đặc tả
  màn hình bằng template chuẩn của BABOK — Interface definition (§10.24.3) + Data
  Dictionary (§10.12: Name | Aliases | Values/Meanings | Description). Output
  markdown trong chat, không tạo file. Dùng khi user nói "mô tả màn hình", "mô tả
  MH", "mô tả UI", "describe screen", "list hạng mục màn hình", "mô tả MH mobile",
  "mô tả bottom sheet/popup/dashboard/form", kể cả khi upload ảnh + nói tắt "mô tả
  đi". KHÔNG dùng cho: vẽ sequence diagram (mermaid-sequence-diagram), activity/
  process model (activity-diagram-builder), thiết kế UI mới.
---

# Screen Description Writer

Skill này hiện thực kỹ thuật **Interface Analysis** (BABOK v3 §10.24) cho **user
interface**, thực hiện trên một **prototype** giao diện (Prototyping §10.36). Phần
đặc tả dữ liệu dùng template **Data Dictionary** (§10.12) của BABOK. Thuật ngữ kỹ
thuật giữ nguyên tiếng Anh theo BABOK.

## Purpose (Mục đích)

> *"Interface analysis is used to identify where, what, why, when, how, and for
> whom information is exchanged between solution components or across solution
> boundaries."* — BABOK v3, §10.24.1

Skill đặc tả một **user interface** (một interface type theo BABOK) từ ảnh
prototype, làm rõ thông tin được trao đổi qua từng phần tử giữa người dùng và
solution.

## Description (Mô tả)

- Một **interface** là connection giữa hai component/solution; **user interface**
  (người dùng tương tác trực tiếp với solution) là một interface type (§10.24.2).
- Theo §10.24.3 ".3 Define Interfaces", đặc tả một interface tập trung vào: các
  **inputs/outputs**, các **validation rules** chi phối input/output, và các
  **events** kích hoạt tương tác. BA xét **who** dùng, **what** thông tin đi qua,
  **when/where** xảy ra.
- Ảnh screenshot/wireframe là một **prototype** (thường là *Visual* hoặc
  *Usability/Functional Prototype* theo §10.36) — mô hình trực quan của future
  state. Skill **mô tả** prototype đã có, KHÔNG tạo prototype mới.
- Các **data element** xuất hiện trên giao diện được đặc tả theo kỹ thuật **Data
  Dictionary** (§10.12) để chuẩn hoá định nghĩa, ý nghĩa và giá trị hợp lệ.

## Elements (Các thành phần)

Đặc tả một màn hình gồm 2 phần, đều theo template của BABOK.

### (a) Interface definition — Interface Analysis §10.24.3

Mô tả ở mức cả màn hình. Theo BABOK, "interface definition includes":

- **Name** — tên của interface (màn hình).
- **Coverage / span** — phạm vi của interface (màn hình bao trùm gì).
- **Exchange method** — cách trao đổi giữa người dùng và solution (vd: form nhập
  liệu, danh sách + phân trang, bottom sheet chọn, popup chi tiết).
- **Message format** — định dạng thông tin trao đổi.
- **Exchange frequency** — tần suất sử dụng (ghi nếu biết).

Kèm theo: **inputs/outputs**, **validation rules**, và **trigger events** theo
typical / alternate / exception flow.

### (b) Data Dictionary — §10.12.3

Mỗi data element trên màn hình ghi theo bảng data dictionary chuẩn (4 cột bắt
buộc theo ".2 Primitive Data Elements"):

| Name | Aliases | Values / Meanings | Description |
|---|---|---|---|
| `<tên duy nhất>` | `<tên gọi khác của stakeholder>` | `<giá trị hợp lệ HOẶC mô tả format cho phép, gồm số ký tự>` | `<định nghĩa element trong ngữ cảnh solution>` |

- **Name**: tên duy nhất của data element (được composite element tham chiếu).
- **Aliases**: tên gọi khác mà các stakeholder dùng.
- **Values / Meanings**: danh sách giá trị hợp lệ (enumerated list) HOẶC mô tả
  format cho phép — **bao gồm số ký tự**; giá trị viết tắt thì giải nghĩa.
- **Description**: định nghĩa của element trong ngữ cảnh solution.

**Composite Elements** (§10.12.3 ".3") — element ghép từ các element nguyên thuỷ:
- **Sequences**: thứ tự, dùng dấu `+`. Vd: `Customer Name = First Name + Middle Name + Family Name`.
- **Repetitions**: element có thể lặp nhiều lần.
- **Optional Elements**: có thể có hoặc không trong một instance.

Mẫu chuẩn của BABOK (Figure 10.12.1) để tham chiếu cách điền cột:

| Name | Aliases | Values / Meanings | Description |
|---|---|---|---|
| First Name | Given Name | Minimum 2 characters | First Name |
| Middle Name | Middle Name | Can be omitted | Middle Name |
| Last Name | Surname | Minimum 2 characters | Family Name |

→ Composite: `Customer Name = First Name + Middle Name + Last Name`.

> Mẫu trên là template của BABOK. Nếu dự án của user có quy ước data dictionary
> riêng (thêm cột Type/Format/Source…), tuân theo quy ước đó.

## Quy trình tạo

1. **Nhận diện interface** từ ảnh (prototype): loại (quản trị/desktop hay mobile),
   phạm vi. Không chắc → hỏi 1 câu.
2. **Interface definition** — ghi Name, coverage/span, exchange method, message
   format, exchange frequency cho cả màn hình.
3. **Liệt kê data element** hiển thị/nhập trên màn hình; với mỗi element điền
   **Name | Aliases | Values/Meanings | Description** theo Data Dictionary.
4. **Composite structures** — ghi sequences / repetitions / optional nếu có.
5. **Interactions & events** — exchange method của từng tương tác (nhập / chọn /
   click / upload / toggle), validation rules, và trigger events (typical /
   alternate / exception flow).
6. **Output markdown trong chat** — không tạo file; không dùng `create_file` /
   `present_files`.

Đa ngôn ngữ: theo Interface Analysis ("for whom"), nhu cầu đa ngôn ngữ là một
usability/accessibility requirement — ghi giá trị từng ngôn ngữ trong cột
**Values / Meanings** (hoặc tách cột localized label nếu dự án yêu cầu).

## Usage Considerations

### Interface Analysis (§10.24.4)
**Strengths:** đặc tả interface sớm → tăng functional coverage; spec rõ ràng →
phân bổ được requirements/business rules/constraints; phạm vi rộng → tránh
over-analysis. **Limitation:** không cho insight về các khía cạnh **internal** của
solution. → Skill mô tả thông tin trao đổi qua giao diện, không suy diễn logic
xử lý bên trong.

### Data Dictionary (§10.12.4)
**Strengths:** cho mọi stakeholder hiểu chung về format và nội dung dữ liệu; một
repository metadata nhất quán. **Limitations:** cần maintain thường xuyên kẻo lỗi
thời; phải làm nhất quán mới dễ tra cứu.

### Prototyping (§10.36.4)
**Strength:** biểu diễn trực quan future state, lấy feedback sớm. **Limitation:**
dễ sa đà bàn "**how**" thay vì "**what**". → Skill chỉ mô tả prototype đã có,
không thiết kế UI mới.

## Ràng buộc khi đặc tả

- **Không tự chế** giá trị/format/độ dài không có trong ảnh → cột Values/Meanings
  để `--` (giữ đặc tả đúng "what is exchanged", không bịa).
- Không dịch bừa nếu ảnh chỉ có 1 ngôn ngữ.
- Giữ nguyên tên data element như trên UI (nhất quán với interface thật).
- Chỉ hỏi khi logic nghiệp vụ thật sự mơ hồ (validation rule, trigger event,
  điều hướng) — không hỏi về nguồn dữ liệu.
