# throttle-ai

## Operational Hierarchy
**Server-side NPM package**
  - Called when configuring listener port behavior
  - Monitors incoming agents and allocates permissions
    - If allowed, do nothing
    - If restricted, check for Auth
    - If unauthorized, return 403
  - Configured with permissions per resource
  - Local persistence (maybe a file for simplicity?)

**AI Agent**
  - The incoming query has to be managed by an Agent. Pure LLMs do not have the infrastructure to handle Auth
  - When allocating Query Browser resources, check if URI needs Auth
    - Agents can also hand off the auth process to user
  - Make query

**Web Interface**
  - User registers as either a server host or AI Agent
    - If AI Agent, opportunity to "subscribe" to servers for access to controlled resources
    - A key is distributed to the server and agent (?)
  - View analytics
  - Handle financial transactions, likely will be very difficult

## NPM Package
  - Applied as middleware to server infrastructure
  - .use(), .createStore(), etc takes a function as it's required argument
    - function called when a new request comes in
  - .config()-esque call likely necessary to initialize resources
  - Private API linkage for keys on registration (?)
  - Most package tooling is built in the native language
    - TS/JS has no threading so be aware
    - Implementation in a separate language might be an equal nightmare

## Web interface
  - This would likely best exist in an architecture that supports our own backend instead of a host
  - Scalability becomes an issue, but I think we need the flexibility
  - Little preference on language choice
  - A Single-Page Application would likely cause more issues than it's worth
  - Focused interfaces based on whether you're registered as a server or a client
  - Link to cloud AI instance / make API call to server to link

## Next Steps
  - Define architecture
  - Set up a test agent and server to interact with one another via natural language query
  - Agent blocking with flexibility to defend against non-AI scrapers
  - key generation and communication for all endpoints
  - Define security strategy