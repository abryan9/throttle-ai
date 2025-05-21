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