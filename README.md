# Screen Description Writer

Skill cho AI agent hỗ trợ kỹ thuật **Interface Analysis** trong BABOK v3 (§10.24)
cho **user interface**, thực hiện trên một **prototype** giao diện (Prototyping
§10.36): từ ảnh screenshot/wireframe, đặc tả màn hình bằng template chuẩn của
BABOK — **Interface definition** (§10.24.3) + **Data Dictionary** (§10.12).

Tài liệu viết bằng tiếng Việt, giữ nguyên thuật ngữ BABOK tiếng Anh (interface,
user interface, prototype, data element, values/meanings, exchange method…).

## Purpose

Theo BABOK §10.24.1, interface analysis xác định **where/what/why/when/how/for
whom** thông tin được trao đổi qua một interface. Áp dụng cho user interface: mỗi
phần tử trên màn hình là một điểm trao đổi thông tin. Skill đặc tả màn hình thành:
(a) **Interface definition** — name, coverage/span, exchange method, message
format, exchange frequency; và (b) **Data Dictionary** của các data element —
`Name | Aliases | Values/Meanings | Description`.

## Cách dùng

```text
Bạn: [upload ảnh màn hình] Mô tả màn hình này
AI:  [Interface definition + Data Dictionary các data element + interactions/events]
```

Các cụm từ kích hoạt: "mô tả màn hình", "mô tả MH", "describe screen", "list hạng
mục màn hình", "mô tả MH mobile", "mô tả bottom sheet / popup / dashboard / form".

## Cấu trúc

```text
screen-description-writer/
├── SKILL.md     ← kỹ thuật (Purpose / Description / Elements /
│                  Usage Considerations) + quy trình + template BABOK
└── README.md
```

`SKILL.md` được nạp vào context của agent.

## Cài đặt

Skill agent-agnostic (Claude, Antigravity/Gemini, Codex CLI, Cursor…). Clone repo
về đường dẫn skill của tool, hoặc cho agent đọc `SKILL.md` như context document:

```bash
git clone https://github.com/huyhn-ba-po/screen-description-writer-.git
```

## Phạm vi (theo Usage Considerations của BABOK)

Interface analysis làm rõ **những gì trao đổi qua giao diện** — không cho insight
về internal components của solution (§10.24.4). Skill mô tả interface đã có, không
suy diễn logic xử lý bên trong và không thiết kế UI mới (tránh sa đà vào "how" —
limitation của Prototyping §10.36.4). Để mô hình hoá luồng nghiệp vụ dùng Process
Modelling (activity-diagram-builder); để thể hiện tương tác giữa các object dùng
Sequence Diagrams (mermaid-sequence-diagram).
