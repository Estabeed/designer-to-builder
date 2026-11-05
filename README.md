# Designer to Builder

> **My copy.** I use this copy of Figma's Designer to Builder project to learn how a Figma component becomes working code. I set it up on 3rd November 2026, merged my first three pull requests and deployed it on Vercel. The original text follows.

This is the working codebase for the Figma **Designer to Builder** livestream series: a beginner-friendly walkthrough of turning a Figma component into reviewable code with Figma MCP and a coding agent.

The project intentionally starts small. It uses native HTML and CSS, with no framework, JavaScript, dependencies, or build step, so every part of the implementation remains visible and understandable to designers who are new to code. The one external resource is the Google Sans Flex font, which the previews load from Google Fonts so that the type matches the Figma design.

## Design source

The project uses the Accordion component from the [Designer to Builder Figma Community file](https://www.figma.com/community/file/1655994171720567013/figma-livestream-designer-builder).

The Figma file contains the component structure, open and closed states, content, variables, and light and dark examples used as the source of truth for the implementation.

## Repository structure

```text
.
├── .gitignore
├── AGENTS.md
├── PROMPTS.md
├── README.md
├── figma.config.json
├── index.html
└── src/
    ├── components/
    │   └── accordion/
    │       ├── Accordion.figma.ts
    │       ├── accordion.css
    │       └── accordion.html
    └── tokens/
        └── tokens.css
```

| Path | Purpose |
| --- | --- |
| `index.html` | The home page. It previews the design tokens in light and dark and links to the accordion preview. |
| `src/tokens/tokens.css` | Design variables from the Figma file as CSS custom properties: raw values first, then semantic and component tokens, with light as the default theme and a dark theme. |
| `src/components/accordion/accordion.html` | The Accordion preview in light and dark, with open and closed states, built on `details` and `summary`. |
| `src/components/accordion/accordion.css` | Styles for the Accordion, reading their values from the tokens. |
| `src/components/accordion/Accordion.figma.ts` | The Code Connect template that links the Figma Accordion component to this HTML. |
| `figma.config.json` | Tells the Code Connect tool where to find the `.figma.ts` files. |
| `AGENTS.md` | Working instructions for coding agents using this repository. |
| `PROMPTS.md` | The prompts and terminal commands used across the three sessions. |
| `.gitignore` | Keeps local environment files, such as `.env`, out of Git. |

`src/components` holds one folder per component and `src/tokens` holds the variables they share. The Accordion is the only component so far.

## View locally

Clone the repository and open `index.html` in a browser. No installation or build command is required.

## How I will use this

I am a product designer moving into building. I will use this repository to practise three things.

1. Trace every visual decision back to Figma. I will open `src/tokens/tokens.css`, pick a variable such as `--component-accordion-background-active`, and find the matching variable in the Figma file. The goal is to see a token as a named design decision, not a number someone typed.
2. Learn what the browser already does for me. The accordion uses `details` and `summary`, so opening, closing and keyboard use work with no JavaScript. The goal is to know what native HTML gives me before I ask anyone to write more code.
3. Review the coding agent's work against the source of truth. I will write a plan prompt, read the result, and compare it with the Figma node using the prompts in `PROMPTS.md`. The goal is to spot what matches, what is missing and what was invented, then ask for the smallest fix.
