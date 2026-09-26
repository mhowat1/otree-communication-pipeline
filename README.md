# otree-communication-pipeline
This is a Python package developed to automate contact with participants in a study (e.g., sending survey links, reminders to take action on various tasks, and communicate abou study compensation). It is run using oTree and Windows Task Scheduler. To function it requires a live Qualtrics, SendGrid, and Twilio API key.

## file architecture 

├── .env                  ⚙️  SETTINGS FOLDER — times, API keys, study days​

│                             This is gitignored ​

├── orchestrator\         🧠  The main executor​

│   ├── clock.py              Checks time​

│   ├── config.py             reads the env file​

│   ├── db.py                 talks to the database files​

│   ├── study_clock.py        calculates participant timing​

│   ├── intake.py             turns a survey response into a participant​

│   ├── messages.py           ✉️ EMAIL CONTENT – can edit this by hand​

│   ├── dispatch.py           sends ONE email, start to finish​

│   ├── deliberation.py       holds session info + calendar files​

│   ├── welfare.py           creates WF IDs and individual links​

│   ├── qualtrics_*.py        fetches survey answers​

│   ├── senders\              hands the email to SendGrid​

│   └── jobs\             ⏱️  CHECKLIST — one file per hourly task​

│       └── run_cycle.py      the boss: runs all the others in order

│​​

├── scripts\              For manual runs – used primarily
in testing rather than during the live study ​

│                             send_test_email,
set_deliberation_session,​​

│                             run_mock_cycle, welfare_ids,
purge_participants…​​

│​​

├── data\                 🗄️  STUDY DATABASE - git ignored ​

│   ├── study.sqlite3         records participants, links,
and emails sent​

│   ├── cycle.log             logs one line per action​

│   └── backup.log​ ​

│​​

├── scheduler\windows\    ⏰ Task Scheduler ​

│   ├── run_cycle.cmd         timing instructions​

│   └── FoodChoicesCycle.xml ​

│​​

└── venv\                 🔧 Python tools, git ignored ​​
