<div align="center">

# Ask Me

### ถามให้ชัด ก่อนสั่งให้ AI ทำ

**Thai-first Agent Skill by Mew Social**

[![Agent Skills](https://img.shields.io/badge/Agent_Skills-Compatible-111827)](https://agentskills.io)
[![Thai First](https://img.shields.io/badge/Language-Thai--first-0F766E)](#)
[![No Scripts](https://img.shields.io/badge/Security-No_scripts-2563EB)](#ความโปร่งใสและความปลอดภัย)
[![MIT License](https://img.shields.io/badge/License-MIT-F59E0B)](LICENSE)

</div>

`Ask Me` คือ Skill สำหรับคนที่รู้ว่าอยากทำอะไร แต่ยังไม่รู้ว่าจะ Prompt อย่างไรให้ครบ

ไม่ต้องเริ่มจาก Prompt ยาว ๆ แค่เล่าไอเดียคร่าว ๆ แล้ว Ask Me จะดู Context ที่มี ถามทีละหนึ่งคำถาม แนะนำคำตอบในทุกจุดสำคัญ และหยุดเมื่อได้ **Working Brief ที่ยืนยันแล้ว** เพื่อใช้เป็น Source of Truth ส่งต่อให้คนหรือ AI Agent ตัวใดก็ได้

```text
ไอเดียที่ยังไม่ชัด
       ↓
ตรวจ Context ที่มีอยู่
       ↓
ถามทีละข้อ + แนะนำคำตอบ
       ↓
Coverage Ledger — หลักฐานว่าครบก่อนสรุป
       ↓
WORKING-BRIEF.md (ยืนยันแล้ว)
       ↓
เลือกเอง: ทำต่อเลย · Handoff · พักไว้
       ↓
Execute Mode — แนะนำโมเดลที่คุ้มค่าต่องาน (ถ้าเลือกทำต่อ)
```

## ใช้กับอะไรได้บ้าง

Ask Me ไม่ผูกกับโมเดลหรือค่ายใดค่ายหนึ่ง ตัว Skill ใช้โครงสร้าง `SKILL.md` ตามแนวทาง [Agent Skills](https://agentskills.io) จึงนำ Workflow เดียวกันไปใช้ได้กับ:

- **Claude:** Claude Chat, Claude Cowork และ Claude Code
- **OpenAI:** ChatGPT Work, Codex app, Codex CLI และ IDE extension
- **Open Agent:** OpenClaw และ Hermes Agent
- **CLI / Coding Agent อื่น:** Cursor, OpenCode, Gemini CLI, GitHub Copilot, Cline และ Agent ที่รองรับ Agent Skills

> การรองรับหมายถึง Logic ของ Skill สามารถพกข้ามแพลตฟอร์มได้ วิธีติดตั้ง วิธีเรียก และสิทธิ์เข้าถึงไฟล์อาจต่างกันตาม Agent และนโยบายของ Workspace

## ติดตั้งแบบเร็วที่สุด

ต้องมี [Node.js](https://nodejs.org/) แล้วเปิด Terminal รันคำสั่งนี้:

```bash
npx skills add mewic/ask-me --skill ask-me -g
```

ตัวติดตั้งจะแสดงรายชื่อ Agent ที่พบในเครื่อง ให้เลือกตัวที่ต้องการใช้

ติดตั้งพร้อมกันใน Claude Code, Codex, OpenClaw และ Hermes Agent:

```bash
npx skills add mewic/ask-me --skill ask-me -g \
  -a claude-code -a codex -a openclaw -a hermes-agent -y
```

ติดตั้งให้ Agent ทุกตัวที่รองรับในเครื่อง:

```bash
npx skills add mewic/ask-me --skill ask-me --agent '*' -g -y
```

หลังติดตั้ง หากยังไม่เห็น Skill ให้ปิดแล้วเปิด Agent หรือเริ่ม Session ใหม่

## ใช้ใน ChatGPT Work / Codex

คำสั่งติดตั้งด้านบนจะติดตั้ง Ask Me เป็น Global Skill สำหรับ Codex และ ChatGPT desktop ที่ใช้ Skill ชุดเดียวกัน จากนั้นเปิดเมนู **Skills** หรือเริ่ม Session ใหม่ แล้วเรียกด้วย `$ask-me` หรือพิมพ์ `ใช้ Ask Me...`

Repository นี้มี [Plugin manifest](.codex-plugin/plugin.json) เตรียมไว้สำหรับการนำ Mew Social Skill ไปใช้ในรูปแบบ Plugin ด้วย การติดตั้งใน ChatGPT Work บนเว็บหรือระดับองค์กรอาจต้องได้รับอนุญาตจาก Workspace และเป็นไปตามขั้นตอนเผยแพร่ Plugin ของ OpenAI

## ติดตั้งใน Claude Chat / Cowork

1. ดาวน์โหลด [`ask-me.zip`](https://github.com/mewic/ask-me/releases/latest/download/ask-me.zip)
2. เปิด Claude แล้วไปที่ **Customize → Skills**
3. กด **+ → Create skill → Upload a skill**
4. เลือกไฟล์ `ask-me.zip` แล้วเปิดใช้งาน Skill

Skill ที่เปิดไว้สามารถใช้ได้ทั้ง Chat และ Cowork ตามสิทธิ์ของบัญชี ดูรายละเอียดได้จาก [คู่มือ Skills ของ Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

## ติดตั้งใน Hermes Agent

ติดตั้งตรงจาก Public GitHub repository ได้ด้วยคำสั่ง:

```bash
hermes skills install mewic/ask-me/skills/ask-me
```

หรือเพิ่ม Mew Social เป็น Skill tap สำหรับติดตั้ง Skill อื่นในอนาคต:

```bash
hermes skills tap add mewic/ask-me
```

## เรียกใช้อย่างไร

เรียกด้วยคำสั่งของ Agent หรือพิมพ์ภาษาธรรมชาติก็ได้:

```text
Ask Me เรื่องออกแบบ Route ทัวร์จีนใหม่
/ask-me ช่วยเคลียร์โจทย์ระบบ CRM สำหรับทีมขาย
$ask-me ก่อนทำเว็บไซต์ร้านไอศกรีม ช่วยถามฉันทีละข้อ
ใช้ Ask Me ทำ Working Brief สำหรับ PDF แนะนำบริการ B2B
```

- Claude Code, OpenClaw และ Hermes Agent มักเรียกด้วย `/ask-me`
- Codex เรียกด้วย `$ask-me` หรือเลือกจากเมนู Skills
- Chat, Cowork และ ChatGPT Work สามารถพิมพ์ว่า `ใช้ Ask Me...` ได้เลย

จากนั้นตอบคำถามทีละข้อ หากไม่แน่ใจ สามารถตอบว่า **“ตามที่แนะนำ”** ได้

## สิ่งที่จะได้รับ

ปลายทางของ Ask Me ไม่ใช่คำตอบสุดท้ายหรือ Deliverable แต่คือ `WORKING-BRIEF.md` ที่ระบุ:

- Outcome ที่ต้องการเพียงเรื่องเดียว
- ปัญหา Context และกลุ่มเป้าหมาย
- สิ่งที่จะส่งมอบ พร้อม Format และช่องทาง
- สิ่งที่อยู่ใน Scope และ Out of Scope
- Requirement ข้อจำกัด และการตัดสินใจสำคัญ
- Success Criteria ที่ตรวจรับได้
- ขั้นตอนถัดไป โดยยังไม่เริ่มลงมือทำ

Working Brief จึงปรับตามคำตอบของผู้ใช้ได้ เช่น:

| งานที่คุย | Working Brief จะเน้น |
|---|---|
| ทัวร์ | ลูกค้า Route ประสบการณ์ ราคา ข้อจำกัด และ Format ของ PDF/เว็บไซต์ |
| ร้านอาหารหรือไอศกรีม | ลูกค้า Offer เมนู ช่องทางขาย Brand Voice และการปฏิบัติงาน |
| B2B | ผู้มีอำนาจตัดสินใจ ปัญหาธุรกิจ Value Proposition ขั้นตอนอนุมัติ และ KPI |
| เว็บไซต์ | ผู้ใช้ หน้าและ Content หลัก Function ขอบเขต เทคนิค และ Acceptance Criteria |
| CRM / LINE Chatbot | Roles, Workflow, Data, Integration, Permission และกรณีผิดพลาด |
| คอนเทนต์ / PDF | Audience, Message, Structure, Tone, CTA, Source และรูปแบบส่งมอบ |

## ใหม่ใน v2

v2 ยกเครื่องข้างในทั้งหมดจาก workflow ภายในที่ Mew Social ใช้ทำงานจริงทุกวัน โดยหน้าตาการใช้งานเดิมไม่เปลี่ยน:

- **สัมภาษณ์ลึกขึ้น** — เดิน Decision Tree จนทุกกิ่งถูกตัดสิน และบังคับถาม 2 เรื่องเสมอ: Deliverable Format และ Success Criteria
- **Coverage Ledger** — ก่อนร่าง Brief ทุกครั้ง Agent ต้องแสดงตารางหลักฐานว่าแต่ละหัวข้อแกนกลาง "ถามแล้ว / เจอใน Context / ไม่เกี่ยวเพราะอะไร" — ปิดปัญหาถามไม่กี่ข้อแล้วรีบสรุป
- **จบ Brief แล้วไม่ตัน** — ยืนยัน Brief เสร็จจะมีเมนู 3 ทางให้เลือกเอง: **ทำต่อเลย** ที่นี่ · **Handoff** รับ Prompt สำเร็จรูปไปวางให้ Agent หรือคนอื่นทำ · **พักไว้** แล้วกลับมาต่อด้วย `/ask-me execute <ไฟล์>`
- **Execute Mode** — ถ้าเลือกทำต่อ Agent จะแตกงานเป็นชิ้น แล้วแนะนำว่าแต่ละชิ้นควรใช้โมเดลไหนถึงคุ้มที่สุด ก่อนเริ่มต้องขออนุมัติแผนเสมอ

### แนะนำโมเดลแบบสัมพัทธ์ — หัวใจของ Execute Mode

ไม่มีสูตรตายตัวว่า "ต้องคุยกับตัวท็อปเสมอ" — จุดตั้งต้นคือโมเดลที่คุณใช้ยืนพื้นอยู่แล้ว ไม่ว่าจะจ่ายแผน $10 หรือ $200:

| ระดับ | Claude | Codex (GPT-5.6) |
|---|---|---|
| Top | Opus | Sol |
| Mid | Sonnet | Terra |
| Small | Haiku | Luna |

Agent จะเทียบ "ลักษณะงาน" กับ "ตัวที่คุณใช้อยู่" แล้วแนะนำ 1 ใน 3 ทิศ:

- **อยู่ตัวเดิม** — งานพอดีมือ หรือเล็กเกินกว่าจะคุ้มสลับ (คุยกับ Terra อยู่ แผนชัดแล้ว ก็ให้ Terra ผลิตต่อเลย)
- **ลดระดับ** — แผนชัดและงานผลิตก้อนใหญ่ ส่งให้ตัวถูกกว่าทำ ประหยัดโควตา (Sonnet→Haiku, Terra→Luna)
- **ยกระดับ** — เฉพาะชิ้นที่เกินมือตัวยืนพื้น ค่อยแนะนำตัวท็อป (คุยกับ Sonnet แล้วเจองาน Architecture ยาก → แนะนำ Opus)

ตารางโมเดลเป็นเพียง Reference — แก้ให้ตรงกับโมเดลที่แผนและเครื่องมือของคุณมีได้เลย เป้าหมายคือได้งานมีคุณภาพโดยวางแผนการใช้โมเดลอย่างคุ้มค่า ไม่ใช่พิธีกรรม

## หนึ่ง Project ใช้ได้หลาย Brief

หนึ่ง Project อาจมีงานต่อเนื่องหลายเดือน แต่ไม่ควรรวมทุกอย่างไว้ใน Working Brief เดียว

```text
Project บริษัททัวร์
├── PROJECT-CONTEXT.md                 บริบทบริษัทระยะยาว
└── briefs/
    ├── 2026-07-ออกแบบ-route-จีน/      Outcome ที่ 1
    │   └── WORKING-BRIEF.md
    └── 2026-08-landing-page-ญี่ปุ่น/  Outcome ที่ 2
        └── WORKING-BRIEF.md
```

- Outcome เดิม คุยต่อหลาย Session ได้
- Outcome ใหม่ ให้เรียก Ask Me แล้วสร้าง Brief ใหม่
- งานที่จบแล้วไม่ถูกนำมาเป็น Requirement ของงานใหม่โดยอัตโนมัติ
- เอกสารบริษัทและ Brand Context แยกจาก Requirement ของแต่ละงาน

## Ask Me ต่างจากการถาม Prompt ปกติอย่างไร

| Prompt ปกติ | Ask Me |
|---|---|
| ผู้ใช้ต้องคิดว่าจะพิมพ์อะไรเอง | เริ่มจากไอเดียสั้น ๆ ได้ |
| AI อาจถามหลายข้อพร้อมกัน | ถามทีละหนึ่งข้อ |
| ให้ตัวเลือกแต่ไม่ช่วยตัดสินใจ | มีคำแนะนำและเหตุผลทุกจุดสำคัญ |
| Context เก่าอาจปนกับงานใหม่ | หนึ่ง Outcome ต่อหนึ่ง Brief |
| AI อาจรีบลงมือทำ | หยุดเมื่อยืนยัน Working Brief |
| คำตอบกระจายอยู่ในแชต | สรุปเป็น Source of Truth ที่ส่งต่อได้ |

## เหมาะกับ Workshop และการสอน

Ask Me ถูกออกแบบให้ผู้เรียนเริ่มใช้งานได้โดยไม่ต้องจำ Prompt Framework จำนวนมาก:

1. เตรียม Folder และใส่ Brand/Context ที่จำเป็น
2. เรียก Ask Me แล้วเล่าโจทย์แบบที่นึกออก
3. ตอบคำถามทีละข้อ หรือเลือก “ตามที่แนะนำ”
4. ตรวจและยืนยัน Working Brief
5. ส่ง Brief ให้ Agent ที่ถนัดงานนั้นลงมือทำต่อ

สามารถใช้ Skill นี้ใน Workshop, บทความ และวิดีโอ YouTube ได้ หากนำไปเผยแพร่ต่อ ฝากอ้างอิง **Ask Me by Mew Social** และลิงก์กลับมาที่ Repository นี้

## ความโปร่งใสและความปลอดภัย

- Skill นี้เป็น Markdown ล้วน ไม่มี Script, Package หรือคำสั่งติดตั้งแอบแฝง
- ตัว Skill ไม่ต้องใช้ API Key และไม่มี Script สำหรับส่งข้อมูลออกไปเอง การประมวลผลของ Agent ยังเป็นไปตามนโยบายของแพลตฟอร์มที่เลือกใช้
- คำสั่งใน Skill กำหนดให้ Agent ตรวจเฉพาะ Context ที่ผู้ใช้ให้สิทธิ์และเกี่ยวข้องกับงาน
- ผู้ใช้สามารถอ่านคำสั่งทั้งหมดได้ที่ [`skills/ask-me/SKILL.md`](skills/ask-me/SKILL.md)
- ควรตรวจสอบ Source ของ Skill ทุกครั้งก่อนติดตั้ง โดยเฉพาะ Agent ที่มีสิทธิ์เข้าถึงไฟล์หรือ Terminal

## แนวคิดและเครดิต

Workflow นี้ได้รับแรงบันดาลใจจาก [`grill-me`](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me), [`grilling`](https://github.com/mattpocock/skills/tree/main/skills/productivity/grilling) และ [`grill-with-docs`](https://github.com/mattpocock/skills/tree/main/skills/engineering/grill-with-docs) ของ [Matt Pocock](https://github.com/mattpocock/skills) ภายใต้ MIT License

Ask Me ดัดแปลงให้เหมาะกับผู้เรียนไทยและงานธุรกิจหลายรูปแบบ โดยเพิ่ม Working Brief, Stop Condition, การแยก Project Context ออกจาก Brief และกติกาหนึ่ง Outcome ต่อหนึ่ง Brief

ส่วน Execute Mode และการแนะนำโมเดลแบบสัมพัทธ์ใน v2 ต่อยอดจาก Kickoff Pipeline ภายในที่ Mew Social ใช้ทำงานจริง โดยปรับให้เป็นกลางต่อทุกค่ายโมเดลและทุกระดับแผนราคา

## License

[MIT](LICENSE) — ใช้งาน ดัดแปลง และนำไปสอนได้ โดยคงข้อความลิขสิทธิ์และ License ตามเงื่อนไข

---

สร้างโดย **Mew Social** — เพื่อให้คนทำงานร่วมกับ AI ได้ชัดขึ้น โดยไม่ต้องเริ่มจาก Prompt ที่สมบูรณ์แบบ
