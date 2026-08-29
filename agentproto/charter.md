# Agent Communication Protocols (agentproto) Proposed Charter

The Agent Communication Protocols (agentproto) Working Group will work on defining protocol building blocks for enabling interoperability for AI Agent applications across the Internet. An AI agent is an autonomous, adaptive intelligent software system that uses AI models to complete a specific task. AI Agents often interact with users via chat or voice, performing tasks based on the flow of the conversation. To complete tasks on behalf of a human user or another AI agent, they can independently make decisions, execute actions, and interact with other AI agents and tools.

With the expansion of communication over the Internet between AI Agents and external resources that can be tools or other AI Agents, reliable communications across platforms and vendors becomes increasingly important. The role of the agentproto working group is to facilitate such interoperability so that tools and agents can be provided by multiple vendors.

# Key Considerations

There are several considerations that are unique to AI Agent applications that need to be addressed while working on developing the building blocks:

- AI Agents act as autonomous software entities that may need to be authenticated independently of the users they represent. Establishing verifiable agent identity that is distinct from user identity enables independent revocation of agent access, scoping of agent permissions to a subset of user permissions, and auditability of agent-initiated actions distinct from user-initiated actions.

- AI Agents possess unique and specialized functional capabilities which can be enhanced by collaboratively working with other agents or tools. This brings new considerations for how these specialized capabilities can be leveraged to select AI agents or tools for collaboration, initiate communication and maintain interactions, including across network boundaries.

- Interactions of AI Agents with users, other AI Agents, and tools can be long-lived, utilize significant amounts of context across various modes (text, audio, video), and require very low latency (including fast barge/interruption times). This introduces new considerations around reliability, transport session management, and data transport.

- To protect data exchanged between AI Agents (and between AI Agents and tools) over potentially untrusted networks, particularly when handling sensitive information (such as personal data or conversational context), mechanisms are required to establish and verify identity, ensure confidentiality, integrity, authenticity of the exchanged data, and delegated authorization across AI Agent chains. This introduces new considerations around protocol-level security and privacy mechanisms.

The scope of the working group includes agent-to-agent and agent-to-tools communication protocols. The working group will document common use-cases to derive requirements for these protocols. Human-agent communication protocols — specifically the protocol-level mechanisms for establishing sessions, negotiating modalities, and exchanging multimodal data between a human user and an AI Agent — are also in scope.

# Deliverables

The working group will produce the following standards track and informational documents.

## Agent Context Propagation Protocol (Standards Track)

A standards-track protocol for the propagation of interaction context across trust boundaries and across modalities, enabling multiparty agent communications. This protocol serves as a signaling foundation for context continuity and correlation in user-to-agent, agent-to-agent, and agent-to-tool interactions, allowing context to follow participants as they move between devices or over time.

The specification will cover two parts:

* Context management primitives: providing context correlation, enabling agents to link related interactions across participants and over time; full context lifecycle management, including establishment, update, termination, and revocation of propagation relationships; and defining propagation behavior across participants, including handling of failures and unreachable parties.

* Transport bindings: specifying how the context and its associated metadata are carried over modern IETF application transfer protocols, such as QUIC, WebTransport, WebRTC or MOQ, based on the anticipated use cases.

The protocol is designed to be used by existing application-layer agent communication protocols (e.g., MCP and A2A maintained the by Linux Foundation) through well-defined extension points, rather than replacing them.

## Framework (Informational)

This informational framework will:

* Define the terms used by the protocol deliverable.

* Describe basic use cases and requirements that derive the context management primitives covered by the protocol deliverable.

* Describe the functional blocks the protocol deliverable assume, and their relationships.

# Coordination

This working group is expected to closely coordinate with other related IETF working groups on dependencies of the framework and the agent context propagation protocol, including security, transport, and discovery aspects:

* **Security:** Web Authorization Protocol (OAuth), webbotauth, WIMSE - on identity, authorization, and security considerations.
* **Transport:** WebTransport, MoQ, QUIC, TSVWG - on data transport.
* **Discovery and Operations:** INT area, OPS area - on agent discovery and operational considerations.

If the working group needs any changes to or extensions of protocols specified by other working groups, those issues will be raised with the relevant working groups for decisions on how best to handle them.


# Out of Scope

The following topics are explicitly out of scope for this working group:

- Implementation details of AI Agents, including definition of AI models, backend AI infrastructure network and protocols, agent reasoning algorithms, or tool-specific business logic.

- Standardization of agent behavior, decision-making, or planning semantics.

- AI agent behavioral security (e.g., preventing the AI model itself from hallucinating, though mitigating the impact of hallucinations via protocol-level user confirmation is in scope).

- The design of human to agent user interfaces, client application UX, or the rendering of agent outputs on end-user devices
