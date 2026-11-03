# Designer to Builder

This is the working codebase for the Figma **Designer to Builder** livestream series: a beginner-friendly walkthrough of turning a Figma component into reviewable code with Figma MCP and a coding agent.

The project intentionally starts small. It uses native HTML and CSS, with no framework, JavaScript, dependencies, or build step, so every part of the implementation remains visible and understandable to designers who are new to code.

## Design source

The project uses the Accordion component from the [Designer to Builder Figma Community file](https://www.figma.com/community/file/1655994171720567013/figma-livestream-designer-builder).

The Figma file contains the component structure, open and closed states, content, variables, and light and dark examples used as the source of truth for the implementation.

## Repository structure

```text
.
├── AGENTS.md
├── README.md
├── index.html
└── src/
    ├── components/
    └── tokens/
```

| Path | Purpose |
| --- | --- |
| `index.html` | The browser preview and home for the component markup. |
| `src/components` | Styles for components created from the Figma design. |
| `src/tokens` | Design variables represented as CSS custom properties. |
| `AGENTS.md` | Working instructions for coding agents using this repository. |

The component and token directories are empty in the starting scaffold. The blank `index.html` page provides the browser entry point without introducing any design or implementation decisions in advance.

## View locally

Clone the repository and open `index.html` in a browser. No installation or build command is required.

## How I will use this

I am a product designer moving into building. I will use this repository to practise three things.

1. Trace every visual decision back to Figma. I will open `src/tokens/tokens.css`, pick a variable such as `--component-accordion-background-active`, and find the matching variable in the Figma file. The goal is to see a token as a named design decision, not a number someone typed.
2. Learn what the browser already does for me. The accordion uses `details` and `summary`, so opening, closing and keyboard use work with no JavaScript. The goal is to know what native HTML gives me before I ask anyone to write more code.
3. Review the coding agent's work against the source of truth. I will write a plan prompt, read the result, and compare it with the Figma node using the prompts in `PROMPTS.md`. The goal is to spot what matches, what is missing and what was invented, then ask for the smallest fix.
