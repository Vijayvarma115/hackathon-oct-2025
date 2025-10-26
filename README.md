**Here is a complete `README.md` file for your project, structured for clarity and immediate use. This README covers the problem statement, objectives, phases, architecture, tech stack, setup instructions, and possible future extensions.

***

# RAG-Enabled Agentic AI Conversational Assistant for Intelligent Customer Support

## Overview

This project delivers an open-source conversational AI assistant designed for modern customer support, combining Retrieval-Augmented Generation (RAG), agentic workflows, and seamless human handoff. It integrates with leading open-source tools like Chatwoot (for customer messaging and live agent handoff), n8n (for workflow automation), Pipecat (for voice AI pipelines), and LiveKit (for real-time voice transport), delivering scalable, cost-effective intelligent support across text and, eventually, voice channels.

***

## Problem Statement

Most customer service bots fail to provide personalized, human-like support for complex queries, and often lack seamless escalation to human agents. Voice support and hybrid automation–human workflows are rarely efficiently combined in current open platforms. This project solves these challenges by building a modular, agentic system that:

- Autonomously resolves customer queries with RAG-based, contextual AI.
- Seamlessly transfers conversations to human agents on Chatwoot based on configurable triggers, and returns to automation when human intervention is complete.
- Is designed for future extension to real-time voice interactions using ultra-low-latency streaming and speech technologies.

***

## Project Objectives

- **Autonomous Query Resolution:** RAG-powered LLM chatbot delivers accurate, contextually grounded responses.
- **Intelligent Human Handoff:** Automated detection and routing for complex, sentiment-driven, or user-requested escalations to human agents.
- **Workflow Continuity:** Automated return to bot after human resolution, closing the loop and ensuring complete customer journey coverage.
- **Voice Agent Extension (Planned):** Voice pipeline integration for real-time speech support, with the same agentic handoff and RAG context.

***

## Architecture

### Phase 1: RAG-Based Text Chatbot with Human Handoff

| Layer         | Tool/Technology                                   |
|---------------|---------------------------------------------------|
| Messaging     | Chatwoot                                          |
| Orchestration | n8n                                               |
| RAG/Vector DB | FAISS / Pinecone / ChromaDB                       |
| LLM           | GPT-4 / Llama 3 / Mistral                         |

- **Chatwoot:** Multichannel messaging, agent dashboards, and agent routing.
- **n8n:** Modular, no-code workflows for RAG, API integration, and agent handoff logic.
- **RAG Layer:** Semantic search over knowledge base (FAQs/tickets/policies).
- **Agentic AI:** Multi-step planning, validation, and tool-augmented actions.
- **Human Handoff:** Triggered by low confidence, keywords, sentiment, or unresolved intent—automatically assigning to agents via Chatwoot.

### Phase 2: Voice Agent Integration (Planned)

| Layer           | Tool/Technology                          |
|-----------------|------------------------------------------|
| Voice Pipeline  | Pipecat                                  |
| Real-time Voice | LiveKit                                  |
| STT             | Whisper / AssemblyAI / Deepgram          |
| TTS             | Cartesia / ElevenLabs / Coqui TTS        |
| NLU/DM          | Rasa / spaCy (optional)                  |

- Real-time speech pipeline for customer calls, with RAG-powered conversational context and automated handoff to live agents when needed.

***

## Key Features

- Modular open-source architecture (cloud or on-premise).
- Scalable vector database for fast RAG context.
- Seamless, configurable escalation to human support.
- Future-proof: Designed for easy extension to full voice agent flows.
- Cost-effective: All core components are open-source, licensing optional for advanced LLMs/APIs.

***

## Setup & Installation

### Prerequisites

- Docker & Docker Compose (for easy deployment)
- Accounts/Keys for any cloud APIs or LLM providers (if not using only open-source LLMs)
- Node.js and npm/yarn (for n8n workflows if running from source)
- Optional: Python for FAISS/ChromaDB indexing scripts

### Core Services Used

- [Chatwoot](https://www.chatwoot.com/) – Customer conversation & agent management.
- [n8n](https://n8n.io/) – Workflow orchestration and RAG logic.
- [FAISS](https://github.com/facebookresearch/faiss), [Pinecone](https://www.pinecone.io/), or [ChromaDB](https://www.trychroma.com/) – Vector DB for semantic document retrieval.
- [OpenAI GPT-4](https://openai.com/), [Llama 3](https://llama.meta.com/llama3/), [Mistral](https://mistral.ai/) – LLM backends.
- (Planned) [Pipecat](https://github.com/pipecat-ai/pipecat), [LiveKit](https://livekit.io/) for real-time voice support.

### Quick Start (Docker Compose)

1. **Clone the Repository**
   ```sh
   git clone <your-repo-url>
   cd <your-repo>
   ```

2. **Configure Environment Variables**
   - Copy `file.env` to `.env`
   - Set Chatwoot, n8n, LLM, and vector DB keys as needed.

3. **Start the Core Services**
   ```sh
   docker-compose up -d
   ```

4. **Import/Configure n8n Workflows**
   - Open n8n dashboard
   - Import prebuilt RAG and handoff workflows, configure endpoints for Chatwoot/LLM/vector DB.

5. **Configure Chatwoot**
   - Add channels (web, WhatsApp, email, etc.)
   - Set up your agent teams and automation triggers.

6. **Test Locally**
   - Use the included `index.html` local test page to trigger chatbot via Chatwoot widget.
   - Confirm handoff triggers and full workflow execution.

### Extending to Voice (Phase 2)

- Add Pipecat and LiveKit services to the Docker Compose stack.
- Configure integration with n8n for voice event triggers.

***

## Example Workflow

1. **User Message:** Enters via Chatwoot widget/channel.
2. **n8n Workflow:** Receives webhook, preprocesses query, triggers semantic document retrieval.
3. **LLM:** Consumes RAG-augmented prompt; generates grounded response.
4. **Human Handoff (if needed):** Triggered by confidence score, keywords, user request, or sentiment.
5. **Agent Handles Conversation:** Chatwoot routes to live agent.
6. **Return to Bot:** After agent resolution, bot follows up if needed.
7. **(Planned) Voice Conversion:** All logic above extended to real-time speech interaction.

***

## Contributing

Contributions, feature requests, and feedback are welcome via Issues/PRs!

- To add a new vector DB, LLM, or channel, follow the modular guidelines in `n8n` workflow examples.
- Document new workflow patterns or voice extensions in `/docs`.

***

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

***

## Acknowledgements

- Open-source communities of Chatwoot, n8n, Pipecat, LiveKit, FAISS, Pinecone, ChromaDB, OpenAI, Meta AI, Mistral.
- Inspiration from pioneering hybrid AI-human customer service architectures.

***

## Project Status

- **Phase 1:** RAG chatbot with human handoff via Chatwoot and n8n — functional.
- **Phase 2:** Voice support via Pipecat + LiveKit — in progress/planned.

***

## Short Description

"This project builds an open-source RAG-enabled agentic AI chatbot with intelligent human handoff using Chatwoot and n8n, extending to real-time voice agents via Pipecat and LiveKit. The system autonomously resolves customer queries, seamlessly transfers complex cases to human agents, and provides voice-based conversational support for scalable, accessible customer service."

---

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/53740383/bd8ed962-e943-42a4-a36a-77b7a12f2d41/image.jpg?AWSAccessKeyId=ASIA2F3EMEYERD4WPXHR&Signature=9NzoDRiyrjv4zGAwnpYtn1nAs7s%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEM%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJHMEUCIQDBbRT%2FCUJx8WtcVD%2FrhrWDcvjAyuPllw3c%2BiNjtraUDAIgSEWbJ2efG%2BI9Y65Rm%2BVvtTBYRZaUYmoRbxc9SodkiWkq%2FAQIh%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgw2OTk3NTMzMDk3MDUiDP3PbYiP0hU7sb%2B3%2FCrQBNUcoxaVDEXdTVjpDIrQWvaZZKvlTU5UH39OT0rzLiWLkoKbJfzIeTJOCICaBcSgLkrB8G%2BtMrjG3Ws3dVddJdcd8gkaDSf7cjpQhhZe%2FV0gOYB%2FFydGWj0SzpnFFsnUP8KSP1Fr9W8n3Knwbo6vfW2FE%2BwEMa8BUn9IO9B0t%2FnQDGdhWRoskOLKyPO0XuVaP4Zos7dneJ9zKsK6maHe0n6G9OiLceMF5CoNb%2BLSFl%2FZEjnhCFZ29Uh6a2FQ2DucDC7bIwc6Cof0VTzstQ0cJ4DKK4JhmzgtvF8pVcH92VQF0p9B6gJyLTPccMhrrE55K8kAE2vhW7rs1Xm%2FOe0PmZWlz9LBFr5mg3Z%2FFuqX5XqhW5xtpVZdxW07WKaZ%2BeOE3z8u3CJrcbDEbxwEDxq2I1KnmPOzY6xlP%2FHpcC0PR1S4OLPKNqQvrmqC0gPz%2FBmhZXzUG15baME6TteJTu8QwLMsKZgW7bap%2FDhNe4Qt%2FCuykU97Xecsj8HlRE2xT5QGdkyRGlt3HPUuKAgwH%2BvLg2bPQe3DP7ohYHyPcn1uXt8nKEU5b2MZYPRPAOxGR12HHgz5KsIlendf%2FeUDNCDOQT06aXuwXvYna5nKnR2i0AFoA7kvQzfNwFgvw%2BoBUPlakr8qeADvbJDk%2Fh1dLjJrVuJvoiF6pYTipjbDrUnEEN5Yp1lVIPNqZhUpwr5LUj9j8zqi7%2B23M1lXP3%2FWsyvFLp5qbL7VzBvIWUS8p9Cx7U4KceSte7q6upGvcTZJdWt1uJG77hwZbrfgoEKYKGB1qgYwyvX2xwY6mAF8FUWDxqnRvqgB6YuPWYh3EFpe9TbSaf5JFUaPxbyAgBO1D8h1OD6psmkXRuhFznY7rbgsQSDcOkCqbt%2BDI0BreY5378YMERoxfzdf5EbJs5A8V3m7d2GuM1DeRyq4TbSX%2F9ime1BwWd9fNDGQf9%2Fm9n%2FIOc7HAZMdKOONZ3PG%2Fa6dSR5GgT12VyYlk2upeVLNJrS4AzPSMA%3D%3D&Expires=1761461551)
[2](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/53740383/583eb4e7-4497-40c2-aea9-529b0ccc9181/image.jpg?AWSAccessKeyId=ASIA2F3EMEYERD4WPXHR&Signature=L4qABQkAj1o%2Fi5UuYfwS9gyjWQo%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEM%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJHMEUCIQDBbRT%2FCUJx8WtcVD%2FrhrWDcvjAyuPllw3c%2BiNjtraUDAIgSEWbJ2efG%2BI9Y65Rm%2BVvtTBYRZaUYmoRbxc9SodkiWkq%2FAQIh%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgw2OTk3NTMzMDk3MDUiDP3PbYiP0hU7sb%2B3%2FCrQBNUcoxaVDEXdTVjpDIrQWvaZZKvlTU5UH39OT0rzLiWLkoKbJfzIeTJOCICaBcSgLkrB8G%2BtMrjG3Ws3dVddJdcd8gkaDSf7cjpQhhZe%2FV0gOYB%2FFydGWj0SzpnFFsnUP8KSP1Fr9W8n3Knwbo6vfW2FE%2BwEMa8BUn9IO9B0t%2FnQDGdhWRoskOLKyPO0XuVaP4Zos7dneJ9zKsK6maHe0n6G9OiLceMF5CoNb%2BLSFl%2FZEjnhCFZ29Uh6a2FQ2DucDC7bIwc6Cof0VTzstQ0cJ4DKK4JhmzgtvF8pVcH92VQF0p9B6gJyLTPccMhrrE55K8kAE2vhW7rs1Xm%2FOe0PmZWlz9LBFr5mg3Z%2FFuqX5XqhW5xtpVZdxW07WKaZ%2BeOE3z8u3CJrcbDEbxwEDxq2I1KnmPOzY6xlP%2FHpcC0PR1S4OLPKNqQvrmqC0gPz%2FBmhZXzUG15baME6TteJTu8QwLMsKZgW7bap%2FDhNe4Qt%2FCuykU97Xecsj8HlRE2xT5QGdkyRGlt3HPUuKAgwH%2BvLg2bPQe3DP7ohYHyPcn1uXt8nKEU5b2MZYPRPAOxGR12HHgz5KsIlendf%2FeUDNCDOQT06aXuwXvYna5nKnR2i0AFoA7kvQzfNwFgvw%2BoBUPlakr8qeADvbJDk%2Fh1dLjJrVuJvoiF6pYTipjbDrUnEEN5Yp1lVIPNqZhUpwr5LUj9j8zqi7%2B23M1lXP3%2FWsyvFLp5qbL7VzBvIWUS8p9Cx7U4KceSte7q6upGvcTZJdWt1uJG77hwZbrfgoEKYKGB1qgYwyvX2xwY6mAF8FUWDxqnRvqgB6YuPWYh3EFpe9TbSaf5JFUaPxbyAgBO1D8h1OD6psmkXRuhFznY7rbgsQSDcOkCqbt%2BDI0BreY5378YMERoxfzdf5EbJs5A8V3m7d2GuM1DeRyq4TbSX%2F9ime1BwWd9fNDGQf9%2Fm9n%2FIOc7HAZMdKOONZ3PG%2Fa6dSR5GgT12VyYlk2upeVLNJrS4AzPSMA%3D%3D&Expires=1761461551)
[3](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/images/53740383/25455649-9ee1-4cb9-8749-5dd10d780ed9/image.jpg?AWSAccessKeyId=ASIA2F3EMEYERD4WPXHR&Signature=lSTQV3WBTpD7MUt92XwGTcpz6eM%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEM%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJHMEUCIQDBbRT%2FCUJx8WtcVD%2FrhrWDcvjAyuPllw3c%2BiNjtraUDAIgSEWbJ2efG%2BI9Y65Rm%2BVvtTBYRZaUYmoRbxc9SodkiWkq%2FAQIh%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARABGgw2OTk3NTMzMDk3MDUiDP3PbYiP0hU7sb%2B3%2FCrQBNUcoxaVDEXdTVjpDIrQWvaZZKvlTU5UH39OT0rzLiWLkoKbJfzIeTJOCICaBcSgLkrB8G%2BtMrjG3Ws3dVddJdcd8gkaDSf7cjpQhhZe%2FV0gOYB%2FFydGWj0SzpnFFsnUP8KSP1Fr9W8n3Knwbo6vfW2FE%2BwEMa8BUn9IO9B0t%2FnQDGdhWRoskOLKyPO0XuVaP4Zos7dneJ9zKsK6maHe0n6G9OiLceMF5CoNb%2BLSFl%2FZEjnhCFZ29Uh6a2FQ2DucDC7bIwc6Cof0VTzstQ0cJ4DKK4JhmzgtvF8pVcH92VQF0p9B6gJyLTPccMhrrE55K8kAE2vhW7rs1Xm%2FOe0PmZWlz9LBFr5mg3Z%2FFuqX5XqhW5xtpVZdxW07WKaZ%2BeOE3z8u3CJrcbDEbxwEDxq2I1KnmPOzY6xlP%2FHpcC0PR1S4OLPKNqQvrmqC0gPz%2FBmhZXzUG15baME6TteJTu8QwLMsKZgW7bap%2FDhNe4Qt%2FCuykU97Xecsj8HlRE2xT5QGdkyRGlt3HPUuKAgwH%2BvLg2bPQe3DP7ohYHyPcn1uXt8nKEU5b2MZYPRPAOxGR12HHgz5KsIlendf%2FeUDNCDOQT06aXuwXvYna5nKnR2i0AFoA7kvQzfNwFgvw%2BoBUPlakr8qeADvbJDk%2Fh1dLjJrVuJvoiF6pYTipjbDrUnEEN5Yp1lVIPNqZhUpwr5LUj9j8zqi7%2B23M1lXP3%2FWsyvFLp5qbL7VzBvIWUS8p9Cx7U4KceSte7q6upGvcTZJdWt1uJG77hwZbrfgoEKYKGB1qgYwyvX2xwY6mAF8FUWDxqnRvqgB6YuPWYh3EFpe9TbSaf5JFUaPxbyAgBO1D8h1OD6psmkXRuhFznY7rbgsQSDcOkCqbt%2BDI0BreY5378YMERoxfzdf5EbJs5A8V3m7d2GuM1DeRyq4TbSX%2F9ime1BwWd9fNDGQf9%2Fm9n%2FIOc7HAZMdKOONZ3PG%2Fa6dSR5GgT12VyYlk2upeVLNJrS4AzPSMA%3D%3D&Expires=1761461551)******
