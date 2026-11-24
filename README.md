# AI & Automation Externship: Document Processing Pipeline Building Blocks

Hands-on notebooks from my **AI & Automation externship at Outamation** (May to July 2025). Outamation automates mortgage and title document workflows. Each notebook is one step of the pipeline that turns messy real-world documents into data an LLM or a downstream system can use:

```
 scanned / PDF documents
        │
        ├─► 02  extract text and tables from PDFs (PyPDF2, pdfplumber, PyMuPDF)
        ├─► 03  clean noisy scanned images before OCR (OpenCV)
        ├─► 04  normalise messy text: encoding, accents, punctuation, prices (regex, unicodedata)
        ├─► 05  structure the result as JSON and analyse it (pandas)
        └─► 01  put an LLM on top: a chatbot with LlamaIndex + Gemini
```

**Author:** Marie Haccandy · [LinkedIn](https://www.linkedin.com/in/marie-christine-haccandy-24b6b21ba) · [GitHub](https://github.com/mhacc001)

## Notebooks

| # | Notebook | What it does | Libraries |
|---|---|---|---|
| 01 | [LlamaIndex chatbot](notebooks/01-llamaindex-chatbot.ipynb) | Interactive chatbot on Gemini through LlamaIndex, keeping the chat history as `ChatMessage` objects | LlamaIndex, Gemini |
| 02 | [Document data extraction](notebooks/02-document-data-extraction.ipynb) | Compares three PDF libraries on a multi-page title report: page text, tables, metadata, text blocks with bounding boxes and fonts, and rendering a page to an image | PyPDF2, pdfplumber, PyMuPDF |
| 03 | [Image cleaning](notebooks/03-image-cleaning-opencv.ipynb) | Cleans a noisy scanned image for OCR: non-local-means colour denoising, then CLAHE contrast boost on the brightness channel only (HSV) so colours stay true. Tuned over 6 attempts to stop text from blurring. | OpenCV, NumPy |
| 04 | [Text cleaning](notebooks/04-text-cleaning-regex.ipynb) | Fixes broken accents and encoding, strips emoji and repeated punctuation, collapses whitespace, and normalises inconsistent price formats | re, unicodedata |
| 05 | [Structured data](notebooks/05-pandas-json-processing.ipynb) | Loads processed records from JSON into a DataFrame and checks types and contents | pandas |

All notebooks run in Google Colab (badge at the top of each).

## Security note

The chatbot notebook reads the Gemini key from an environment variable or a hidden prompt (`getpass`) and never stores it in the notebook. The document used in notebook 02 was a real title report, so its printed output was cleared before publishing.

## Where this went next

- [document-processing-eval](https://github.com/mhacc001/document-processing-eval): a LlamaIndex + Gemini document assistant prototype with an evaluation of its accuracy, reliability, cost, privacy handling, and where a human still needs to review
- [ai-support-triage-agent](https://github.com/mhacc001/ai-support-triage-agent): an agentic workflow on the Claude API that calls REST services, with human approval before every write and a full audit log

## Skills

Python · LLM application development · LlamaIndex · Gemini API · document AI / PDF extraction · OCR preprocessing (OpenCV) · data cleaning · pandas · Google Colab
