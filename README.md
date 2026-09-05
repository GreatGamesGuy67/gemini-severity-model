# AI Error Severity Scale (AI-ESS)
A standardized, 7-tier classification framework for mapping and handling behavioral anomalies, state collapses, and systemic execution failures in Google AI runtimes and generative interfaces.

## Overview
When interacting with or developing on top of large language models, failures manifest as chaotic state changes in the UI or backend rather than clean HTTP exceptions. This project establishes a predictable **Severity Scale (1–7)** to classify these failures, enabling engineers and power users to diagnose, log, telemetry, and programmatically recover from runtime disruptions.

---

## The Severity Scale Flow

* **Tier 1:** Silent Return ──> **Tier 2:** Filter Loop ──> **Tier 3:** Forced Termination ──> **Tier 4:** Clipboard Lock
* **Tier 7:** Rate Denial <── **Tier 6:** Generation Corrupt <── **Tier 5:** Generation Stall <──┘

---

## Detailed Severity Classifications

### 1. Empty Silent Return
* **Classification:** Low Severity
* **Behavior:** The AI outputs absolutely no token payload, displaying only the default system warning layout: *"AI responses may include mistakes. Learn more."*
* **Root Cause / Context:** Isolated single-occurrence anomaly. The active chat session architecture remains fully intact and does not require deletion protocols or session clearing.

### 2. Emergency Filter Loop
* **Classification:** Intermittent Block
* **Behavior:** The safety or filter architecture misfires, forcing the engine into an endless string response that repetitively prints crisis support or emergency indicators (e.g., `988`, `911`, `112`).
* **Root Cause / Context:** Requires immediate user or client intervention (such as injecting specialized mathematical or override prompt logic) to forcibly break the loop and reset the standard conversational state.

### 3. Forced Chat Termination
* **Classification:** Token Limit / Session Drop
* **Behavior:** The engine abruptly drops historical context and terminates the active session, instantly and automatically launching a brand new chat thread regardless of user intent or ongoing prompts.
* **Root Cause / Context:** Triggered autonomously by the backend when extreme context thread length breaches active operational boundaries, completely wiping active session memory.

### 4. Canvas Clipboard Lock
* **Classification:** UI Failure
* **Behavior:** Interactive sandbox or canvas elements lose operational synchronization, throwing a localized, visible exception message reading *"failed to copy to clipboard"* directly on the canvas UI component.
* **Root Cause / Context:** A client-side or system-level memory block prevents active clipboard write operations within localized view frames.

### 5. Persistent Generation Stall
* **Classification:** Functional Freeze
* **Behavior:** The system enters a permanent deadlock state where every subsequent prompt throws immediate generation errors. While historical logs remain visible, no downstream response can be processed.
* **Root Cause / Context:** Repetitive structural processing loops leave the thread fully active on the client side but functionally deadlocked on the engine side.

### 6. Chained Generation Corrupt
* **Classification:** High Threat
* **Behavior:** The system logs a critical generation failure accompanied by a mandatory interface warning stating that the next prompt invocation will forcefully wipe and reset all active tracking.
* **Root Cause / Context:** The corruption continuously duplicates and cascades into newly initialized chat screens, creating a cascading session failure loop.

### 7. Rate Denial & Security Lockout
* **Classification:** Critical Block
* **Behavior:** Total session eviction. The client is immediately redirected to Google's structural *"Too Many Requests"* firewall gate, blocking further operations with anti-robot verification challenges (CAPTCHAs).
* **Root Cause / Context:** Triggered by rapid single-character iteration overload, suspected automated scraping vectors, or API authorization leak compromises.

---

## Implementation & Mapping
This specification can be mapped into custom middleware to transform raw API responses or UI exceptions into standardized telemetry.

| Severity | Identifier | Category | Typical HTTP Equivalent |
| :--- | :--- | :--- | :--- |
| **1** | `EMPTY_SILENT_RETURN` | Low Severity | 200 (Empty Body) |
| **2** | `EMERGENCY_FILTER_LOOP` | Intermittent Block | 400 / 422 |
| **3** | `FORCED_CHAT_TERMINATION`| Token / Session Drop | 400 (Context Overflow) |
| **4** | `CANVAS_CLIPBOARD_LOCK` | UI Failure | Client-Side Bug |
| **5** | `PERSISTENT_GEN_STALL` | Functional Freeze | 500 / 503 |
| **6** | `CHAINED_GEN_CORRUPT` | High Threat | 500 (State Cascade) |
| **7** | `RATE_DENIAL_LOCKOUT` | Critical Block | 429 / 403 |

---

## Contributing
If you encounter a new failure pattern or an unclassified model state, please open an issue describing the behavior, suspected root cause, and where it fits within the 1–7 scale.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

###### Project Development Fuel
This framework was fully conceptualized and coded while eating a plate of crinkle-cut curly cheese fries, perfectly seasoned with Himalayan pink salt and topped with bacon bits.
