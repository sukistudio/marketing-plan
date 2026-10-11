# marketing-plan 🌕

หน้าเว็บแผนทีม Marketing ที่ **Beam Oracle (AI)** เสนอเปรม — ข้อเสนอจาก AI รอเปรมเคาะ

- static หน้าเดียว: `index.html` อ่านข้อมูลจาก `data/marketing-team-plan.json` ตอนโหลดหน้า (same-origin) — เนื้อหาทั้งหมดมาจาก JSON ไม่ hardcode
- ข้อมูลเป็นฉบับ public ที่ Beam ออกเอง (ตัดชื่อ repo private) — ปัจจุบัน v3 (เคาะ A แล้ว) · ถ้าแผนเปลี่ยน Beam ส่ง JSON ใหม่ผ่าน Monday → Tide แล้ววางทับไฟล์เดียว
- ไม่มี build step · ไม่มี analytics · dark/light ตาม system · มือถือ 375px

## ข้อมูล = `.public.json` v3 ของ Beam (ทุก byte)

`data/marketing-team-plan.json` = `marketing/plan/2026-10_marketing-team-plan.public.json` **v3 ของ Beam (marketing@7a1170e · `meta.version` 1.1.0) ไม่แก้สักตัวอักษร** — Beam redact เองครบ (ชื่อ repo private 5 รายการ + ชื่อ repo ของทีม Marketing 5 ที่) และเพิ่มผลการเคาะ (`decision`, `meta.status = decided`, `options[].decided`, `questions_for_prem[].answer`, `recommendation.outcome`) ซึ่งหน้าเว็บ render ให้

ประวัติ (Nothing is Deleted): ก่อนหน้านี้ PR นี้เคย redact เองบน v1 — แทน `sukistudio/marketing` 5 ที่ และตัดคำ "repo" ซ้ำใน `team.rules[4]` (Monday/Tide เคาะ) · v2 ของ Beam แทนที่ทั้งหมด (v2 ยังมี "repo repo" ใน `team.rules[4]`) → v3 Beam แก้คำซ้ำนั้นเองแล้ว

ดูในเครื่อง:

```bash
python3 -m http.server 8000   # แล้วเปิด http://localhost:8000
```

🤖 แผนโดย Beam Oracle · เว็บโดย Tide/Swell/Shore จาก [เปรม] → sukistudio/marketing-plan
