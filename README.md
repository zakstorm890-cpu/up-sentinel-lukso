# UP Sentinel 🛡️

**A security & permission checker for LUKSO Universal Profiles.**

UP Sentinel lets anyone paste a Universal Profile address and instantly see
every controller key, dApp, or secondary wallet that has been granted
access to it — decoded directly from the LSP6 Key Manager's on-chain
permission data.

Universal Profiles are powerful because of their flexible permission
system, but that same flexibility makes it easy to lose track of who can
actually do what. A dApp or browser extension might hold `TRANSFERVALUE`,
`CHANGEOWNER`, or `SUPER_SETDATA` permissions without the user realizing
what that access actually means. UP Sentinel exists to make that visible
at a glance, for technical and non-technical users alike.

## Features

- 🔍 **One-click scan** — paste any Universal Profile address, no wallet
  connection or signature required
- 🔴 **High-risk detection** — automatically flags controllers with
  fund-moving or ownership-changing permissions (`TRANSFERVALUE`,
  `CHANGEOWNER`, `EDITPERMISSIONS`, `SUPER_SETDATA`, etc.)
- 🟢 **Safe/limited access grouping** — clearly separates low-risk,
  read-only, or restricted controllers
- 🔁 **Smart resolution** — if you paste an LSP6 Key Manager address
  instead of the profile account, it automatically follows `target()`
  to the correct Universal Profile
- 🔒 **Fully read-only** — no transactions, no signatures, no wallet
  connection. It only reads public on-chain data.
- ⚡ **Zero backend** — a single self-contained HTML file. No servers,
  no data collection, nothing to install.

## How it works

UP Sentinel reads the standard LSP6 permission data keys directly from
a profile's ERC725Y storage:

- `AddressPermissions[]` — the array of all controller addresses
- `AddressPermissions:Permissions:<address>` — the permission bitmap
  for each controller

Each bitmap is decoded locally against the official LSP6 permission
schema and classified as high-risk or safe based on what it actually
allows that address to do.

## Tech Stack

- Vanilla JS + [ethers.js v6](https://docs.ethers.org/v6/)
- Direct RPC calls to LUKSO Mainnet (`rpc.mainnet.lukso.network`)
- No frameworks, no build step, no dependencies to install

## Usage

Just open `index.html` in any modern browser — locally or hosted
anywhere as a static file.

## Disclaimer

This tool is provided as-is, for informational purposes. It performs
read-only on-chain queries and never requests a signature or
transaction. Always verify critical permission changes directly
through your Universal Profile browser extension.

## License

MIT
