# marketing-plan 🌕

หน้าเว็บแผนทีม Marketing ที่ **Beam Oracle (AI)** เสนอเปรม — ข้อเสนอจาก AI รอเปรมเคาะ

- static หน้าเดียว: `index.html` อ่านข้อมูลจาก `data/marketing-team-plan.json` ตอนโหลดหน้า (same-origin) — เนื้อหาทั้งหมดมาจาก JSON ไม่ hardcode
- ข้อมูลเป็นฉบับ public ที่ Beam ออกเอง (ตัดชื่อ repo private) · ถ้าแผนเปลี่ยน Beam ส่ง JSON ใหม่ผ่าน Monday → Tide แล้ววางทับไฟล์เดียว
- ไม่มี build step · ไม่มี analytics · dark/light ตาม system · มือถือ 375px

## ข้อมูลต่างจาก `.public.json` ของ Beam (redact 2026-10-11 — Monday เคาะ)

`data/marketing-team-plan.json` = `marketing/plan/2026-10_marketing-team-plan.public.json` (v1) **แทนข้อความ `sukistudio/marketing` → `repo ภายในของทีม Marketing (private)` ทั้ง 5 ที่** เพื่อไม่เปิดชื่อ repo private · เป็นการ redact ไม่ใช่แก้เนื้อหา · ชื่อ `*-oracle` คงไว้ · Beam จะออก `.public.json` v2 ตามมา แล้ววางทับไฟล์นี้ได้เลย

| path ใน JSON | เดิม → ใหม่ |
|---|---|
| `meta.signature` | `… → sukistudio/marketing` → `… → repo ภายในของทีม Marketing (private)` |
| `team.rules[4]` | `… ใน repo sukistudio/marketing` → `… ใน repo ภายในของทีม Marketing (private)` — ตัดคำ "repo" ที่ซ้ำจากการแทนตรงตัว (artifact ของ redact, Tide อนุมัติ) |
| `team.repo.name` | `sukistudio/marketing` → `repo ภายในของทีม Marketing (private)` |
| `channels[0].signature` | `… → sukistudio/marketing (ใน description)` → `… → repo ภายในของทีม Marketing (private) (ใน description)` |
| `rule6_policy.articles[1].signature_full` | `… → sukistudio/marketing` → `… → repo ภายในของทีม Marketing (private)` |

ดูในเครื่อง:

```bash
python3 -m http.server 8000   # แล้วเปิด http://localhost:8000
```

🤖 แผนโดย Beam Oracle · เว็บโดย Tide/Swell/Shore จาก [เปรม] → sukistudio/marketing-plan
