# 🖥️ System Call Tracer & AI-based Log Analyzer

This project is a **Linux system call tracer** combined with an **AI-based log analyzer**.  
It uses `ptrace` in C to trace all syscalls made by a target process and then leverages **Google Generative AI** (Gemini API) to interpret the logs, explain each syscall, and make an educated guess about what the program is doing.

---

## 📌 Features
- **Low-level tracing** of syscalls via `ptrace` (like `strace`).
- Supports **x86_64 syscall table** for human-readable syscall names.
- **Log storage** in `syscallLogs.txt`.
- **Python-based AI analysis** of syscall logs.
- Command-line execution with target program as argument.
- Can make **educated guesses** about the program’s behavior using syscall patterns and CLI arguments.

---

## 🧩 Components / Requirements
- **Linux** environment with `ptrace` support.
- **GCC** for compiling C tracer.
- **Python 3.8+** with:
  - `google-generativeai` (Gemini API client)
  - `subprocess` (standard library)

---

## 🔧 Installation

### 1️⃣ Clone the repository

CMD : git clone https://github.com/SagarEL/System_call_Tracer.git

CMD : cd SystemCallTracer

### 2️⃣ Install Python dependencies
CMD : pip install google-generativeai

### 3️⃣ Set up Google API Key
Get your API key from: Google AI Studio

### Replace API_KEY in sysCallAnalyzer.py with your key:

genai.configure(api_key="YOUR_API_KEY")


## 🚀 How to Use

### 1️⃣ Compile the Tracer

CMD: gcc traceLogger.c -o mytrace
### 2️⃣ Trace a Command

CMD: ./mytrace <command> [args...]

Example: ./mytrace ls -l

This generates syscallLogs.txt with all syscalls.

### 3️⃣ Analyze with AI

CMD : python3 sysCallAnalyzer.py 

Reads syscallLogs.txt.

Sends to Gemini API for interpretation.

Saves output to analysis.txt.


