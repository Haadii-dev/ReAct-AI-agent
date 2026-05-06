# ReAct AI Agent

An AI agent that follows the ReAct (Reasoning + Acting) pattern — it thinks through a problem step by step, decides which tool to use, calls it, observes the result, and repeats until it has an answer.

Built with JavaScript and the OpenAI API. Uses Vite for local development.

## How it works

The agent receives a user query and enters a loop:

1. **Thought** — the LLM reasons about what it needs to do next
2. **Action** — it picks a tool and calls it with specific parameters
3. **Observation** — the tool returns a result
4. **Repeat** — the agent decides if it has enough info or needs another tool call

This continues until the agent has a final answer, which it returns to the user.

## Tools

The agent has two tools it can call:

- **getCurrentWeather** — takes a city name, hits the OpenWeatherMap API, returns current weather data (temperature, conditions, etc.)
- **getLocation** — uses IP geolocation to detect the user's current location automatically

So if you ask "what's the weather like right now?", the agent will first call `getLocation` to figure out where you are, then call `getCurrentWeather` with that city to get the forecast. Two tool calls, chained together through reasoning.

## Files

```
├── index.js         # main agent loop (ReAct cycle)
├── tools.js         # tool definitions (weather + geolocation)
├── dom.js           # UI interaction logic
├── index.html       # frontend interface
├── index.css        # styling
├── vite.config.js   # dev server config
└── package.json
```

## Setup

```bash
npm install
npm run dev
```

## Why ReAct?

Standard LLM calls are one-shot — you ask, it answers. ReAct lets the model break complex questions into steps and use external tools to gather real information before answering. This is the same pattern used by LangChain agents and similar frameworks, implemented here from scratch to understand how it works under the hood.

## Tech

JavaScript, OpenAI API (function calling), Vite
