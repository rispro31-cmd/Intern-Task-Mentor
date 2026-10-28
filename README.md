# AI Intern Task Mentor

An AI chatbot web app that assigns tasks to company interns, explains each task in a human voice (Tamil, English, Hindi), emails the submission link and review date, reviews the submission against the company's expected output, and keeps sending feedback until the task is completed.

## How it works

1. **Company (Admin)** assigns a task: title, description, expected output (one requirement per line), intern name/email, language, review interval, pass score, max attempts.
2. **AI explanation**: the chatbot explains the task in Tamil, English or Hindi, as text and voice (Web Speech API).
3. **Email**: the intern gets the submission link and review date.
4. **Submission**: the intern submits their work through the link.
5. **Review**: on the review date the AI compares the submission with the expected output and scores each requirement.
6. **Iteration**: if the score is below the pass mark, the intern gets specific feedback, a new review date and the submission link again. This repeats until the work matches.
7. **Completion**: once it matches, the task is marked Completed and the loop stops. After the max attempts, it is escalated to a human mentor.

Status flow: `Assigned → Submitted → Needs Changes (repeat) → Completed`

## Features

- Real human voice explanation in 3 languages: the mentor records (or uploads) a voice for English, Tamil and Hindi; computer voice is the fallback
- Voice files can be downloaded and shared; put them in the `voices` folder as `en.webm`, `ta.webm`, `hi.webm` (mp3, m4a, wav, ogg also work) so everyone who opens the app hears them
- Chatbot answers intern questions (deadline, submission link, requirements, status)
- Requirement-by-requirement review with a match score
- Feedback in the intern's language
- Email outbox with "Open in Gmail" and "Send from my mail app" options
- Dashboard of all interns, attempts, scores and review dates
- Optional Google Gemini API key for AI review and chatbot answers; works offline with a built-in checklist matcher without one
- "Run review now" button for demo (skips waiting for the review date)

## Run it

No installation needed. Unzip, then open `index.html` in Google Chrome or Microsoft Edge.

Live hosting: enable **GitHub Pages** (Settings → Pages → Deploy from branch `main`, folder `/root`).

## Tech stack

HTML, CSS, JavaScript, Web Speech API (voice), Google Gemini API (optional AI), localStorage (data).

## Future improvements

- Backend (Node.js + database) and real email sending (e.g. Resend / Nodemailer)
- Server-side scheduler for review dates
- File and GitHub repository uploads with code analysis
- Login for admins and interns
