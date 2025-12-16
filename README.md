# ♻️ Waste Classification Dataset (Global Taxonomy)  
### 🧩 Built for **SAM2 Segmentation** + 🧠 **Waste Classifier**

Dataset này được tổ chức theo **10 nhóm rác (waste streams)** phổ biến quốc tế để phục vụ đồ án:
- 🖼️ **Segment Anything 2 (SAM2)**: tách vật thể rác → sinh mask (instance segmentation)
- 🧠 **Classifier**: phân loại rác theo **nhóm lớn (Level A)** hoặc **nhóm nhỏ (Level B)** dựa trên folder label

> ✅ Mục tiêu: Cấu trúc dữ liệu rõ ràng • Dễ mở rộng • Dễ mapping nhãn • Phù hợp triển khai pipeline end-to-end

## 📌 1) Dataset Folder Structure (Theo đúng cây thư mục hiện tại)

> ⚠️ Lưu ý: Giữ nguyên tên folder tiếng Việt + tiếng Anh trong ngoặc như bạn đã tạo.

data/
├── 🧪 Bùn thải & chất thải từ hệ thống nước thải (Wastewater sludge)/
│ ├── 🏭 Bùn từ trạm xử lý nước thải đô thịkhu công nghiệp/
│ └── 🍳 Cặn từ bẫy mỡ nhà hàng/
├── ⛏️ Chất thải khai khoáng (Mining waste)/
│ └── 🪨 Đất đá thải, quặng đuôi, bùn tuyển…/
├── ☢️ Chất thải phóng xạ (Radioactive waste)/
│ └── 🧫 Nguồn kín (sealed sources), chất thải mức thấp, vật liệu nhiễm xạ…/
├── 🌾 Rác nông nghiệp (Agricultural waste)/
│ ├── 🧴 Bao bì hóa chất nông nghiệp/
│ ├── 🧵 Màng phủ nông nghiệp, ống tưới (nhựa)/
│ └── 🌿 Phụ phẩm hữu cơ rơm rạ, vỏ trấu/
├── 🏗️ Rác thải công nghiệp (Industrial waste)/
│ ├── ✅ Không nguy hại (phế liệu bao bì, bùn không độc)/
│ └── ⚠️ Nguy hại (dung môi, bùn mạ, hóa chất độc…)/
├── ⚠️ Rác thải nguy hại (Hazardous waste)/
│ ├── 🔥 Dễ cháy (Ignitable)/
│ ├── 💥 Phản ứng mạnh (Reactive)/
│ ├── 🧪 Ăn mòn (Corrosive)/
│ └── ☠️ Độc (Toxic)/
├── 🏙️ Rác thải sinh hoạt đô thị (Municipal Solid Waste – MSW)/
│ ├── 🧻 Rác còn lạikhó tái chế (tãbỉm, đồ vệ sinh cá nhân)/
│ ├── 🛋️ Rác cồng kềnh (nệm, sofa, đồ gỗ lớn…)/
│ ├── 🍌 Rác hữu cơ (thực phẩm thừa, vỏ rau củ, bã tràcà phê…; lá câycỏ cắt tỉa)/
│ └── ♻️ Rác tái chế (giấybìa, nhựa, kim loại, thủy tinh…)/
├── 🏥 Rác thải y tế (Health-care waste Medical waste)/
│ ├── 🧪 Chemical (hóa chất)/
│ ├── 🧬 Cytotoxic (thuốc gây độc tế bào)/
│ ├── 🦠 Infectious (lây nhiễm)/
│ ├── 🫁 Pathologicalanatomical (mô, bộ phận cơ thể)/
│ ├── 💊 Pharmaceutical (thuốc quá hạnthu hồi)/
│ ├── ☢️ Radioactive (phóng xạ)/
│ └── 🩸 Sharps (vật sắc nhọn kim tiêm, lưỡi dao mổ…)/
├── 🏗️ Rác xây dựng & phá dỡ (Construction & Demolition – C&D)/
│ ├── 🧱 Bê tông, gỗ, nhựa đườngasphalt (đường & mái), thạch caogypsum (vách drywall)/
│ ├── 🚪 Cấu kiện tháo dỡ tái sử dụng (cửa, cửa sổ, thiết bị ống nước…)/
│ ├── 🔩 Kim loại, gạch, kính, nhựa/
│ └── 🌍 Đất đácây gốc từ san lấp mặt bằng/
└── 💻 Rác điện tử (E-waste WEEE)/
├── 🖥️ Màn hìnhmonitor & thiết bị có màn hình lớn/
├── 📱 Thiết bị CNTT & viễn thông cỡ nhỏ/
├── 🧺 Thiết bị cỡ lớn/
├── 🔌 Thiết bị cỡ nhỏ/
├── ❄️ Thiết bị trao đổi nhiệt (tủ lạnh, máy lạnh…)/
└── 💡 Đèn (lamps)/

## 🧠 2) Label Strategy (Chiến lược nhãn cho mô hình)

### ✅ Level A — 10 lớp (nhóm lớn)
Phù hợp để demo “phân loại theo dòng thải” (giải thích rất dễ trong báo cáo):

1. 🧪 Wastewater sludge  
2. ⛏️ Mining waste  
3. ☢️ Radioactive waste  
4. 🌾 Agricultural waste  
5. 🏗️ Industrial waste  
6. ⚠️ Hazardous waste  
7. 🏙️ MSW (Municipal Solid Waste)  
8. 🏥 Medical waste  
9. 🏗️ C&D (Construction & Demolition)  
10. 💻 E-waste (WEEE)

### 🎯 Level B — lớp chi tiết (theo folder con)
Phù hợp để nâng cao độ “xịn”:
- 🏙️ MSW: hữu cơ / tái chế / cồng kềnh / còn lại  
- 🏥 Medical: sharps / infectious / pharmaceutical / ...  
- ⚠️ Hazardous: ignitable / corrosive / reactive / toxic  
- 💻 E-waste: screens / lamps / heat exchange / ...

> 💡 Khuyến nghị đồ án:
- **Bắt đầu** với Level A để pipeline chạy ổn và demo rõ ràng  
- **Sau đó** mở rộng Level B cho 2–4 nhóm trọng điểm (MSW + Medical + E-waste + Hazardous)

---

## 🗂️ 3) Data Content Rules (Quy ước dữ liệu trong mỗi folder)

### 🖼️ 3.1 Supported Formats
- Images: `.jpg`, `.jpeg`, `.png`

### 🏷️ 3.2 File Naming Convention (khuyến nghị)
Đặt tên theo format: <group><subgroup><source>__<id>.jpg

Ví dụ:
- `msw__organics__phone__000001.jpg`
- `medical__sharps__hospital__000045.jpg`
- `ewaste__screens__web__000210.jpg`

## 🧩 4) SAM2 → Mask → Crop → Classifier (Pipeline chuẩn đồ án)

### Step 1 — 📥 Collect & Organize
- Bỏ ảnh/video vào đúng folder (theo taxonomy ở mục 1)

### Step 2 — ✂️ Segment with SAM2
- SAM2 chạy theo chế độ “segment everything” hoặc prompt-based (point/box)
- Ảnh nhiều vật thể → sinh **nhiều instance masks**

### Step 3 — 🧷 Crop Objects from Masks
- Dùng `mask + bbox` để crop từng vật thể ra ảnh riêng
- Tuỳ chọn: set nền ngoài mask thành trắng/đen để classifier học tốt hơn

### Step 4 — 🧠 Train Classifier
Có 2 hướng:
- **Train từ ảnh gốc** (nhanh, nhưng nhiễu nền)
- **Train từ object crops** (chuẩn pipeline SAM2 + tăng accuracy)

---

## 📦 5) Recommended Output Structure (khuyến nghị cho kết quả xử lý)

> Nếu muốn chuyên nghiệp hơn, tạo folder output riêng để không lẫn với `data/`.

outputs/
├── 🧩 masks/ # mask PNG theo từng ảnh (instance-level)
├── 🖍️ overlays/ # ảnh preview (mask overlay)
├── ✂️ crops/ # object crops dùng cho classifier
└── 📊 reports/ # confusion matrix, metrics, logs

## ✅ 6) Data Quality Checklist (để dataset sạch)

- 🔍 Ảnh rõ vật thể, hạn chế nhòe/mờ
- 🌗 Tránh ảnh quá tối/điều kiện ánh sáng cực xấu
- 🧬 Tránh ảnh trùng lặp (near-duplicate)
- 🧩 Ảnh nhiều vật thể: ưu tiên ảnh rác “tách biệt” để mask không dính
- ⚠️ Nhóm y tế/phóng xạ/nguy hại: ưu tiên ảnh minh hoạ rõ, tránh nội dung khó nhìn

## 📝 7) Notes for Report (Gợi ý viết báo cáo)
Khi viết báo cáo, nên nêu rõ:
- Bạn train theo **Level A** hay **Level B**
- Bạn dùng SAM2 để sinh mask & crop như thế nào
- Vì sao “crop theo mask” giúp tăng chất lượng phân loại (giảm nhiễu nền)
- Dataset lấy từ đâu (nếu có) + license

## 👤 Maintainer / Project Info
- **Project:** Waste Sorting — SAM2 Segmentation + Classification  
- **Maintainer:** *(Võ Anh Nhật, Dư Quốc Việt, Võ Huỳnh Anh Tuấn, Trương Hoài Tú)*  
- **Last updated:** *(16/12/2006)*  
