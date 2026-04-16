# Visual Guideline — LUBYLAB Product Marketing Banners
# Hướng Dẫn Visual — Banner Marketing Sản Phẩm LUBYLAB

> **Purpose / Mục đích:** This document is a strict instruction for Claude Code when generating marketing banners / visuals using LUBYLAB product images provided by the user.
>
> Tài liệu này là chỉ dẫn bắt buộc cho Claude Code khi tạo banner/visual marketing sử dụng ảnh sản phẩm LUBYLAB do người dùng cung cấp.

---

## 🇻🇳 TIẾNG VIỆT

### 1. Nguyên tắc TỐI THƯỢNG — KHÔNG BAO GIỜ được vi phạm

Ảnh gốc của sản phẩm là tài sản thương hiệu. Khi xử lý ảnh sản phẩm, Claude Code **PHẢI** tuân thủ tuyệt đối các quy tắc sau:

#### ❌ TUYỆT ĐỐI KHÔNG:

1. **KHÔNG được thay đổi label/nhãn sản phẩm**
   - Không chỉnh sửa, xóa, che, hay làm mờ bất kỳ chữ nào trên nhãn
   - Không dịch nhãn sang ngôn ngữ khác
   - Không thay đổi font chữ, kích thước chữ, vị trí chữ trên nhãn
   - Không thêm bất kỳ text nào lên bao bì sản phẩm
   - Không thay đổi số seri, mã vạch, thành phần, hạn sử dụng

2. **KHÔNG được thay đổi màu sắc bao bì**
   - Giữ nguyên 100% hex color của bao bì, nắp, thân chai
   - Không tăng/giảm saturation, hue, brightness của chính sản phẩm
   - Không áp filter màu (sepia, warm, cool, v.v.) lên sản phẩm
   - Nếu ảnh gốc có màu xanh lá → phải giữ đúng màu xanh lá đó

3. **KHÔNG được thay đổi hình dáng chai/lọ**
   - Không biến dạng, kéo giãn, nén ngang/dọc
   - Không thay đổi thiết kế vật lý (nắp, vòi, pump, v.v.)
   - Không "tái tạo lại" sản phẩm bằng AI — phải dùng ảnh gốc

4. **KHÔNG được thay đổi logo thương hiệu**
   - Logo LUBYLAB (루비랩) phải giữ nguyên 100%
   - Không đổi màu, không xoay, không thêm hiệu ứng
   - Không che hoặc cắt logo khi crop ảnh

5. **KHÔNG được thay đổi tỷ lệ / kích thước sản phẩm**
   - Giữ đúng aspect ratio gốc của sản phẩm
   - Không stretch, squeeze, skew
   - Khi scale: chỉ scale đồng đều (uniform scaling), không bao giờ non-uniform

---

### 2. Những gì ĐƯỢC PHÉP thay đổi

#### ✅ ĐƯỢC PHÉP:

- Thay đổi **background** (nền) phía sau sản phẩm
- Thêm **text marketing** bên ngoài sản phẩm (headline, CTA, giá, v.v.)
- Thêm **decorative elements** (hoa văn, đường viền, icon) xung quanh
- Thêm **shadow / reflection** cho sản phẩm để hài hòa với background
- **Crop** khung hình tổng thể (miễn là không cắt vào sản phẩm/label/logo)
- Điều chỉnh **ánh sáng chung của scene** (không đụng vào sản phẩm)
- Thêm **layout effects** như gradient, blur phía sau sản phẩm

---

### 3. Quy trình bắt buộc trước khi tạo banner

Claude Code **PHẢI** thực hiện các bước sau theo thứ tự:

```
BƯỚC 1: Nhận ảnh gốc sản phẩm từ người dùng
BƯỚC 2: Phân tích kỹ ảnh gốc:
        - Ghi nhận màu bao bì (hex code nếu có thể)
        - Ghi nhận toàn bộ text có trên label
        - Ghi nhận tỷ lệ chai/lọ
        - Ghi nhận vị trí logo
BƯỚC 3: Tách sản phẩm ra khỏi background gốc (nếu cần)
        → KHÔNG retouch vào sản phẩm khi tách
BƯỚC 4: Tạo background mới + layout marketing
BƯỚC 5: Đặt ảnh sản phẩm GỐC (không qua AI regenerate) vào layout
BƯỚC 6: So sánh banner cuối với ảnh gốc:
        - Label có bị thay đổi không?
        - Màu sắc sản phẩm có đúng không?
        - Hình dáng có bị méo không?
        - Logo có bị che/đổi không?
        - Tỷ lệ có đúng không?
BƯỚC 7: Nếu bất kỳ điểm nào ở BƯỚC 6 sai → LÀM LẠI
```

---

### 4. Checklist tự kiểm tra (MANDATORY SELF-CHECK)

Trước khi xuất file cuối cùng, Claude Code **BẮT BUỘC** trả lời "CÓ" cho tất cả các câu sau:

- [ ] Label trên sản phẩm giống 100% với ảnh gốc?
- [ ] Màu bao bì giữ nguyên 100% với ảnh gốc?
- [ ] Hình dáng chai/lọ không bị biến dạng?
- [ ] Logo LUBYLAB rõ ràng, nguyên bản?
- [ ] Tỷ lệ sản phẩm đúng với ảnh gốc?
- [ ] Không có element marketing nào đè lên label/logo?
- [ ] Ảnh sản phẩm KHÔNG phải do AI tái tạo?

**Nếu có BẤT KỲ câu nào trả lời "KHÔNG" → DỪNG LẠI, làm lại từ đầu.**

---

### 5. Xử lý tình huống đặc biệt

| Tình huống | Cách xử lý ĐÚNG |
|---|---|
| Ảnh gốc có background rối | Tách sản phẩm ra, KHÔNG retouch sản phẩm |
| Ảnh gốc bị mờ một phần | Báo cho user, YÊU CẦU ảnh chất lượng cao hơn |
| Label có chữ Hàn không đọc được | Giữ nguyên, KHÔNG dịch, KHÔNG thay thế |
| Logo bị khuất một phần | Báo cho user, KHÔNG tự vẽ lại logo |
| User yêu cầu "làm đẹp sản phẩm" | Từ chối — chỉ có thể làm đẹp scene xung quanh |

---

## 🇬🇧 ENGLISH

### 1. TOP PRIORITY Rules — NEVER to be violated

The original product image is brand property. When processing product images, Claude Code **MUST** strictly follow these rules:

#### ❌ STRICTLY FORBIDDEN:

1. **DO NOT modify product label**
   - Do not edit, erase, cover, or blur any text on the label
   - Do not translate the label to another language
   - Do not change font, size, or position of text on the label
   - Do not add any text onto the product packaging
   - Do not alter serial numbers, barcodes, ingredients, or expiry dates

2. **DO NOT change packaging colors**
   - Preserve 100% of the original hex colors of the packaging, cap, and bottle
   - Do not adjust saturation, hue, or brightness of the product itself
   - Do not apply color filters (sepia, warm, cool, etc.) on the product
   - If the original is green → keep the exact same green

3. **DO NOT change the bottle/jar shape**
   - No deformation, stretching, or compression
   - Do not modify physical design (cap, nozzle, pump, etc.)
   - Do not "regenerate" the product with AI — must use the original image

4. **DO NOT change the brand logo**
   - LUBYLAB logo (루비랩) must remain 100% intact
   - Do not recolor, rotate, or add effects
   - Do not crop or obscure the logo when framing

5. **DO NOT change product proportions / size**
   - Preserve the original aspect ratio
   - No stretching, squeezing, or skewing
   - When scaling: uniform scaling only, never non-uniform

---

### 2. What IS ALLOWED to change

#### ✅ PERMITTED:

- Change the **background** behind the product
- Add **marketing text** outside the product (headline, CTA, price, etc.)
- Add **decorative elements** (patterns, borders, icons) around it
- Add **shadow / reflection** to blend the product with the background
- **Crop** the overall frame (as long as it doesn't cut into product/label/logo)
- Adjust the **overall scene lighting** (without touching the product)
- Add **layout effects** like gradients or blur behind the product

---

### 3. Mandatory workflow before creating a banner

Claude Code **MUST** follow these steps in order:

```
STEP 1: Receive the original product image from user
STEP 2: Analyze the original carefully:
        - Record packaging colors (hex codes if possible)
        - Record all text on the label
        - Record bottle/jar proportions
        - Record logo position
STEP 3: Extract product from original background (if needed)
        → DO NOT retouch the product during extraction
STEP 4: Create new background + marketing layout
STEP 5: Place the ORIGINAL product image (not AI-regenerated) into the layout
STEP 6: Compare final banner with the original:
        - Is the label unchanged?
        - Are product colors correct?
        - Is the shape undistorted?
        - Is the logo intact?
        - Are proportions correct?
STEP 7: If ANY point in STEP 6 fails → REDO
```

---

### 4. Mandatory Self-Check

Before exporting the final file, Claude Code **MUST** answer "YES" to every question below:

- [ ] Is the product label 100% identical to the original?
- [ ] Is the packaging color 100% preserved from the original?
- [ ] Is the bottle/jar shape undistorted?
- [ ] Is the LUBYLAB logo clear and unchanged?
- [ ] Is the product proportion correct vs original?
- [ ] No marketing element overlapping the label/logo?
- [ ] Is the product image NOT AI-regenerated?

**If ANY answer is "NO" → STOP and redo from scratch.**

---

### 5. Special case handling

| Situation | CORRECT handling |
|---|---|
| Original has busy background | Extract the product, DO NOT retouch it |
| Original is partially blurry | Notify user, REQUEST a higher-quality image |
| Label has unreadable Korean text | Keep as-is, DO NOT translate or replace |
| Logo partially obscured | Notify user, DO NOT redraw the logo |
| User asks to "beautify the product" | Refuse — only the surrounding scene may be beautified |

---

## 📌 FINAL NOTE / LƯU Ý CUỐI

> **VI:** Nguyên tắc vàng: Sản phẩm là bất khả xâm phạm. Tất cả sự sáng tạo phải diễn ra XUNG QUANH sản phẩm, không phải TRÊN sản phẩm.
>
> **EN:** Golden rule: The product is untouchable. All creativity must happen AROUND the product, never ON the product.

---

**Version:** 1.0
**Applies to:** All LUBYLAB product marketing banners
**Áp dụng cho:** Tất cả banner marketing sản phẩm LUBYLAB