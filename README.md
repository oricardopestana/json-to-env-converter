# JSON ↔ ENV Converter

A browser-based tool to convert between JSON and environment variable formats. All processing happens client-side — no API calls, no data leaves your browser.

## Live Demo

**[json-to-env-converter.vercel.app](https://json-to-env-converter.vercel.app)**

## Features

- Convert JSON to `.env` format and vice versa
- Flat and nested JSON support
- Real-time validation feedback
- Copy output with one click
- Fully client-side — no server involved

## Commands

| Command           | Action                                       |
| :---------------- | :------------------------------------------- |
| `yarn`            | Install dependencies                         |
| `yarn dev`        | Start local dev server at `localhost:4321`   |
| `yarn build`      | Build production site to `./dist/`           |
| `yarn preview`    | Preview the production build locally         |

## Tech Stack

- [Astro 6 beta](https://astro.build)
- [Tailwind CSS v4](https://tailwindcss.com)
- TypeScript
