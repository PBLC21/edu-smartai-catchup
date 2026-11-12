# Edu-SmartAI Catch-Up

Free, bilingual (English/Spanish) catch-up practice apps for Texas students, K–12 Math and Language Arts, aligned to the TEKS and STAAR.

**Live site:** https://edu-smartai-catchup.netlify.app/

Every app follows the same template and design:

| Stage | What the student does |
|---|---|
| **Quick check** | A short diagnostic, one question per readiness standard, that builds a practice order from the gaps it finds. |
| **1. Learn** | A short explanation, key words in English and Spanish, the most common mistake, and a worked example revealed one step at a time. |
| **2. Guided practice** | A new problem broken into small steps, with a hint after one miss and the worked step after two. |
| **3. On my own** | Unlimited generated problems. Three correct in a row marks the skill as mastered. |

## Apps

| Subject | Level | Link | Status |
|---|---|---|---|
| Math | Grade 3 | [/math/grade-3/](https://edu-smartai-catchup.netlify.app/math/grade-3/) | Live |
| Math | Grade 8 | [/math/grade-8/](https://edu-smartai-catchup.netlify.app/math/grade-8/) | Live |
| Language Arts | Grade 3 | [/la/grade-3/](https://edu-smartai-catchup.netlify.app/la/grade-3/) | Live |
| Language Arts | Grade 4 | [/la/grade-4/](https://edu-smartai-catchup.netlify.app/la/grade-4/) | Live |

## Folder structure

```
/
├── index.html          Landing page listing every subject and grade
├── 404.html            Shown for any address that doesn't exist
├── netlify.toml        Netlify settings (no build step, headers, short links)
├── README.md
├── math/
│   ├── grade-8/index.html
│   ├── grade-4/index.html      (future)
│   └── algebra-1/index.html    (future)
└── la/
    ├── grade-4/index.html      (future)
    └── english-1/index.html    (future)
```

### Naming rules (keep these exactly, or links will break)

- **Subjects:** `math` and `la`.
- **Grades K–8:** `k`, `grade-1` … `grade-8`.
- **High school is by course, not grade,** because the TEKS and STAAR EOC are course-based:
  - Math: `algebra-1`, `geometry`, `algebra-2`
  - Language Arts: `english-1`, `english-2`, `english-3`, `english-4`
- Lowercase only, hyphens instead of spaces. Each app is a single `index.html` inside its folder.

## Adding a new app

1. **Create the folder** with the correct name (for example `math/grade-4/`) and put the app's `index.html` inside.
2. **Give the app its own saved-progress key.** All apps share one website, so each one must save under a unique name:
   `catchup.<subject>.<level>.v1` (for example `catchup.math.grade-4.v1`). Reusing a key would mix students' progress between apps.
3. **List it on the landing page.** In `/index.html`, add the path to the `LIVE` list near the top of the script:
   ```js
   const LIVE = [
     'math/grade-8',
     'math/grade-4',
   ];
   ```
4. **Optional short link.** In `netlify.toml`, add a redirect such as `/math4` → `/math/grade-4/`.
5. **Upload all the changed files in one commit.** Netlify redeploys automatically after each commit.

## Deploying

- Hosted on **Netlify**, connected to this GitHub repository. Every commit to `main` publishes the site within a minute or two.
- Check a deploy in Netlify under **Deploys**. A failed or stuck deploy shows there with a log.
- To undo a bad change, open an earlier deploy in Netlify and choose **Publish deploy**.

## Embedding in Google Sites

**Insert → Embed → By URL**, paste the app's address (for example `https://edu-smartai-catchup.netlify.app/math/grade-8/`) and choose **Whole page**. Add a plain "Open full screen" link below the embed: some browsers, notably Safari on iPads, may not save progress inside an embed.

## Privacy

- No logins, no analytics code, no student information collected.
- Progress is stored only in the student's own browser (`localStorage`). Switching devices or clearing browser data starts the skill map over.
- The only outside request is for the Google Fonts typefaces. If they are blocked, the apps use system fonts.

## Credits

Standards and STAAR item ranges come from lead4ward *Snapshot* documents (source: Texas Education Agency). This project is not affiliated with or endorsed by the Texas Education Agency or lead4ward.

---

**En español:** Edu-SmartAI Catch-Up es una colección gratuita y bilingüe de aplicaciones de práctica para que estudiantes de Texas se pongan al día en Matemáticas y Lenguaje (K–12), alineadas a los TEKS y STAAR. Cada aplicación tiene diagnóstico rápido, lecciones, práctica guiada y práctica independiente. No se recopila información de los estudiantes; el progreso se guarda solo en el navegador de cada estudiante.
