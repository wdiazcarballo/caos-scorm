# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is a SCORM-compliant educational web application that teaches operating system concepts through an interactive restaurant kitchen simulation. The entire application is contained in a single `index.html` file (38KB) using pure HTML5, CSS3, and vanilla JavaScript.

## Development Commands
Since this is a pure HTML/CSS/JS project with no build tools:
- **Run locally**: Open `index.html` directly in a browser or use VS Code Live Server (configured for port 5501)
- **No build/test/lint commands**: This project has no npm scripts, build process, or automated testing

## Architecture and Key Concepts

### Single-Page Application Structure
The app uses section-based navigation with 5 main sections, all contained within `index.html`:
1. Introduction (`#section1`)
2. OS Evolution (`#section2`) 
3. Kitchen Simulation (`#section3`) - Interactive simulation with era selection
4. Memory Management (`#section4`)
5. Summary (`#section5`)

### SCORM Integration
- Uses `pipwerks-scorm-api-wrapper` library loaded via CDN
- Key SCORM functions: `initSCORM()`, `setSCORMScore()`, `setSCORMComplete()`
- Tracks progress, quiz scores, and completion status
- Falls back gracefully if SCORM API is unavailable

### State Management
Global variables track application state:
- `currentSection` - Current visible section (1-5)
- `selectedEra` - Selected OS era for simulation (0-3)
- `isSimulationRunning` - Simulation active state
- `simulationTime` - Elapsed simulation seconds
- `completedOrders` - Orders completed in simulation
- `score` - Overall quiz score
- `quizAnswers` - User quiz responses

### Interactive Components
- **Era Selection**: 4 different efficiency levels affect simulation speed
- **Kitchen Simulation**: Animated chefs demonstrate OS concepts (multitasking, scheduling)
- **Memory Visualization**: RAM vs disk storage representation
- **Quiz System**: 4 embedded quizzes with immediate feedback

### Code Patterns
- Event-driven architecture with inline event handlers
- CSS animations for visual effects (chef movements, transitions)
- No external dependencies except SCORM wrapper
- All code in single file - styles in `<style>`, scripts in `<script>`

## Important Considerations
- **Thai Language Content**: All user-facing text is in Thai
- **Educational Context**: Designed for LMS deployment, test locally with SCORM player
- **Restaurant Metaphor**: OS concepts mapped to kitchen operations (processes = orders, CPU = chef, memory = storage)
- **No Modularization**: Everything in one file - be careful with global scope conflicts