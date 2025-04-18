# Multi-Agent Reasoning Model

## Project Overview

The Multi-Agent Reasoning Model is a Python-based AI solution that employs multiple AI agents collaborating to generate optimal responses to user prompts. This system enhances reasoning capabilities through agent collaboration, Swarm Intelligence integration, and sophisticated conversation management.

## Core Components

### 1. Main Modules

- **reasoning.py**: The main script that handles the reasoning process, chat interactions, and user interface
- **swarm_middle_agent.py**: Implements the Swarm Framework integration for enhanced agent coordination
- **agents.json**: Configuration file for defining agent personalities, interaction styles, and other attributes

### 2. Key Features

#### Multi-Agent Collaboration
The system simulates collaborative reasoning between multiple AI agents, each with unique perspectives and expertise. Through structured discussion, verification, critique, and refinement, agents converge on high-quality responses.

#### Swarm Framework Integration
The Swarm Framework for Intelligence enhances agent coordination and execution through a lightweight, scalable architecture. Agents can dynamically hand off tasks to specialized agents, improving responsiveness and flexibility.

#### Agent Awareness
Agents are aware of each other, including their personalities, quirks, and capabilities. This allows them to answer questions about one another and provide a rich interactive experience.

#### Prompt Caching
The system leverages OpenAI's Prompt Caching to reduce latency and costs for repeated prompts. By caching the longest common prefixes of prompts, it improves processing time for subsequent requests.

#### Customizable Agents via JSON
Agents are fully configurable through the `agents.json` file, allowing customization of:
- System purpose
- Interaction style
- Ethical conduct
- Capabilities and limitations
- Context awareness
- Adaptability and engagement
- Responsiveness
- Additional tools and modules
- Personality traits and quirks

## Technical Implementation

### Agent Implementation (reasoning.py)

The `Agent` class in `reasoning.py` represents individual agents with methods for:
- Message management with token count limits
- Chat response handling
- Various reasoning actions:
  - `discuss`: Initial response formulation
  - `verify`: Accuracy verification
  - `critique`: Critical analysis of other agents' responses
  - `refine`: Response improvement based on feedback

The system uses advanced OpenAI models:
- `o1-preview-2024-09-12` for reasoning tasks
- `gpt-4o` for chat interactions

### Swarm Integration (swarm_middle_agent.py)

The `swarm_middle_agent.py` module implements the Swarm Framework integration with:
- Agent initialization from the JSON configuration
- Swarm client setup for managing agent interactions
- Dynamic agent handoffs for specialized tasks
- Parallel processing of agent activities
- Response blending functions

### Response Generation Process

#### Reasoning Logic Mode
1. **Initial Discussion**: Each agent independently formulates a response
2. **Verification**: Agents verify the accuracy of their own responses
3. **Critiquing**: Agents critique each other's verified responses
4. **Refinement**: Agents refine responses based on critique feedback
5. **Response Blending**: Refined responses are combined into a cohesive answer
6. **User Feedback Loop**: System incorporates user feedback for further refinement
7. **Context Retention**: Option to maintain conversation context for follow-ups

#### Swarm-Based Reasoning
Similar to the standard reasoning process but utilizes the Swarm framework for agent coordination, allowing:
- Dynamic agent handoffs
- Function execution by specialized agents
- Parallel processing of agent tasks
- Enhanced collaboration through Swarm's primitives (Agents and Handoffs)

#### Chat Mode
Allows direct conversation with individual agents:
- Agents maintain their unique personalities and interaction styles
- Retains conversation history within token limits
- Agents are aware of each other and can discuss other agents

### Utility Features

#### Token Management
- Uses `tiktoken` library for accurate token counting
- Manages conversation history to stay within token limits
- Provides token usage transparency after each response

#### Logging and Error Handling
- Customized logging with colored output for clarity
- Extensive error handling with retry mechanisms
- File and console logging for debugging

#### User Interface
- Interactive menu-driven interface
- Color-coded agent responses for easy identification
- Structured display of reasoning steps

## Technical Requirements

- **Python 3.10** or higher
- **OpenAI Python Library**
- **colorama** library for colored console output
- **tiktoken** library for token counting
- **Swarm** library for agent coordination

## Performance Optimization

### Prompt Caching
- Automatically caches prompts longer than 1,024 tokens
- Cached prompts remain active for 5-10 minutes of inactivity
- Significantly reduces processing time and computational resources
- Provides usage metrics for monitoring cache effectiveness

### Parallel Processing
- Agent tasks are executed concurrently where appropriate
- ThreadPoolExecutor is used for parallel agent operations
- Improves efficiency for independent tasks

## Configuration Details

### agents.json Structure
The JSON configuration file defines each agent with the following attributes:
- `name`: Unique identifier for the agent
- `system_purpose`: Primary role and objectives
- `interaction_style`: Communication approach, tone, and accuracy
- `ethical_conduct`: Ethical boundaries and privacy concerns
- `capabilities_limitations`: Transparency and tool availability
- `context_awareness`: Conversation memory and adaptation
- `adaptability_engagement`: Language matching and empathy
- `responsiveness`: Focus on objectives and problem-solving
- `additional_tools_modules`: Available tools and capabilities
- `personality`: Humor style, traits, quirks, and demeanor

## Usage Workflows

### Standard Workflow
1. Run `python reasoning.py`
2. Select from menu options:
   - Chat with an agent
   - Use reasoning logic
   - Use Swarm-based reasoning
3. Enter prompts and interact with the system
4. Choose whether to retain context for follow-up questions

### Advanced Usage
- Add custom agents by modifying the `agents.json` file
- Adjust token limits and retry parameters in the constants section
- Implement custom logging for specific debugging needs

## Future Extensibility

The system is designed for easy extension through:
- Adding new agents to the JSON configuration
- Implementing additional reasoning steps
- Integrating with other AI frameworks
- Extending the Swarm functionality with custom functions 