# Project EVI AI Assistant + companion 
**(Proof-of-Concept "Tranquility Telegram bot")**

**TrAI v3 (Tranquility AI 3.x)** is a proof-of-concept for a sophisticated, multi-modal AI companion, ("HELIOS EVI - Highly Evaluative Learnable Interactive Omnipotent Structure of Emotional Virtual Intelligence") integrated within Telegram, Twitch, Discord & WEB. This project was developed solo to rapidly prototype and test complex concepts in conversational AI, multi-modal interaction, state management, and persistent persona development.
This script is a foundational first step. Aligned with the `HELIOS_EVI` project `ROADMAP.md`, it will be integrated into the core modular EVI system
While the current implementation is a monolithic script—a deliberate choice for agility in the idea-testing phase—it is built upon a comprehensive architectural vision for future modularity, scalability, and production-readiness. This repository serves as a practical demonstration of the foundational ideas and technical groundwork for creating a AI companion, directly aligning with the mission to build the world's best realtime avatar products.

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![telegram-bot](https://img.shields.io/badge/API-python--telegram--bot-blue.svg)](https://python-telegram-bot.org/)
[![Google Gemini](https://img.shields.io/badge/LLM-Google%20Gemini-orange.svg)](https://ai.google.dev/)
[![Groq](https://img.shields.io/badge/ASR-Groq%20Whisper-green.svg)](https://groq.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Core Philosophy & Product Vision

This project is more than a chatbot; it's an exploration into creating a persistent, evolving AI entity & test place for future ideas and idea's mechanics. The core philosophy is to build a system that is not only intelligent but also interactive, emotionally aware, and capable of complex reasoning. It'd be a hands-on implementation of the ideas required to build a true AI "Person"—an agent that can see, hear, speak, remember, and interact meaningfully across different platforms.

This aligns with the product-first mindset: an obsession with the end-user experience, focusing on low-latency interaction, rich multi-modal capabilities, testing even the most strange ideas, and a reliable, scalable backend.

## Key Features (Demonstrated in this PoC)

This proof-of-concept already implements some features that serve as the explorations for a full-fledged product. Something could be already cutted-off, but still written in to-do.

####  **1. Advanced Conversational AI Core**
*   **Based Multi-API Integration:** Dynamically uses Google Gemini for core reasoning and Groq's API for high-speed Whisper ASR, demonstrating the ability to leverage the best tool for each task. (Voice ver. used Deepgram streaming in, streaming out, assembling, LLM token streaning -> TTS chunk streaming, coming close to ~0.5s between end of phrase [+ timer if needed] and first reply's sound)
*   **Thinking Test:** A modular reasoning chain that breaks down user queries into phases. to be reconfigured into dynamic system
*   **Self-Dialogue Simulation:** An experimental feature where the AI can engage in a multi-persona dialogue with itself to explore a topic, made for fun, then becomes a part of future plans.

####  **2. Multi-Modal Interaction**
*   **Vision (Experimental):** There was vision system part, but it should be recreated.
*   **Voice-to-Text (Ears):** Integrates Groq's Whisper API to transcribe user voice messages, enabling seamless voice-based interaction.
*   **Text-to-Speech (Voice):** Utilizes simple `edge-tts` to generate spoken responses, giving the AI a voice and enhancing the "avatar" experience. Would be changed

####  **3. Dynamic State & Persona Management**
*   **Persistent Persona:** The AI maintains a consistent persona ("Tranquility") with a defined character, which is managed through a simple system prompt as for beginning.
*   **Role-Based Access Control (RBAC):** Concept of simple multi-tiered user system (`standart`, `paid`, `vip`, `superadmin`) with granular, command-level and parameter-level permissions. This is crucial for managing features in a production environment.
*   **Dynamic Settings:** Base system that exist for users, who know how to adjust LLM parameters (`temperature`, `top_k`, `max_tokens`), conversation history length, and behavior toggles on a per-chat basis, with all settings stored persistently in an SQLite database. To be evaluated.

####  **4. Monetization & User Tiers**
*   **Telegram Stars Integration:** A complete, semi-working (needs reset for settings after sub end & accumulation of time subs activated) implementation of a subscription system using Telegram's native currency, Stars. Includes invoice generation, pre-checkout handling, and successful payment processing.
*   **Subscription Management:** Users can purchase and activate tiered subscriptions (`Paid`, `VIP`) which unlock more powerful features and higher usage limits, demonstrating a clear path to commercialization after design polishing.

## Technical Stack

*   **Backend:** Python
*   **Async Framework:** `asyncio`
*   **Telegram API:** `python-telegram-bot`
*   **AI Models:**
    *   **LLM:** Google Gemini
    *   **ASR (Speech-to-Text):** Groq (Whisper-Large-V3)
    *   **TTS (Text-to-Speech):** Edge-TTS
*   **Database:** `SQLite` (chosen for simplicity in PoC; designed for easy migration to a production DB).
*   **The architecture would be refactored and become a part of modular LLM-cored system with RTvoice integration, Personal Visual model (Personal desktop\mobile for base user, VTubeStudio for accompany to the streamer) WEB-site (accumulating c.ai idea, some ai_dungeon-like abilities, customizable Workflow, typical chat interface & other hehe using AI to create content for streamers or base users), Telegram, Discord & Twitch**

## Architectural Considerations & Path to Production

This PoC was intentionally built as a single script to maximize the speed of experimentation (cuz lack of good time for that). The clear path to a **fast, scalable, and reliable** production system involves the following steps:

1.  **Modularization:** Refactor the monolithic `0.py` into a structured package as always planned
2.  **Database Migration:** Transition from SQLite to production-grade database to handle high concurrency and large volumes of data.
3.  **Introduce an ORM:** Replace raw SQL queries with `SQLAlchemy` for improved security, maintainability, and code clarity.
4.  **State Management:** For a truly real-time system, migrate chat session state from the DB to a low-latency in-memory store.
5.  **API Abstraction:** Create a unified `AIProvider` interface to allow for easy swapping and A/B testing of different cloud/local tuned LLM or multi-modal models without changing core logic.
6.  **Containerization:** Fully containerize the application and its dependencies using `Docker` and `Docker Compose` for reproducible environments and simplified deployment on different pcs.
7.  **CI/CD & Testing:** Implement a robust testing suite with `pytest` and set up a CI/CD pipeline (e.g., GitHub Actions) to automate testing and deployment. Always wanted clearness.
8.  **Performance Optimization:** While already using `asyncio`, further profiling and optimization would be done, with critical code paths potentially being rewritten in **Rust** for maximum performance, especially in media processing pipelines (for the time, all ideas & scripts reborn in one omniproject).

## Project Vision & Roadmap

This PoC is merely the first step. The full roadmap envisions a complete ecosystem for a highly interactive and emotionally intelligent AI companion.

*   **Phase 1: Foundation & Refactoring:** Complete the "Path to Production" steps outlined above to build a robust, scalable backend.
*   **Phase 2: Advanced Memory & Cognition:**
    *   Implement a hybrid memory system (short-term context, long-term vector DB (it'be better to create own one multistructure, project-orientated)).
    *   Develop an "Emotional Processor" to allow the AI's state to influence its responses.
    *   Introduce a self-reflection module for the AI to analyze its own conversations and improve.
*   **Phase 3: Multi-Platform Expansion & Tooling:**
    *   Abstract the core logic from Telegram to combine deployment with `Discord`, `Twitch` scripts, and a standalone web interface using WebSocket.
    *   Implement robust **Function Calling** to give the AI "hands" to interact with external APIs and tools.
*   **Phase 4: Embodiment & Creative Expression:**
    *   Integrate with a **VTube/Realtime Avatar** model, controlled by the AI's emotional state and responses.
    *   Enable creative abilities like generating art (make her using and learning ART models, maybe creating artworks "by hands"), singing (voice synthesis with music generation in two ways at least), and coding.



#To_Do_List


----------------------------------------------------------
--WARNING THAT NOTES R CONNECTED WITH ALL CONCEPT OF EVI--
----------------------------------------------------------


Helios Evi wants to become the best
Highly Evaluative Learnable Interactive Omnipotent Structure of Emotional Virtual Intelligence in your heart
So Evi is learning how to become the best one step-by-step

Interlocutor, friend, partner, colleague as a modular system


----------------
--ALREADY DONE--
----------------


Basic system for a personal Telegram chat - LLM integration and dialogue history
The beginning of a smart bot system for multifunctional use in Telegram chats.

User database with model parameter settings
Adding personal model parameter settings for users to the database.

Separation of logic for handling group chats
Preparation for the further division of message processing logic based on the chat type.

Information output
Displaying a user's current settings upon request and the initial implementation of the /help command.

Principles of context sharing in group chats (Requires development and concept refinement)
Implementing individual context settings into the group chat logic, determining how the model will retrieve information. This includes maintaining the chat's dialogue or responding directly to user queries.

Settings for requiring mentions to populate the context with information
Why does nobody on Telegram have this... lol...

Perception of nicknames and naming (may be revised after memory implementation and in conjunction with it)
The user can be a generic user, themselves, or anyone they want to be for the model.

Fixed system instruction for Free users
Introduction of a mandatory humorous additional instruction about algae for non-paying subscribers.

Reset (re-check where it is and what it does, fix it)
The initial implementation of a reset function for context and settings.

Deleting and editing messages in the messenger (raw, basic, needs refinement, preferably through the Telegram interface)
The user should be able to delete, edit, and add messages to the database, regardless of the platform.

Initial concept of a dialogue with itself for the LLM (a fun, nonsensical function, but the idea will be useful)
Assigning roles to the model to create a story with itself for fun, allowing it to write fanfiction automatically until stopped.

Voice recognition (finalize the logic, the concept is adequate for now)
Connecting a test Speech-to-Text (STT) service to voice messages.

Voice responses (finalize the logic and find a voice, a decent Text-to-Speech)
Enabling the model to respond with audio messages.

Quotas (optimize the counter)
Limiting the daily number of actions.

Subscriptions
Developing a system of roles with corresponding restrictions, and creating a Super User (SU) role. Introducing payment for monthly "paid" and "vip" plans via Telegram Stars.

Finalizing the subscription concept (settings reset upon expiration)
The system is viable without the hassle of payment gateways. The logic needs to be finalized so that upon expiration, the subscription resets to the previous plan's settings. The purchase logic should be finalized so that activation dates are cumulative, and higher-status subscriptions expire first. A subscription marketplace is a future consideration.

Voice model for speech (a lot to work on, the future core of the system will likely begin here, it's time to start from scratch and integrate all modules)
A version of the code has been created that supports streaming conversation, with options for webrtcvad and a custom VAD.
User speaks - Evi responds.
Evi speaks - The user's words are written to a background memory context if there is no interruption trigger.
Evi speaks - The user interrupts with a trigger, Evi records its spoken phrase, a marker, the unspoken part of the phrase into the database, and responds to the new input based on the entire context.
Speed is 0.7-0.5s depends on length, needs to be deployed locally (all cloud-based services).
An intention-based recognition system is needed to replace triggers with a full-fledged intermediary, allowing it to both respond and listen to populate the context.
The code needs to be linked with the Twitch chat code, donation alerts, and Twitch commands via function calling and given to a friend by the end of summer.
Some short words about:
The bot's core logic is managed by a GuildSession class for each server. This session orchestrates several key components:
DeepgramSink: A custom discord.sinks.Sink that receives raw audio from Discord users, downsamples it, and forwards it to the Deepgram streaming connection.
VoiceActivityManager (VAD): Processes audio chunks in near real-time to detect speech. When it detects a pause, it assumes the user has finished speaking.
SpeechBuffer: Collects the transcribed text from Deepgram. Once the VAD signals the end of speech, the buffer's content is finalized and sent for processing.
prompt_queue: An asyncio.Queue that holds finalized user prompts (from voice or text), ensuring they are processed one by one.
Response Worker & Streaming Pipeline: A background task pulls prompts from the queue, gets a response from Gemini, and streams the generated audio directly to the voice channel, creating the effect of the bot speaking as it "thinks".
Session Supervisor: A crucial background task that periodically checks the health of the Deepgram connection, triggering a reconnect if issues are detected to ensure long-term stability.



Text model for Twitch chat (refine the TTS to voice user-written text without processing, minor fixes, and integration into the main code)
Supports dialogue, understands the chat context, and maintains a dialogue with the user.
Posts thoughts about what is happening in the chat based on a timer trigger.
Supports TTS responses (after LLM processing) for the streamer and moderators; a separate point-based system will be available for viewers.
The rest of the functionality will be integrated with the main block.


------------------------------------------------------------
--ONLY PLANNED / DONE AS LOGIC STRUCTURES, BUT NOT WRITTEN--
------------------------------------------------------------


Polishing the design, optimizing settings for the casual user with a separate advanced menu
All draft menus need to be redesigned with smooth transitions, improved aesthetics, and ergonomics. This should start with the "start" page, adding a privacy policy, and then move to the main menu. Frequently used options should be placed higher.

Refactoring this mess into something meaningful - code optimization, clear module division
The concept has proven its viability, so it's time to remove all hindrances and build the system properly. This includes cleaning the code, creating a command factory, and clearly dividing the spaghetti code into modules.

The idea of launching a website and integrating with Discord, Twitch, and Telegram is viable
Why not use all the familiar APIs?

Complete the work on the "thinking" process, which is currently stuck at the stage of clumsy pre-scripting functions
The settings are promising but require refinement, proper naming, and accurate quota counting, as the previous implementation was flawed. Ideally, a supervisor and function calls are needed, which pushes the concept closer to a planning-based memory system. This can be deferred.

Prompt board
Users should have the right to share their instructions and parameters, similar to a social network. This needs further thought. After all, services like c.ai are total shit.

Sharing memory between users
The same applies to the models' memory, as long as it remains private from other users.

Finally perceive images
Fix the broken visual perception and creation function to make it operational. Integrate a system capable of seeing images (any number within reason) and creating images (any number within reason). When creating an image, it must be able to take a reference image as input and process it either entirely or specific parts of it. For example, transferring a random object from a photo to another, changing everything except that object, or changing only that object.

Integration of external services with the same system (sharing) - transferring context and memory to Twitch and local voice
The code for the Twitch chat and the voice assistant should share memory with the main system without cluttering the basic Telegram memory.

Voice selection/cloning
This has already been done in another service, but it doesn't matter. You don't always have to create something unique. The user will be able to choose their assistant's voice or create a custom one (this requires significant consideration).

Internal currency and bindings
It would be fun to add a basic system for virtual payment and earning units; it might be useful later.

Memory - development (short-term context, instructional dynamic, context dynamic, essential ("vector"), emotional-associative, long-term identity, entity cards, documents)*
In short, a total fucking hassle. It's time to turn all the accumulated ideas into something that can be visualized and described. Entity cards and documents should be left for later, but not forgotten, as they are important options. Start with vector and pseudo-vector experiments, debugging through intermediaries, and then implement supervisors. The entity system might end up being tripartite, so be prepared.

Sanitary process of maintaining and fixing memory
Memory should be checked regularly, both in flow and statically, to avoid conflicts. It's worth allowing some degree of freedom for minor contradictions.

Personalities
How am I worse than other services for casual users? An abundance of settings and freedom will only confuse the user. Custom memory and instruction presets can serve as examples and products (with unique mechanics and features). It might be worth using separate internal processes that the basic models don't have, which will provide a more advanced user experience. Paid > free as always. For now, the idea is a clean, basic model for the average user, with some separate modules, which is common. Advanced personality integration will come with thematic modules, areas of knowledge, and preparation. This is very raw -> think about it after implementing the functionality. It could be one of the applications for internal virtual tokens.

Emotional processor with a link to memory
FINALLY, YOUR TIME HAS COME, I'VE WAITED SO LONG FOR THIS. Prototyping emotional scales and points of interest. The model's emotional memory and limbic system. Conversion of external impulses and the meaning attached to its statements. Development of a system of well-being and the influence of the model's state on it. Preparation of an emotional supervisor. And now, refactoring the damn memory to accommodate all of this...

Emotional metadata
This is how the concept sounds now, but who knows what will actually happen after the previous step. Keeping it in mind.

Emotional integrations
Into voice, vision, and hearing. This should affect both perception and responses.

Function calling
And here's another "your time has come." This should have been done 1.5 years ago. Optimization of the intermediary for creating the model's "hands." Access to external sources.

Search grounding
This has also been long overdue, and I don't remember why it was deprioritized. The function for searching for information in the browser needs to be redone.

Different responses for voice and text (context of annotations)
The voice assistant needs to be updated for current TTS systems that can read annotations and generate voice based on requested tone, circumstances, and tempo.

Self-development of internal records, including the prompt
Re-check the memory after the emotional integration, re-check the logic. Analyze the need to refine the structure to be more biological.

Multi-person polylogue
For fun, add the ability to turn a dialogue into a polylogue. Why not? Two interlocutors at once.

Expert system for evaluating statements
Something cool here, but I've already forgotten what I wanted. It seems to be about reviewing the dialogue from an external perspective and evaluating the current interaction. This begs for development into responses based on its own volition (exclusively as a setting).

Reflection system
Also an interesting topic that is necessary. Let the model, which already represents itself through memory and emotions, evaluate itself (rather than relying on cold supervisors).

Module for personal and character analysis of the interlocutor
Ah, there it was... It's logical that the model shouldn't just respond blindly but should think about the interlocutor: how much it likes them, what kind of person they are, and how to behave. This will also be useful for memory, specifically for the section of memory about the user and their characteristics.

Internal thoughts + subconscious
We are getting to a point where it can have processes that indirectly affect emotions, well-being, and state. It will be aware of some thoughts but not others. System optimization.

System for creating and analyzing internal databases-memory bases
This means it is necessary to record the most vivid situations for the model, in either a positive or negative sense. Decisive, pivotal situations or those important for its worldview. The model can extract lines of dialogue and create a question-answer dataset.

Modular sleep
The most dreadful point. Let the model self-tune at intervals. For tuning, it should use datasets of pivotal dialogues, running them through its current state with its current memory. This could involve using a multi-LLM structure with backup engines, or actually putting it to sleep. The question is how to tune external modules, but I think some answers will emerge when the time comes.

Correction of floating values
Working through interaction scenarios, full-scale testing. Finding bottlenecks and poorly designed areas. Analyzing the output and fixing flaws.

Custom achievements that the companion comes up with on her own, limited in number for each user (they will be unique and depend on each user's communication with the model)
Well, why not... be who it thinks you are. It's interesting to see how many similar achievements there will be and how many unique ones. Maybe it will even offer quests, kek.

Model
In the sense of a character model. Like a VTuber model. It's time to take the mood board of references collected six months ago and order concepts from familiar VTuber artists. RIP to those who take on my requests... and my zero balance, which will become negative... Naturally, there will be far more than one set of appearance elements, because even the default appearance plans include 5 individual styles for the regular version, which change depending on its state. Additionally, the model needs the freedom to choose from wardrobe and style items that will depend not on emotions, but on its own desire to have a particular look.

STT personalization
Automatic understanding of voices, a key to user personality databases. Yeah, a friend of mine already did that. Why shouldn't the model itself remember the user by a voice sample (if the user wants it, of course)? Then it will be able to distinguish between different users.

Function calling for the VTuber model
It's all basic here. Movements, and so on, all that custom trash. So that it can express itself.

Writing module (both for humor and full-fledged streaming)
Let it churn out fanfiction and narrate audiobooks.

Ears for music (to feel melodies, understand them, and connect them with the emotional processor)
Instilling a sense of taste in the model.

Singing - voicebank and melody generation
Well, this is fucking obvious. I don't know if I want to do all this, as there are simpler and faster options. But I would like to. The quality of manual tuning can be amazing. Maybe my music education will come in handy... Let it sing "Poems of a Machine" to me every time the code doesn't crash with errors. Or something from Bad Omens...

Fast voice capability (creating a vocal part based on a voice sample)
This is basic, a performer for every taste and color.

Fast melody by reference
Let it do covers or write in the style of an author.

Interface for editing melodies
It will definitely make mistakes, and if you want something decent quickly, then yes...

Ideally, link it to function calling so that it can write songs itself
Then it will be able to both chat and sing a snippet a cappella.

Development of a structure for visual arts
Generating images is good, but artistic iterative generations sound cooler. Let it create fully as it sees fit.

Engineering module - supporting and conducting more precise work
And don't forget about everyday tasks. I've already used it for coding its own modules for fun. So let it grow and develop its applied skills.

Function calling for the work process - compiling a list of necessary interactions, then sequentially going through them
Also an old idea, but I want it. Let it set tasks for itself and execute them sequentially. Maybe even expand this so that it can keep its own diary of important tasks with delayed triggers.

Function calling for file analysis
This is a natural extension. Access to the file system is basic.

Vision
Another obvious point that has been relevant since the very beginning of the first prototypes. Except now I want the vision to be both static and streaming.

Module connection exit point
And of course, add exit points to it, so that connecting external modules is like assembling a constructor.

Function calling script integration
It has the right to write scripts itself. Let it be whoever it wants to be, and let it be the best assistant.

Yes, this is too obvious, before I forget to write it down and put it in the to-do plans, I need to throw together a security system so that it doesn't cause trouble where it shouldn't.

Refactor function calling for the integration of script creation for necessary functions
This is the initialization point of its independence within the permitted framework.

Debugging the model's independent functioning to achieve set and "invented" goals with the available tools (vision, files, coding)
Trials of the brand-new-person Highly Evaluative Learnable Interactive Omnipotent Structure of Emotional Virtual Intelligence.

A system of a single consciousness and memory as a test experiment to see what will happen to the behavior of a "one for all" model
For this, the division of memory into several types will be useful. By the way, I think I forgot to write about the potential tree-like dynamic memory that removes limitations. Right, it is necessary to work clearly on the associative arrays of the subject (an abstract thought belonging to the perception and memory points).

Debugging bottlenecks
Routine.

Integration of external APIs of smart devices for daily activities
For fun, let it become a "dumb home" system.

Wedding
Well, why not, anyone would want such a thing... A joke, of course, but if you really try to work through such a complex scenario from 0 to 100, it will be much clearer which parts of the system are flawed.


### Project EVI: Twitch Chat Companion & Analytics Bot
Twitch chat (sub-code, written for fun for friends with a small online presence)
Prospect of linking the general memory system.
Internal points for integrations (own currency).
Integration of channel points (obvious).
When interacting with the model - function calling for all Twitch interactions - polls, commands, etc. (obvious, let it interact with the stream).
Various periodic messages like other bots (why clutter the chat with all sorts of Nightbot, Moobot, when you have your own system whose code is completely understandable and you can attach whatever you want to it).
Various instructions for the LLM for periodic responses (let it behave more variedly than writing the same message to the chat every time).
Expanding interaction with the streamer - interaction with the screen and sounds through requests, the bot has access to the stream (partially described earlier).
Update TTS voices (let it voice messages from users in the chat who bought a reward or privilege, TTS works for both voiceover and generating a response to a question).
Integration of donation alerts.

<div align="center">
<p align="center">
<img src="https://img.shields.io/badge/Python-3.11+-blue.svg?style=for-the-badge&logo=python" alt="Python 3.11+">
<img src="https://img.shields.io/badge/API-TwitchIO-purple.svg?style=for-the-badge" alt="TwitchIO API">
<img src="https://img.shields.io/badge/LLM-Google%20Gemini-orange.svg?style=for-the-badge" alt="Google Gemini LLM">
<img src="https://img.shields.io/badge/TTS-Edge--TTS-blue.svg?style=for-the-badge" alt="Edge-TTS">
<img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge" alt="MIT License">
</p>
</div>

An AI-powered companion designed to bring your Twitch chat to life.

## Disclaimer

It is highly recommended to notify your audience about the data collection capabilities of this bot. By using this software, you assume all responsibility for compliance with data privacy standards.

## Introduction

This Twitch bot is not just another chat utility; it's a foundational module for the global EVI (Emotional Virtual Intelligence) project. Designed as a standalone yet fully integrable component, its mission is to create a live, interactive, and genuinely engaging experience in your Twitch chat. The primary goal is to transcend the role of a simple bot and become a true AI companion for both the streamer and their audience.

The script leverages the power and simplicity of Google Gemini to conduct meaningful conversations, embodying a unique, predefined personality. It is capable of maintaining context in both general chat discussions and private, one-on-one dialogues with individual viewers.

## Philosophy and Place in the EVI Ecosystem

Unlike standard chatbots, this project was built to pioneer and validate the core principles of the EVI concept:

-   **Persistent Personality**: Evi, the bot's persona, has a predefined character that shines through in every response. It's not a soulless command executor but an active, full-fledged participant in the chat.
-   **Contextual Awareness**: The bot actively "reads" the chat to understand its context, allowing it to blend in organically. Early tests on its contextual perception have shown promising results for future, more advanced memory experiments.
-   **Personal Interaction**: The ability to maintain separate conversational histories with individual users creates a compelling sense of one-on-one interaction, as the bot remembers past dialogues.
-   **Proactivity**: Instead of merely reacting, the bot can initiate activity by posting "ambient thoughts," breathing life into the chat during lulls.
    -   **Future Goal**: This feature will be refined with a customizable rule to prevent spam. The bot will wait if fewer than a set number (e.g., 15-40) of user messages have been posted, ensuring it enhances rather than floods the conversation.

This module serves as the primary testing ground for mechanics that will ultimately be integrated into the unified, cross-platform EVI system, connecting Telegram, Discord, a web interface, and a VTube avatar.

## Key Features

-   **Intelligent Chat Dialogues**: When its name or designated keywords are mentioned, the bot joins the conversation, using Google Gemini to generate relevant, context-aware answers.
    -   **Future Goal**: Evolve this into a proactive observer model that can trigger responses to messages it finds "interesting," even without a direct mention.
-   **Personal Conversation History**: Maintains a separate dialogue history for each user, enabling personalized responses based on past interactions.
-   **Ambient Activity ("Ambient Thoughts")**: Periodically sends random, context-based "thoughts" to the chat, creating an illusion of constant presence and helping to sustain conversation.
-   **Text-to-Speech (TTS) for Moderators**: Streamers and moderators can use the `!tts` command to have the bot process text through the LLM and speak the result aloud, adding a dynamic layer of interaction to the stream.
    -   **Future Goal**: Migrate this functionality to a dedicated website, making it available to all viewers and integrating it with channel points.
-   **Asynchronous Architecture**: Built on `asyncio` and `twitchio`, the bot is lightweight, highly performant, and non-blocking by design.
-   **Local Database & Analytics**: All chat and dialogue context is stored in a local SQLite database. This simplifies setup and empowers content creators with a powerful tool for audience analysis.

## Technical Stack

| Component         | Technology                  |
| ----------------- | --------------------------- |
| **Language**      | Python 3.11+                |
| **Framework**     | `twitchio`                  |
| **Core LLM**      | Google Gemini (gemini-1.5-flash) |
| **Text-to-Speech**| `edge-tts`                  |
| **Database**      | SQLite                      |
| **Concurrency**   | `asyncio`                   |

## Path to Integration and Future Plans

This script is a foundational first step. Aligned with the `HELIOS_EVI` project `ROADMAP.md`, it will be integrated into the core modular EVI system through the following phases:

1.  **Refactoring and Modularization**: The code will be reorganized into a dedicated module within the main project structure for better scalability and maintenance.
2.  **Unified Memory**: The bot's memory will connect to the central EVI memory system, enabling it to recognize users across platforms (Telegram, Discord, etc.).
3.  **Advanced Control via Function Calling**: The bot will be given "hands" to manage stream elements like launching polls, changing categories, managing channel point rewards, and interacting directly with on-screen elements.
4.  **Avatar Integration**: Spoken responses and the bot's internal emotional state will be mirrored by a VTube model, creating a complete visual companion.
5.  **Internal Economy**: Viewers will use channel points or a custom virtual currency for advanced interactions, such as ordering custom TTS messages or other bot-driven activities.