# Super Prompts

Open, copy-and-paste "super prompts" for teachers and curious humans. Each one turns an AI chatbot such as Claude into a careful helper for a specific job, like building a show-and-share page from a pile of student submissions or summarizing peer feedback. Every prompt is documented, tested, and free to adapt.

**Browse and copy them on the website:** https://wfryer.github.io/super-prompts/

## The prompts

| Prompt | What it does |
| --- | --- |
| [Student Work Spinner](prompts/student-work-spinner.md) | Turns a Canvas submissions zip into a single-page spinner and show-and-share site with first-name links, plus a CSV that remembers which projects your class has already watched. |

## How to use a super prompt

1. Open the prompt file and read the "How to use it" steps at the top.
2. Copy the prompt text and paste it into a new chat. Most of these work best in Claude with file upload and file creation turned on.
3. Fill in any [bracketed] settings, or leave them blank and the AI will ask you.
4. Answer the questions, check what comes back, and adjust.

## Student privacy

Never put student data in this repository: no submission zips, no CSVs, no screenshots with real names. Use made-up names in examples. The included `.gitignore` blocks zip and CSV files to help.

## Add your own prompt

Copy `prompts/_template.md`, fill it in, and add one entry to `prompts.json`. The website updates itself. Keep the text between the `PROMPT START` and `PROMPT END` markers, because that is what the Copy button grabs.

## License and credit

All prompts and text in this repository are licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). You may copy, share, and adapt them, including for classroom or commercial use, as long as you credit **Wes Fryer** and link back to this repository.

Thanks to Mike Caulfield, whose [SIFT Toolbox](https://gitea.com/mcaulfield/SIFT-Toolbox) showed how useful it is to share super prompts in the open.
