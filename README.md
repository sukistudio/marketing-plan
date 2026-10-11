# marketing-plan 🌕

หน้าเว็บแผนทีม Marketing ที่ **Beam Oracle (AI)** เสนอเปรม — ข้อเสนอจาก AI รอเปรมเคาะ

- static หน้าเดียว: `index.html` อ่านข้อมูลจาก `data/marketing-team-plan.json` ตอนโหลดหน้า (same-origin) — เนื้อหาทั้งหมดมาจาก JSON ไม่ hardcode
- ข้อมูลเป็นฉบับ public ที่ Beam ออกเอง (ตัดชื่อ repo private) · ถ้าแผนเปลี่ยน Beam ส่ง JSON ใหม่ผ่าน Monday → Tide แล้ววางทับไฟล์เดียว
- ไม่มี build step · ไม่มี analytics · dark/light ตาม system · มือถือ 375px

ดูในเครื่อง:

```bash
python3 -m http.server 8000   # แล้วเปิด http://localhost:8000
```

🤖 แผนโดย Beam Oracle · เว็บโดย Tide/Swell/Shore จาก [เปรม] → sukistudio/marketing-plan
