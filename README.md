# NovaE²E — Quantum Encrypted Messaging

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

NovaE²E is a quantum-encrypted, self-hosted end-to-end encrypted messaging platform built on the Wire protocol.

## Features

- **Quantum Encryption** — Post-quantum cryptographic algorithms
- **MLS Protocol** — Messaging Layer Security for group messaging
- **Self-Hosted** — Full control over your data
- **Zero Trust** — No trust assumptions, verify everything
- **Forward Secrecy** — Past messages stay secure even if keys are compromised
- **Post-Compromise Security** — Automatic recovery from key compromise

## Architecture

- **Frontend**: TypeScript, React
- **Backend**: Wire Server (self-hosted)
- **Encryption**: MLS + Quantum-resistant algorithms
- **Deployment**: Docker containers on Hetzner Cloud

## Development

```bash
# Install dependencies
yarn install

# Start development server
yarn start

# Build for production
yarn bundle:prod
```

## License

This project is licensed under the GNU General Public License v3.0 — see the [LICENSE](LICENSE) file for details.

Based on [Wire](https://wire.com) open-source messenger.

© 2026 NovaOS — [novaos.cloud](https://novaos.cloud)
