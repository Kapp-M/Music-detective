#  Music Detective

**Understanding how a music player works through code analysis, browser testing, and reverse engineering.**

Music Detective project focused on investigating an existing music player, understanding its behavior, and tracing that behavior back to the source code.

Rather than immediately rebuilding the application, the goal is to first understand how its components, state, event handlers, and audio controls work together.

## Project Goals

- Understand the structure of an existing React application.
- Observe and document user-facing behavior.
- Trace UI interactions back to their source code.
- Investigate how audio playback, track navigation, search, filtering, shuffle, and looping work.
- Use static analysis and browser inspection to support the investigation.
- Document findings, limitations, and edge cases throughout the process.

## 🛠️ Tech Stack and Tools

| Technology / Tool | Purpose |
|---|---|
| React | User interface |
| Vite | Development server and build tooling |
| JavaScript | Application logic |
| HTML / CSS | Structure and styling |
| Git & GitHub | Version control and documentation |
| REA Agents | Static analysis and evidence collection |
| Microsoft Edge | Browser-based inspection |
| Node.js & npm | Runtime and package management |

## 🔍 Initial Investigation

The investigation began with the open-source [Audio Player](https://github.com/madzadev/audio-player) project.

A separate experimental copy is maintained locally under `audio-player-lab` so the investigation can be performed without modifying the original cloned target.

Initial package scripts and build output indicate that the application uses React and Vite.

### Current Observations

The following behaviors have been manually tested in the browser:

- [x] Application loads successfully.
- [x] Play starts audio playback.
- [x] Next changes to another track.
- [x] Previous changes to another track.
- [x] Shuffle works.
- [x] Loop works.
- [x] Search filters tracks by name.
- [x] Clearing search restores the track list.
- [x] Genre filters work.

These checks establish observed behavior, but they do not yet explain every implementation detail behind it.

## 🧪 Initial Build and Code Quality Checks

| Check | Result |
|---|---|
| Dependency installation (`npm ci`) | Successful |
| Production build (`npm run build`) | Successful |
| Lint (`npm run lint`) | Failed: 74 errors and 7 warnings |
| npm security audit | Reported 15 vulnerabilities |

The lint findings included unused imports, missing prop-type declarations, hook dependency issues, and other code-quality warnings.

The audit reported 1 low, 3 moderate, and 11 high vulnerabilities. These results have been recorded for investigation; automatic dependency fixes have not been applied.

## 🧠 Reverse-Engineering Plan

The next phase focuses on connecting observable behavior to implementation.

1. **Track navigation:** Trace Next and Previous through event handlers, state updates, and audio-source changes.
2. **Playback controls:** Investigate Play/Pause, Shuffle, and Loop, including relevant state and effects.
3. **Search and filtering:** Follow search and genre filters through the application logic.
4. **Edge cases:** Test empty search results, filtering out the currently selected track, and track-list boundaries.
5. **Evidence and documentation:** Record the user action, visible result, relevant source code, and any remaining uncertainty.

## 📁 Repository Structure

```text
Music-detective/
├── audio-player-lab/       # Experimental application snapshot
├── notes/
│   └── progress-log.md     # Investigation notes and findings
├── .gitignore
└── README.md
```

The original target clone is kept separately from the main repository's tracked files. Dependencies and generated build output are excluded from version control.

## 📌 Current Status

**Phase 1 — Initial Setup and Behavioral Observation**

The project environment is set up, the experimental application builds successfully, and initial player behavior has been documented.

**Source-to-behavior tracing is still in progress.** The project has not yet completed a full reconstruction of the application's internal logic.

## 📚 Reference

- Original project: [madzadev/audio-player](https://github.com/madzadev/audio-player)
- Investigation notes: [`notes/progress-log.md`](notes/progress-log.md)

This repository is intended as a learning and analysis project. The original application remains the reference implementation; the current work documents the investigation rather than claiming an independent implementation.

## ⚖️ Attribution

The application being investigated is available under the MIT License in its original repository. Refer to the upstream project for its license and attribution requirements when redistributing its code.
