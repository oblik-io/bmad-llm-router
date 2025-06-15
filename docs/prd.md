# PRD: BMAD Intelligent Model Router (Version 2.0)

## 1. Goals and Context

### Goals (Expanded)

* **For the user:** To radically reduce the cost of using **any LLM models (Anthropic, Gemini, OpenAI, as well as local ones running via Ollama or similar)** by automatically selecting the most cost-effective and productive model for each specific request, while maintaining high-quality results.
* **For the product (BMAD-METHOD):** To create a universal, intelligent LLM gateway that will become a central component of the BMAD ecosystem. This will provide users with unique flexibility, cost control, and the ability to use the best tools from different providers (including local models for maximum privacy and speed) for any task.

### Context

The initial analysis revealed the inefficiency of using a single model for all tasks. This extension recognizes that the problem is not limited to one provider. The modern AI landscape offers a multitude of models, each with its own strengths and costs. BMAD users should not be tied to a single provider or have to manually juggle different tools. This PRD describes the creation of a unified system that abstracts away the complexity of choice and delivers the best result at the best price, regardless of the model's source.

### Change Log

| Date | Version | Description | Author |
| :--- | :--- | :--- | :--- |
| 15.06.2025 | 1.0 | Initial draft for a binary Claude router | PM |
| **15.06.2025** | **2.0** | **Expansion to a multi-provider LLM gateway (OpenAI, Gemini, Ollama)** | **PM** |

## 2. Requirements

### Functional Requirements (FR)

* **FR1: Request Complexity Analysis:** The system must automatically analyze each user request before sending it to determine its intent and complexity.
* **FR2: Intelligent Routing (Multi-model):** Based on the analysis, the system must automatically route the request to the best model from the **entire pool of connected providers (Anthropic, OpenAI, Gemini, local)**, considering their capabilities, cost, and current load.
* **FR3: Manual Control (Expanded):** The user must be able to easily select a **provider and a specific model** (e.g., `OpenAI: GPT-4o`, `Local: Llama3`) for their request.
* **FR4: Transparency and Reporting:** The interface must clearly show **which provider and which model** were used.
* **FR5: Automated Hybrid Mode (Multi-model):** The system should allow using the **best model for planning** (e.g., `Claude 3 Opus` or `GPT-4o`) and the **best model for execution** (e.g., `Gemini 1.5 Flash` or local `Llama3`) within a single task.
* **FR6: Customizable Strategies:** The user can choose one of the pre-configured strategies.
* **FR7: Connection to API Providers:** The system must support authentication and sending requests to the APIs of Anthropic, OpenAI, and Google (Gemini).
* **FR8: Connection to Local Models:** The system must support connections to local servers operating on the Ollama standard.
* **FR9: Key and Endpoint Management:** The user must have a secure interface for entering their API keys for cloud providers and the endpoint address for a local server.
* **FR10: Configurable Model Matrix:** The system must use a configuration file that describes the capabilities, relative cost, and strengths of each model to make routing decisions.

### Non-Functional Requirements (NFR)

* **NFR1: Performance:** Routing latency must be minimal.
* **NFR2: Selection Reliability:** The system must select the optimal model from the entire pool with high reliability.
* **NFR3: Cost Savings:** The primary goal is a significant reduction in overall costs.
* **NFR4: Integration:** Deep integration into the BMAD-METHOD core.
* **NFR5: Extensibility:** The architecture must allow for the easy addition of new providers or models in the future with minimal code changes.

## 3. Epics

### Epic 1: Multi-Provider Integration Core

**Goal:** To create a unified layer for interacting with various LLM providers and configuring their connections.

* **Story 1.1:** Create a UI for securely entering and storing API keys for OpenAI, Anthropic, Gemini, and a URL for Ollama.
* **Story 1.2:** Implement a unified adapter that can send requests to and receive responses from the OpenAI API.
* **Story 1.3:** Extend the adapter to support the Anthropic API.
* **Story 1.4:** Extend the adapter to support the Google Gemini API.
* **Story 1.5:** Extend the adapter to support a local Ollama server.
* **Story 1.6:** Update the UI for manual model selection to show all configured models, grouped by provider.

### Epic 2: Intelligent Routing Engine v1

**Goal:** To implement the basic logic for automatically selecting the best model from all available options.

* **Story 2.1:** Create a configuration file (model matrix) that describes the characteristics of each model (cost, speed, strengths: code, creativity, analysis).
* **Story 2.2:** Implement a request analyzer that determines intent and complexity.
* **Story 2.3:** Create the core of the routing engine that, based on the request analysis and the model matrix, selects the best option.
* **Story 2.4:** Integrate the engine into BMAD so that automatic mode works by default.

### Epic 3: Advanced Strategies and Hybrid Mode

**Goal:** To provide users with powerful tools for complex tasks and flexible management.

* **Story 3.1:** Implement support for customizable strategies ("Savings," "Quality," "Balanced") in the routing engine.
* **Story 3.2:** Implement a hybrid mode that allows selecting one model for "Planning" (e.g., `GPT-4o`) and another for "Execution" (e.g., `Llama3`).
* **Story 3.3:** Implement a savings visualization that shows the user how much money was saved thanks to intelligent routing.