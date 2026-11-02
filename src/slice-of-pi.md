---
title: Slice of pi
---

# Harness

. . .

::::: columns

:::: {.column width=10%}
::::
:::: {.column width=30%}

## What it does? \centering

. . .

- LLM communication
- Skill access
- Tool execution
- Context management
- Session management
- Chat display

. . .

- Agentic loop

. . .

## Examples \centering

. . .

- Claude code
- Codex
- Opencode
- **pi**

::::
:::: {.column width=10%}
::::
:::: {.column width=50%}

```{=latex}
\onslide<.(-1)->
```

## Agentic loop \centering

```{=latex}
\vspace{1em}
\centering
\begin{tikzpicture}[->,every edge/.append style={bend right=-45}]
  \node (read)  at ( 90:2)   {Prompt / Tool};
  \node (eval)  at ( 330:2)  {Request};
  \node (print) at ( 210:2)  {Response};
  \graph [use existing nodes] {
    read -> [bend right] eval -> ["LLM"] print -> read
  };
\end{tikzpicture}
```

::::

:::::

# Context

:::::: columns
:::: column

## What is context? \centering

. . .

- Initial prompt
  - System prompt
  - Tool descriptions
  - Skill descriptions
  - MCP descriptions
- Messages
  - User prompts
  - LLM responses
  - Tool call results
  - LLM reasoning

. . .

## Compaction \centering

- Keep initial prompt
- Keep last 20k messages without reasoning
- Ask LLM to summarize everything else

::::
:::: column

. . .

\centering

|                       | pi           | opencode       |
|-----------------------|--------------|----------------|
| System prompt         | 2 742 ch     | 8 603 ch       |
| Tools                 | 4 · 2 956 ch | 12 · 14 033 ch |
| Initial prompt        | 5 710 ch     | 22 640 ch      |
| Tokens                | 1 395        | 5 077          |
| Price                 | ₽0.027       | ₽0.090         |

. . .

- Claude code/Codex prompts are even bigger
- Increased initial prompt size is better for model providers
- Initial prompt is what survives compaction
- Bigger context on average costs more

::::
::::::

# pi

:::::: columns
:::: column

## pi agent harness \centering

`{\centering\footnotesize`{=latex}
There are many agent harnesses but this one is \color{CtpMauve}{yours}
`}`{=latex}

\vspace{1em}

. . .

- Minimal
  - Small system prompt
  - 4 tools by default
  - No MCP/sub-agents
- Extensible
  - Vibe-code extensions/skills/themes
  - Package marketplace
- Transparent
  - .jsonl session files
  - Good bundled docs
  - Extensions can access all internal info

::::
:::: column

```{=latex}
\begin{minipage}[c][.8\textheight][c]{\linewidth}
\centering
\qrcode[height=4cm]{https://pi.dev}
\vspace{1em}
```
<https://pi.dev>
```{=latex}
\end{minipage}
```

::::
::::::

# My pi config {.fragile}

`\lstset{style=default,basicstyle={\ttfamily\color{CtpPeach}}}`{=latex}

:::::: columns
:::: column

```{=latex}
\begin{onlyenv}<2>
```

::::: block

## My extensions \centering

- `routerai-provider.ts`
  - Model selection UI
  - Shows real cost
  - Model provider selection UI
  - Sorting and filtering
  - Limits context size
- `turn-timer.ts`
  - Tracks current turn stats
  - Time, cost, inference speed
  - Reports summary when model turn ends
- `pin.ts`
  - Pin arbitrary text or skills to system prompt
  - Survives compaction
- `no-root-scan.ts`
  - Blocks searches in root of file system

:::::

```{=latex}
\end{onlyenv}
```

```{=latex}
\begin{onlyenv}<3->
```

::::: block

## My skills \centering

- `duckduckgo-search` - Web searching
  - search.sh + fetch.sh
  - curl + w3m internally
  - Uses GitHub CLI for GitHub access
- `pair` - Pair programming system prompt
  - Plan then implement
  - Do only what is asked
  - Pause on surprises
  - Don't deep dive
  - Autonomy when explicitly asked
- `tutor` - Tutor system prompt
  - Does not give you the answer right away
  - Guides with questions
  - Reduces output size
  - Combines with `pair`
  - [Original source](https://www.patreon.com/SciencePetr/posts/guide-to-turn-ai-153388398)

:::::

```{=latex}
\end{onlyenv}
```

::::
:::: column

```{=latex}
\begin{minipage}[c][.9\textheight][c]{\linewidth}
\centering
\qrcode[height=4cm]{https://github.com/liontiger23/configs-pi}
\vspace{1em}
```
<https://github.com/liontiger23/configs-pi>
```{=latex}
\end{minipage}
```

::::
::::::


# {.plain}

\centering
```{=latex}
{\fontsize{48pt}{7.2}\selectfont Q\&A }
```

