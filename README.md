# Agentic Pay-by-Vision: Multimodal AI & Autonomous Action Agents for Retail & MSME Invoice Automation

An advanced, edge-optimized multimodal AI system built to automate the entire invoice-to-payment workflow for merchants and MSMEs, reducing manual data entry to a 5-second "Snap & Approve" cycle.

---

## 🛠️ Technology Stack

* **Front-End Client:** Flutter / React Native (Edge-optimized camera capture & responsive mobile UI)
* **Computer Vision Engine:** OpenCV (Image processing & deskewing) + Google ML Kit / PaddleOCR (High-accuracy local token extraction)
* **Agentic Core & Orchestration:** LangChain / LlamaIndex + fine-tuned SLM (Small Language Models like Phi-3 / Llama-3-8B-Instruct)
* **Backend Layer:** FastAPI / Python (Asynchronous, low-latency framework)
* **Database & Vector Store:** PostgreSQL + `pgvector` (For semantic merchant matching & historic caching)
* **Banking Infrastructure (Mocked for Prototype):** RESTful Webhooks mimicking NPCI UPI Intent APIs, IMPS/NEFT networks, and corporate ledger frameworks.

---

## 🔄 Process Flow & System Architecture

The platform operates on a decoupled, async **Perceive ➔ Reason ➔ Execute** architecture pipeline:

PERCEIVE LAYER
              
              ───> Image Normalization & Deskewing (OpenCV)

              ───> Text & Bounding Box Coordinates Extraction (OCR Engine)
                              │
                              ▼

REASON LAYER   

              ───> Semantic Token Parsing & Line-Item Classification (SLM Agent)

              ───> Cross-Reference Vendor Directory & Compute Fraud Checks (DB Vector Match)
                              │
                              ▼

EXECUTE LAYER  

              ───> Assemble Structured JSON Payment Voucher (IFSC/UPI, Amount, GST)

              ───> Trigger Bank Transaction Gateway API Hook & Render One-Click UI Popup

### Operational Pipeline Breakdown

1. **Ingestion (Perceive):** The merchant captures an image of a physical bill or uploads an unformatted PDF invoice. The vision engine deskews and reads raw OCR tokens.
2. **Parsing (Reason):** The Agentic LLM layer maps unstructured strings into a strictly structured JSON payload mapping `vendor_name`, `account_no`, `ifsc`, `subtotal`, `cgst_sgst`, and `due_date`.
3. **Verification (Reason):** The agent performs a semantic similarity search using `pgvector` against the bank’s existing vendor database to prevent invoice fraud and verify account balance liquidity.
4. **Automation (Execute):** The agent bundles the metadata into a core banking transaction object, automatically constructs a pre-filled UPI string or IMPS routing token, and brings up a secure, biometric one-touch approval screen.

---

## 🚀 Key Value Proposition

* **Frictionless Digital Adoption:** Moves small business owners from painful manual bookkeeping data entry into digital current account loops instantly.
* **Intelligent Engagement:** Operates as an automated on-the-go accountant directly inside the bank's digital app environment.
* **Alternative Underwriting Data:** Collects clean B2B transactional logs to help the bank systematically evaluate risk and issue automated, pre-approved working capital micro-loans.
