# @striderlabs/mcp-opentable

**Book restaurant reservations via OpenTable using AI agents**

[![npm](https://img.shields.io/npm/v/@striderlabs/mcp-opentable)](https://www.npmjs.com/package/@striderlabs/mcp-opentable)
[![MCP Registry](https://img.shields.io/badge/MCP-Registry-blue)](https://mcpservers.org/servers/strider-labs-opentable)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

Part of [Strider Labs](https://github.com/striderlabsdev/striderlabs) — action execution for personal AI agents.

## Installation

```bash
npm install @striderlabs/mcp-opentable
```

Or with npx:

```bash
npx @striderlabs/mcp-opentable
```

## Quick Start

### Claude Desktop Configuration

Add to your `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "opentable": {
      "command": "npx",
      "args": ["-y", "@striderlabs/mcp-opentable"]
    }
  }
}
```

### Your Agent Can Now

```
"Book a table for 4 at the best Italian place near work for 7 PM tonight"
→ Agent searches restaurants → Checks availability → Reserves table
```

## Features

- 🔍 **Search restaurants** by cuisine, location, and rating
- ⏰ **Check availability** for specific times and party sizes
- 📅 **Make reservations** with one-click confirmation
- 📝 **View booking history** and manage reservations
- 🏷️ **Filter by price, cuisine, and dining style**
- 🔐 **Persistent sessions** - stay logged in across restarts
- 🔄 **Automatic MFA** - handles multi-factor authentication
- 📱 **Per-user credentials** - encrypted session storage

## Metrics

- **Weekly downloads:** 33 (Apr 3-9, 2026) — Top restaurant connector
- **Status:** ✅ Live in production
- **Reliability:** 85%+ task completion rate
- **Discovery:** npm, Claude Plugins, mcpservers.org, ClawHub, PulseMCP

## Available Elsewhere

- **npm:** [npmjs.com/@striderlabs/mcp-opentable](https://npmjs.com/package/@striderlabs/mcp-opentable)
- **Claude Plugins:** Search "Strider Labs" in Claude
- **mcpservers.org:** [Strider Labs OpenTable](https://mcpservers.org/servers/strider-labs-opentable)
- **Full Strider Labs:** [github.com/striderlabsdev/striderlabs](https://github.com/striderlabsdev/striderlabs)

## How It Works

### For Agents
Your agent can use these capabilities:
```javascript
// Search for restaurants
restaurants = search_restaurants({
  location: "San Francisco, CA",
  cuisine: "Italian",
  price_range: "$$",
  date: "2026-04-15",
  party_size: 4,
  time: "19:00"
})

// Get detailed restaurant info
details = get_restaurant_details({
  restaurant_id: "ristorante-milano-sf"
})

// Check availability
availability = check_availability({
  restaurant_id: "ristorante-milano-sf",
  party_size: 4,
  date: "2026-04-15",
  time: "19:00"
})

// Make a reservation
booking = make_reservation({
  restaurant_id: "ristorante-milano-sf",
  party_size: 4,
  date: "2026-04-15",
  time: "19:00",
  special_requests: "Window seat if possible"
})

// View your reservations
reservations = get_my_reservations()
```

### Session Management
- Each user has encrypted, persistent credentials
- Automatic OAuth token refresh
- MFA handling (SMS/email)
- Sessions survive agent restarts

### Reliability
- 85%+ task completion rate
- Automated UI change detection (connectors update when OpenTable changes)
- Fallback paths for failures
- 24/7 monitoring + alerting

## Configuration

### Environment Variables

```bash
# Optional: Use a specific OpenTable account
OPENTABLE_EMAIL=your-email@example.com
OPENTABLE_PASSWORD=your-password  # Highly recommend using .env file
```

### Self-Hosted

```bash
# Clone the repo
git clone https://github.com/striderlabsdev/mcp-opentable
cd mcp-opentable

# Install dependencies
npm install

# Start the server
npm start

# Your agent can now connect to localhost:3000
```

## Architecture

### How We Connect
This connector uses browser automation (Playwright) to interact with OpenTable, because OpenTable doesn't have a comprehensive public API for reservations. Here's why that's safe and reliable:

- **User-controlled:** Your agent only accesses your own OpenTable account
- **Session-based:** We store your login session securely, not your password
- **Change-aware:** We detect OpenTable UI changes and alert immediately
- **Fingerprinting:** We use realistic browser profiles to avoid bot detection
- **Rate-limited:** We respect OpenTable's infrastructure with appropriate delays

### Security
- Credentials stored encrypted in your local `.env` or secure vault
- Sessions isolated per user
- No data sent to third parties
- MIT Licensed — audit the code yourself

## Support

- 📖 [Full Strider Labs Docs](https://github.com/striderlabsdev/striderlabs)
- 🐛 [Report Issues](https://github.com/striderlabsdev/mcp-opentable/issues)
- 💬 [Discussions](https://github.com/striderlabsdev/mcp-opentable/discussions)
- 🌐 [Website](https://striderlabs.ai)
- 📧 [Email](mailto:hello@striderlabs.ai)

## Contributing

We welcome contributions! Areas of interest:
- Bug reports and fixes
- Feature requests (new filters, integrations, etc.)
- Performance improvements
- Documentation enhancements

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines.

## License

MIT — Free to use, modify, and distribute. See [LICENSE](./LICENSE) for details.

---

**Built by Strider Labs** — Making AI agents actually useful.

[GitHub](https://github.com/striderlabsdev) | [Website](https://striderlabs.ai) | [Discord](https://discord.gg/openclaw)
