# Gamma-Native LNbits Extension — Proposal Site

A zero-build static site that presents the proposal for **`gammamarkets`**, a
GammaMarkets-native marketplace extension for [LNbits](https://lnbits.com).
The extension would let a merchant manage products once and publish them as
both NIP-15 marketplace events and NIP-99/GammaMarkets classified listings,
with Lightning checkout through LNbits invoices.

The site renders Markdown documents client-side — there is no framework, no
build step, and no dependencies to install. It is deployed as a static site
on Vercel.

## Documents

| Document | File | URL | Description |
|---|---|---|---|
| Architecture | `gamma-native-python-extension-proposal.md` | `/` (default) | Architecture and rationale for the `gammamarkets` Python extension |
| Technical Spec | `technical-specification.md` | `/?doc=spec` | The normative build contract (RFC 2119), targeting LNbits `v1.6.2-rc1` |
| Initial Research | `research.md` | `/?doc=research` | Original research transcript on NIP-99 / GammaMarkets support in LNbits |
| WASM Proposal | `proposal.md` | `/?doc=wasm` | Earlier proposal exploring an LNbits WASM-runtime extension (not linked in the nav) |

Documents are registered in the `documents` map in `index.html`. To add a new
one, drop the `.md` file in the repo root and add an entry there (plus a nav
link if it should appear in the header).

## Features

- Client-side Markdown rendering via [marked](https://marked.js.org/) (GFM)
- [Mermaid](https://mermaid.js.org/) diagram rendering, with a modal viewer
  for expanding and zooming diagrams
- Auto-generated table of contents from `h2`/`h3` headings
- Dark/light theme toggle, persisted in `localStorage`
- Print stylesheet and "Source" link to the raw Markdown file

## Running locally

`index.html` fetches the Markdown files over HTTP, so opening it directly
from the filesystem (`file://`) won't work. Serve the directory with any
static file server:

```sh
python3 -m http.server 8000
# or
npx serve .
```

Then open http://localhost:8000.

## Deployment

The repo is linked to a Vercel project (`gamma-proposal-site`) and deploys as
a plain static site — no build command or output directory configuration is
needed. Pushing to `main` (or running `vercel` from this directory) deploys
it.

## Repository structure

```
index.html                                # the entire site (markup, styles, renderer)
gamma-native-python-extension-proposal.md # architecture proposal (default document)
technical-specification.md                # normative build specification
research.md                               # initial research transcript
proposal.md                               # earlier WASM-runtime proposal
```
