# ♻️ Waste Classification Dataset (Global Taxonomy)
(TẬP DATASET CHO CÁC LOẠI RÁC SINH HOẠT)
### 🧩 Built for **SAM2 Segmentation** + 🧠 **Waste Classifier**

Dataset này được tổ chức theo **4 nhóm rác sinh hoạt hàng ngày (waste streams)** phổ biến quốc tế để phục vụ đồ án:
- 🖼️ **Segment Anything 2 (SAM2)**: tách vật thể rác → sinh mask (instance segmentation)
- 🧠 **Classifier**: phân loại rác theo **nhóm lớn (Level A)** hoặc **nhóm nhỏ (Level B)** dựa trên folder label

> ✅ Mục tiêu: Cấu trúc dữ liệu rõ ràng • Dễ mở rộng • Dễ mapping nhãn • Phù hợp triển khai pipeline end-to-end

## 📌 1) Dataset Folder Structure

## <!-- 
    data/

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
        │ └── ♻️ Rác tái chế (giấybìa, nhựa, kim loại, thủy tinh…)/ ## -->

## 🧠 2) Label Strategy (Chiến lược nhãn cho mô hình)

### ✅ Level A — 10 lớp (nhóm lớn)
Phù hợp để demo “phân loại theo dòng thải” (giải thích rất dễ trong báo cáo):

1. 🧪 Hazardous waste    
2. 🌾 Agricultural waste  
3. 🏗️ Industrial waste   
4. 🏙️ MSW (Municipal Solid Waste)  

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

## 👤 Maintainer / Project Info
- **Project:** Waste Sorting — SAM2 Segmentation + Classification  
- **Maintainer:** *(Võ Anh Nhật, Dư Quốc Việt, Võ Huỳnh Anh Tuấn, Trương Hoài Tú)*  
- **Last updated:** *(16/12/2006)*  
