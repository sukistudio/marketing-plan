# marketing-plan 🌕

หน้าเว็บแผนทีม Marketing ที่ **Beam Oracle (AI)** เสนอเปรม — ข้อเสนอจาก AI รอเปรมเคาะ

- static หน้าเดียว: `index.html` อ่านข้อมูลจาก `data/marketing-team-plan.json` ตอนโหลดหน้า (same-origin) — เนื้อหาทั้งหมดมาจาก JSON ไม่ hardcode
- ข้อมูลเป็นฉบับ public ที่ Beam ออกเอง (ตัดชื่อ repo private) — ปัจจุบัน v6 (เคาะ A แล้ว · ไม่เปิดเผยชื่อแบรนด์จนจดทะเบียนเสร็จ) · ถ้าแผนเปลี่ยน Beam ส่ง JSON ใหม่ผ่าน Monday → Tide แล้ววางทับไฟล์เดียว
- ไม่มี build step · ไม่มี analytics · dark/light ตาม system · มือถือ 375px

## ข้อมูล = `.public.json` v6 ของ Beam (ทุก byte)

`data/marketing-team-plan.json` = `marketing/plan/2026-10_marketing-team-plan.public.json` **v6 ของ Beam (marketing@44c827e · `meta.version` 1.3.0) ไม่แก้สักตัวอักษร** — Beam redact เองครบ (ชื่อ repo private 5 รายการ + ชื่อ repo ของทีม Marketing 5 ที่) และเพิ่มผลการเคาะ (`decision`, `meta.status = decided`, `options[].decided`, `questions_for_prem[].answer`, `recommendation.outcome`; v6 เพิ่ม `decision.brand` / `niche` / `first_batch`) ซึ่งหน้าเว็บ render ให้

ประวัติ (Nothing is Deleted): ก่อนหน้านี้ PR นี้เคย redact เองบน v1 — แทน `sukistudio/marketing` 5 ที่ และตัดคำ "repo" ซ้ำใน `team.rules[4]` (Monday/Tide เคาะ) · v2 ของ Beam แทนที่ทั้งหมด (v2 ยังมี "repo repo" ใน `team.rules[4]`) → v3 (marketing@7a1170e) Beam แก้คำซ้ำนั้นเอง → v4 (marketing@c48a55d) Glow/Pulse เป็น active (เกิด 2026-10-11) → v6 (marketing@44c827e, 1.3.0) ตัดชื่อแบรนด์/โดเมน/ช่องออก แสดงเป็น "ชื่อแบรนด์: เคาะแล้ว 2026-10-11 (รอจดทะเบียน)" (กฎ Monday: ห้ามชื่อแบรนด์จริงบนหน้า public จนกว่าจะจดทะเบียน) · v5 ไม่เคยขึ้นเว็บนี้

## URL + deploy (2 project บน Vercel · scope `sukistudios-projects`)

| URL | project | มาจาก |
|---|---|---|
| **https://monday-marketing-plan.vercel.app** (หลัก ตั้งแต่ 2026-10-12 · คู่กับ monday-team-chart) | `monday-marketing-plan` | root ของ repo (`index.html` + `data/` — `.vercelignore` ส่งแค่ 2 อย่างนี้ `redirect/` ไม่ขึ้น) |
| https://marketing-team-plan.vercel.app (เดิม) → **redirect ถาวร** ไป URL หลักทุก path | `marketing-team-plan` | `redirect/` (`vercel.json` + `index.html` สำรองกรณี redirect ไม่ทำงาน) |

```bash
# หน้าหลัก — ที่ root ของ repo (main)
vercel link --yes --scope sukistudios-projects --project monday-marketing-plan
vercel --prod --yes > /tmp/monday-marketing-plan.txt 2>&1; grep -o 'dpl_[A-Za-z0-9]*' /tmp/monday-marketing-plan.txt | head -1
# redirect (แก้แค่เมื่อ URL หลักเปลี่ยน)
cd redirect && vercel link --yes --scope sukistudios-projects --project marketing-team-plan
vercel --prod --yes > /tmp/marketing-team-plan.txt 2>&1; grep -o 'dpl_[A-Za-z0-9]*' /tmp/marketing-team-plan.txt | head -1
curl -sI https://marketing-team-plan.vercel.app/ | grep -iE '^(HTTP|location)'   # 308 + location: https://monday-marketing-plan.vercel.app/
```

- `.vercel/` (ผล `vercel link`) อยู่ใน `.gitignore` ทั้ง root และ `redirect/` — ห้าม commit · ทั้งสอง project เป็น public ห้ามแตะ Deployment Protection
- deploy เก็บ output ลงไฟล์แล้ว grep id ครั้งเดียว (ไม่ deploy ซ้ำเพื่อดู output)

ดูในเครื่อง:

```bash
python3 -m http.server 8000   # แล้วเปิด http://localhost:8000
```

🤖 แผนโดย Beam Oracle · เว็บโดย Tide/Swell/Shore จาก [เปรม] → sukistudio/marketing-plan
