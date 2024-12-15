- 👋 Hi, I’m @adunraharza
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
adunraharza/adunraharza is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from fpdf import FPDF

class PDF(FPDF):
    def header(self):
        self.set_font('Arial', 'B', 12)
        self.cell(0, 10, 'Tabel Kebenaran', 0, 1, 'C')

    def chapter_title(self, title):
        self.set_font('Arial', 'B', 12)
        self.cell(0, 10, title, 0, 1, 'L')
        self.ln(5)

    def chapter_body(self, body):
        self.set_font('Arial', '', 12)
        self.multi_cell(0, 10, body)
        self.ln()

pdf = PDF()
pdf.add_page()

# Tabel Kebenaran 1
pdf.chapter_title('1. (pvq)^~p')
table1 = """| p | q | p v q | ~p | (p v q) ^ ~p |
|---|---|---|---|---|
| T | T | T | F | F |
| T | F | T | F | F |
| F | T | T | T | T |
| F | F | F | T | F |"""
pdf.chapter_body(table1)

# Tabel Kebenaran 2
pdf.chapter_title('2. (p^q) v (qvr)')
table2 = """| p | q | r | p ^ q | q v r | (p ^ q) v (q v r) |
|---|---|---|---|---|---|
| T | T | T | T | T | T |
| T | T | F | T | T | T |
| T | F | T | F | T | T |
| T | F | F | F | F | F |
| F | T | T | F | T | T |
| F | T | F | F | T | T |
| F | F | T | F | T | T |
| F | F | F | F | F | F |"""
pdf.chapter_body(table2)

# Tabel Kebenaran 3
pdf.chapter_title('3. (pvq) vp')
table3 = """| p | q | p v q | (p v q) v p |
|---|---|---|---|
| T | T | T | T |
| T | F | T | T |
| F | T | T | T |
| F | F | F | F |"""
pdf.chapter_body(table3)

pdf.output('tabel_kebenaran.pdf')
