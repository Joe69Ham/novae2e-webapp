<!-- nx configuration start-->
<!-- Leave the start & end comments to automatically receive updates. -->

# General Guidelines for working with Nx

- When running tasks (for example build, lint, test, e2e, etc.), always prefer running the task through `nx` (i.e. `nx run`, `nx run-many`, `nx affected`) instead of using the underlying tooling directly
- You have access to the Nx MCP server and its tools, use them to help the user
- When answering questions about the repository, use the `nx_workspace` tool first to gain an understanding of the workspace architecture where applicable.
- When working in individual projects, use the `nx_project_details` mcp tool to analyze and understand the specific project structure and dependencies
- For questions around nx configuration, best practices or if you're unsure, use the `nx_docs` tool to get relevant, up-to-date docs. Always use this instead of assuming things about nx configuration
- If the user needs help with an Nx configuration or project graph error, use the `nx_workspace` tool to get any errors

<!-- nx configuration end-->

# Repository Structure

This is an Nx monorepo with the following structure:

```
apps/
├── webapp/           # React frontend application
└── server/           # Node.js/Express backend API
libraries/
└── core/             # @wireapp/core - Wire's communication core library
```

## Core Library (`@wireapp/core`)

Located in `libraries/core/`, this is Wire's communication core library that provides:
- Account authentication and management
- WebSocket connections for real-time communication
- Protocol message handling (send/receive Protobuf messages)
- Cryptographic operations for secure messaging

The webapp depends on this library for all backend communication. When making changes to core functionality:
- Run tests: `nx run core-lib:test`
- Build the library: `nx run core-lib:build`
- Check for circular dependencies: `nx run core-lib:check:circular-dependencies`

# NovaE²E (our fork) – commands and notes

Moved here on 26.10.2026 from `/opt/CLAUDE.md`, so it only loads when working in this repo.

```bash
yarn install                              # Install (Yarn 4.12+, Node 24.10+)
yarn start                                # Dev server (nx serve server)
yarn dev                                  # Dev with library watching
yarn build:prod                           # Production build
yarn bundle:prod                          # Bundle webapp
yarn test                                 # All tests (nx run-many -t test)
yarn lint / yarn lint:fix                 # ESLint
yarn e2e-test / yarn e2e-ui               # Playwright E2E tests
yarn type-check                           # TypeScript check (nx run-many -t type-check)
nx run core-lib:test                      # Test core library only
nx run core-lib:check:circular-dependencies
```

Always run tasks via `nx` (or `yarn` scripts that call nx), not underlying tooling directly.

- `apps/webapp/`: React + TypeScript frontend (Emotion CSS-in-JS, i18next, Service Worker).
- `apps/server/`: Node.js backend API (Protobuf protocol, REST).
- `libraries/core/`: `@wireapp/core`, Wire protocol, WebSocket, MLS plus post-quantum Kyber768. Handles all cryptographic operations, account auth and real-time communication.
- `libraries/config/`: shared configuration.
- Default nx project: `webapp`.
