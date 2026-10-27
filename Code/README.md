# Code

Product code goes here. Nothing built yet beyond the hackathon PoC.

The PoC lives in its own repo: [gawtamcr/cursor-hack](https://github.com/gawtamcr/cursor-hack). Its parts, as described in the hackathon PDF:

- a ROS 2 control stack for a self-driving car's steering subsystem, with a fault injector (bias, reversed, stuck, noise, lag)
- a unit-tested symptom classifier (commanded intent vs measured response over a rolling window)
- an MCP server exposing the live system to an LLM agent (read health, read stats, inject fault, restart unit)
- requirements and known issues held as agent memory
- a web panel with live telemetry, the cited diagnosis and a one-click fix
