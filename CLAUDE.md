# CLAUDE.md — Social Post Generator for LUBYLAB

## Tổng quan dự án

Đây là hệ thống tạo nội dung social media (ảnh + caption) cho thương hiệu **LUBYLAB** — thương hiệu derma cosmetic hiệu năng cao từ Hàn Quốc. Dự án hoạt động như một **content creation workflow** được điều khiển qua Claude Code, không phải ứng dụng phần mềm truyền thống.

**Mục tiêu:** Tự động hóa việc tạo social post (ảnh sản phẩm + caption) đảm bảo chuẩn thương hiệu LUBYLAB trên các nền tảng: Instagram, Facebook, TikTok, LinkedIn, Threads.

---

## Cấu trúc thư mục

```
Social_Post_Generator/
├── CLAUDE.md                    ← File này — hướng dẫn cho Claude Code
├── README.md                    ← Giới thiệu ngắn về dự án
│
├── brand/                       ← Tài liệu thương hiệu (BẮT BUỘC ĐỌC)
│   ├── brand_context.md         ← Định vị, đối tượng, thông điệp cốt lõi
│   ├── brand_voice.md           ← Tone of voice (đang cập nhật)
│   ├── product_catelog.md       ← Catalog sản phẩm: tên, thành phần, công dụng, path ảnh
│   └── visual_guideline.md      ← Bảng màu, ánh sáng, bố cục, prompt template
│
├── skills/
│   └── reference/
│       ├── SOP.md               ← Quy trình tạo social post (file quy trình chính)
│       ├── image_reference/     ← Ảnh sản phẩm gốc, chia theo dòng
│       │   ├── 1. Daily Care/Product Photos/
│       │   ├── 2. Recovery/Product Photos/
│       │   ├── 3. Elixir/Product Photos/
│       │   ├── group_color.jpg
│       │   └── LUBYLAB_Brand_Instruction_ENG.pptx
│       ├── social_post_caption/
│       │   └── korean/          ← Mẫu caption tiếng Hàn (.xlsx, .csv)
│       └── image_create/        ← Thư mục lưu ảnh đã tạo
│
└── outputs/                     ← Thư mục output
    ├── content_generated/       ← Caption/text đã tạo
    └── image_generated/         ← Ảnh đã tạo
```

---

## Quy trình làm việc (Workflow)

### File SOP chính: `skills/reference/SOP.md`

Khi người dùng yêu cầu tạo social post, Claude Code **PHẢI** tuân theo quy trình trong SOP.md:

### Thứ tự đọc file bắt buộc

1. **`brand/brand_context.md`** — Luôn đọc đầu tiên (định vị, đối tượng, thông điệp)
2. **`brand/visual_guideline.md`** — Luôn đọc khi tạo ảnh (bảng màu, layout, prompt template)
3. **`brand/product_catelog.md`** — Luôn đọc khi cần thông tin sản phẩm cụ thể
4. **`brand/brand_voice.md`** — Đọc khi có nội dung (hiện tại đang trống)

### 5 bước tạo social post

1. **Thu thập thông tin** — Hỏi người dùng: sản phẩm, nền tảng, mục tiêu, ngôn ngữ, ảnh tham khảo
2. **Xác định thông số kỹ thuật** — Tỷ lệ ảnh và kích thước theo nền tảng
3. **Tạo ảnh** — Đọc visual_guideline.md → chọn Layout (A/B/C/D) → viết prompt → gọi Nano Banana 2
4. **Viết caption** — Theo cấu trúc: Hook → Nội dung chính → CTA → Hashtags
5. **Review & Output** — Kiểm tra checklist ảnh + caption → trả kết quả

---

## Quy tắc thiết kế quan trọng

### Bảng màu theo dòng sản phẩm

| Dòng SP | Nền | Accent | Ghi chú |
|---------|-----|--------|---------|
| Basic (Daily Care) | Nude Beige `#FBF1E2` | Dark Gray `#262626` | Nền mặc định signature |
| Cica (Recovery) | Nude Beige `#FBF1E2` | Green `#97C93C` | Gradient: `#1A4644` → `#226653` |
| Artemisia | Forest Blue `#05272D` | Snow White `#FBFCFF` | Nền tối |
| Elixir | Dark `#161616` | Snow White `#FBFCFF` | Gradient: `#B9B9BB` → `#FBFBFB` |

### 4 Layout templates

- **A — Hero Single:** 1 sản phẩm trung tâm, 60-75% chiều cao (product launch, hero shot)
- **B — Dynamic Group:** Nhiều SP xếp chéo/tam giác (giới thiệu bộ sản phẩm)
- **C — Product-in-Action:** SP đang hoạt động — bột đổ, serum nhỏ giọt (storytelling, texture)
- **D — Floating:** SP bay/levitation, góc thấp (premium feel, dramatic)

### TUYỆT ĐỐI KHÔNG

- KHÔNG dùng nền trắng tinh `#FFFFFF` — luôn dùng Nude Beige hoặc Snow White `#FBFCFF`
- KHÔNG thêm hoa, lá, nước bắn, bokeh, sparkle, lens flare
- KHÔNG để AI tự tạo text trên bao bì — dùng ảnh gốc hoặc "leave label blank"
- KHÔNG dùng keyword soup ("4k, ultra HD, best quality, masterpiece")
- KHÔNG skip bước review

---

## Công cụ tạo ảnh: Nano Banana 2

- Image generation model dựa trên Google Gemini, tích hợp qua MCP server
- **Resolution khuyến nghị:** 2K cho social post, 512px cho draft nhanh
- **Batch:** Tối đa 4 ảnh/request
- **Thinking level:** low / medium / high (dùng high cho composition phức tạp)

### Cấu trúc prompt chuẩn

```
[1] MASTER PROMPT — copy từ visual_guideline.md Section 8
[2] LAYOUT PROMPT — chọn 1 trong 4 layout A/B/C/D
[3] THÔNG TIN CỤ THỂ — tên SP, kích thước, text overlay, dòng SP → bảng màu
```

Luôn paste Master Prompt ở đầu mọi prompt tạo ảnh.

---

## Thông số kỹ thuật theo nền tảng

| Nền tảng | Tỷ lệ | Kích thước | Caption |
|----------|--------|------------|---------|
| Facebook Feed | 1:1 / 4:5 | 1080x1080 / 1080x1350 | Trung bình, 3-7 hashtags |
| Instagram Feed | 1:1 / 4:5 | 1080x1080 / 1080x1350 | Dài OK, 5-15 hashtags |
| Instagram Stories/Reels | 9:16 | 1080x1920 | Ngắn |
| LinkedIn | 1:1 / 16:9 | 1080x1080 / 1200x628 | Professional, 3-5 hashtags |
| TikTok | 9:16 | 1080x1920 | Ngắn, catchy |
| Threads | 1:1 | 1080x1080 | Ngắn gọn |

---

## Quy tắc viết caption

- **Tone:** Chuyên nghiệp nhưng thân thiện, tự tin về hiệu quả sản phẩm
- **Thông điệp cốt lõi:** "home clinic" — mang phòng khám da liễu về nhà
- **Cấu trúc:** Hook → Nội dung (2-4 câu) → CTA → Hashtags
- **Hashtags bắt buộc:** `#LUBYLAB` và `#TheStandardOfDerma`
- **Công nghệ nhấn mạnh:** Exosome Spicule, PLLA, NAD+ (khi phù hợp)
- **Tham khảo mẫu:** `skills/reference/social_post_caption/korean/`

---

## Quy ước đặt tên file output

```
[YYYY-MM-DD]-[platform]-[loại-post]-[tên-sp].[ext]

Ví dụ:
2026-04-15-instagram-feed-pore-peeling-pad.png
2026-04-15-instagram-feed-pore-peeling-pad-caption.txt
```

- Ảnh lưu vào: `skills/reference/image_create/`
- Caption lưu vào: `outputs/content_generated/`

---

## Ngôn ngữ

- **Tài liệu dự án:** Tiếng Việt
- **Caption:** Tiếng Việt / Tiếng Hàn / Song ngữ (tuỳ yêu cầu)
- **Prompt tạo ảnh:** Tiếng Anh (cho Nano Banana 2)

---

## Lưu ý quan trọng cho Claude Code

1. **Luôn đọc SOP.md trước khi bắt đầu bất kỳ task tạo content nào**
2. **Không bao giờ bỏ qua bước review** — kiểm tra artifact, text sai, màu lệch
3. **Khi tạo ảnh, luôn attach ảnh sản phẩm gốc** từ `image_reference/` để đảm bảo sản phẩm trông chính xác
4. **Hỏi đủ thông tin trước khi tạo** — sản phẩm, nền tảng, mục tiêu, ngôn ngữ
5. **Nếu người dùng không chỉ định layout** — chọn Layout A (Hero Single) làm mặc định
6. **Brand_voice.md hiện đang trống** — bỏ qua cho đến khi có nội dung
7. **Troubleshooting ảnh:** Xem mục 4 trong SOP.md để xử lý các lỗi thường gặp
