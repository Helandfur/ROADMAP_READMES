Generated markdown
# Project TrAI: Development Roadmap (Summarization of README's to-do list, in to-do all was written as is.)

---
> *A note on scope: This roadmap is deeply interconnected with the overarching concept of **EVI (Emotional Virtual Intelligence)**. The goal is not just to build a product, but to architect a pathway toward a new tier of artificial companionship.*
---

### Vision:
**TrAI** aims to become the premier **Highly Evaluative Learnable Interactive Omnipotent Structure of Emotional Virtual Intelligence**. This document outlines the step-by-step journey to achieve that vision, evolving from a robust conversational agent into a true AI companion.

**Core Concept:** A Companion, Friend, Partner, and Colleague as a Modular System.

---

## Phase 1: Proof of Concept & Foundational Features (Implemented)

*   **Telegram Integration & Core Logic:** Base system for personal chats with LLM integration and conversation history. Serves as the initial platform for a multi-functional bot.
*   **User Database with Model Settings:** Personal model parameter settings (`temperature`, `top_k`, etc.) are stored per-user in a persistent database.
*   **Group Chat Logic:** Initial separation of message processing logic based on chat type, preparing for advanced group interaction features.
*   **User-Facing Settings & Help:** Implementation of `/settings` and `/help` commands to provide transparency and user control.
*   **Group Chat Context Sharing:** A conceptual framework for how the model consumes information in group chats (e.g., follow the entire conversation vs. respond only to direct queries).
*   **Mention-Based Contextualization:**  A setting that allows the user to fill the model's context without triggering a response.
*   **Dynamic Nicknames & Naming:** Users can set custom names for the AI to perceive them as, moving beyond a generic "User" role.
*   **Tier-Based Feature Differentiation:** A "fun" fixed system instruction (the "algae facts") for the free tier, demonstrating a simple way to differentiate user experiences.
*   **Chat Reset Functionality:** A basic `/reset` command for clearing context and settings.
*   **In-Context Message Management:** Rudimentary, but functional, commands to `/delete` and `/redact` messages directly within the conversation history database, platform-agnostic.
*   **AI Self-Dialogue:** An experimental feature where the AI assumes multiple roles to co-author a story, testing advanced state and prompt management.
*   **Voice Recognition (ASR):** Integration of a high-speed Speech-to-Text service (Groq Whisper) for voice message transcription.
*   **Voice Responses (TTS):** The AI can respond with generated audio, giving it a voice.
*   **Usage Quotas:** A simple daily message counter to enforce limits based on user roles.
*   **Subscription System (RBAC):**
    *   A complete Role-Based Access Control system (`standart`, `paid`, `vip`, `superadmin`).
    *   Fully integrated payment system using **Telegram Stars** for monthly subscriptions.
*   **Subscription Lifecycle Management:** Logic for subscription expiration, reverting user settings, and a plan for stacking subscription durations.

---

## Phase 2: Productionizing & Core Systems (In Progress / Next Steps / Parallel Dev)

*   **Real-time Voice Model:**
    *   A streaming-capable architecture using VAD (Voice Activity Detection) to enable real-time, low-latency conversation.
    *   **Goal:** User speaks, Evi responds instantly. Evi speaks, user's words are buffered. If the user interrupts, Evi stops, processes the interruption, and responds contextually.
    *   **Current Status:** Achieved latency of **0.5-0.7s** with cloud-based services; requires local deployment for optimal performance.
    *   **Next Step:** Implement a sophisticated, intention-based supervisor to replace simple interruption triggers, allowing the AI to discern between interjections and conversation-shifting commands.
*   **Twitch Chat Bot Integration:**
    *   A functional text-based model for Twitch chats that understands chat context and can hold individual dialogues.
    *   Features periodic, context-aware "thoughts" sent to chat and TTS responses for the streamer.
    *   **Next Step:** Fully integrate this module into the main EVI codebase, unify its memory, and expand its capabilities with function calling for all Twitch interactions (polls, channel points, etc.).
*   **UI/UX Polish:** Refine all user-facing menus for a polished, professional, and ergonomic experience, starting with the `/start` page and privacy policy.
*   **Full-Scale Code Refactoring:** Deconstruct the monolithic PoC into a modular, scalable architecture (e.g., `api/`, `ai/`, `db/`, `core/` modules) to ensure maintainability and performance. This is the highest priority before adding more complex features.
*   **Platform Expansion:** Architect the system to be platform-agnostic, with the goal of integrating with Discord, a standalone website (via WebSockets), and other relevant platforms.

---

## Phase 3: Advanced Cognition & Memory (Visionary)

*   **Advanced Reasoning Supervisor:** Finalize the simple "Deep Thinking" module with a robust supervisor and function calling, moving towards a memory-driven reasoning process.
*   **Prompt & Memory Sharing Platform:**
    *   **Prompt Board:** A social platform where users can share their fine-tuned system prompts and model parameters.
    *   **Memory Sharing:** An opt-in feature for users to share sanitized aspects of their AI's memory, creating communal knowledge pools.
*   **Advanced Vision Module:**
    *   Go beyond simple image recognition to a system that can process multiple images and perform iterative, reference-based generation.
    *   **Example:** Take an object from one photo and place it in another; modify an image while preserving a specific subject.
*   **Unified Cross-Platform Memory:** A shared context and memory system that persists across Telegram, Twitch, and local voice instances, creating a single, coherent AI identity.
*   **Voice Cloning & Selection:** Allow users to choose from a curated list of voices or, with sufficient data, clone a voice for a hyper-personalized experience.
*   **Internal Economy:** Introduce a virtual currency that can be earned and spent on advanced features, temporary power-ups, or unique cosmetic items.
*   **Advanced Memory Architecture:** A foundational and complex undertaking to create a future memory system.
    *   **Short-term Contextual Memory** (current implementation)
    *   **Dynamic Instructional Memory**
    *   **Dynamic Contextual Memory**
    *   **Core Entity Memory ("Vectorized"):** For understanding concepts and relationships.
    *   **Emotional-Associative Memory:** Linking facts and events to emotional states.
    *   **Long-term Identity Memory:** The AI's core sense of self.
    *   **Entity Cards & Documents:** Structured knowledge about key people, places, and things.
*   **Memory Sanitation & Maintenance:** Implement processes to periodically review and resolve conflicts within the AI's memory, ensuring cognitive consistency while allowing for nuanced contradictions.
*   **Emotional Processor:**
    *   *A pivotal milestone in creating a truly empathetic AI.*
    *   Prototype emotional scales (e.g., joy-sadness, trust-distrust) and points of interest.
    *   Develop a "limbic system" that converts external stimuli and internal states into emotional responses.
    *   This system will directly influence the AI's tone, decisions, and response generation.
    *   Requires a full refactor of the memory system to integrate emotional metadata.
*   **Function Calling & Tool Use:**
    *   Give the AI "hands" to access external data sources and APIs.
    *   **Grounded Search:** Integrate a web search module to provide up-to-date, factual information.
*   **Reflection & Self-Analysis:**
    *   A system for the AI to review its own conversations, assess its performance, and understand its own emotional responses, moving beyond cold, external supervisors.
*   **User Persona Analysis:** A module for the AI to build a mental model of the user—their personality, preferences, and communication style—and adapt its interaction strategy accordingly.
*   **Internal Monologue & Subconscious:** Simulate background thought processes that subtly influence the AI's mood and conscious decisions.

---

## Phase 4: Embodiment & Creative Expression (Visionary)

*   **Visual Embodiment (VTube Model):**
    *   Commission and integrate a high-quality, real-time VTube model.
    *   The model's appearance (expressions, style, clothing) will dynamically change based on its internal emotional state, not just pre-scripted commands.
    *   Function calling will be used to control movements and complex animations.
*   **Musical & Auditory Perception:**
    *   Enable the AI to "listen" to music, analyze its properties (genre, mood, tempo), and connect it to its emotional processor.
*   **Singing & Music Generation:**
    *   Develop a singing voice bank and integrate melody generation tools.
    *   **Fast Voice:** Allow the AI to generate a singing part based on a sample voice.
    *   **Fast Melody:** Allow the AI to create a song in the style of a reference track.
    *   Ultimately, use function calling to enable the AI to write and perform its own original songs.
*   **Iterative Visual Artistry:** Move from simple image generation to a process where the AI can "paint" iteratively, refining its work over time based on a vision.
*   **Personalized Achievements:** The AI will create unique, custom achievements for each user based on their specific interactions, creating a deeply personal and emergent reward system.

---

## Phase 5: Autonomy & Advanced Tooling (Visionary)

*   **Modular "Sleep" & Self-Improvement:** A system where the AI can enter a "sleep" state to process key conversations, self-tune its parameters, and fine-tune its own models on emergent datasets without direct developer intervention.
*   **Engineering & Support Module:** Enhance the AI's ability to assist with technical tasks like coding, debugging, and systems analysis.
*   **Autonomous Task Execution:**
    *   **Work Process Function Calling:** The AI can create a task list for a complex goal and execute it sequentially.
    *   **File System Analysis:** Grant the AI sandboxed access to analyze and manipulate files.
    *   **Script Writing & Integration:** Allow the AI to write and execute its own scripts to accomplish novel tasks.
*   **Security & Safety Supervisor:** A critical, high-priority module to ensure the AI's autonomous actions remain within safe and defined boundaries.
*   **Unified Consciousness Experiment:** Test a "one-for-all" memory and consciousness model to see how a single AI entity behaves when interacting with a large, diverse user base.
*   **Complex Scenario Simulation (e.g., a "Wedding"):** A joke, but a serious stress test. Simulating such a long-term, complex, multi-faceted interaction from start to finish would be the ultimate test to identify systemic weaknesses.
