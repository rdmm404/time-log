# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Time Tracker Desktop App** built with Electron + TypeScript + React + SQLite. The goal is to create a minimal, reliable, local-only desktop time tracker with ultra-fast start/stop flow, accurate daily totals, and simple exports.

## Project Management

You'll find a detailed implementation plan at ./IMPLEMENTATION_PLAN.md, you will be tasked to implement tasks from this implementation plan.
Once you complete a task, you must get back to the user for final review on the task completed, and then once it's approved, you MUST:

- mark it as done in the implementation plan
- create a commit with a descriptive message
- push directly to the main branch
- update CLAUDE.md with any new relevant details.

## Relevant files

- IMPLEMENTATION_PLAN.md: tasks to follow for the implementation of this project
- PROJECT.md: Full feature spec of the project

## Architecture Overview

### Tech Stack

- **Framework**: Electron with TypeScript
- **Package Manager**: pnpm for dependency management
- **Frontend**: React with Zustand/Redux for state management
- **Database**: SQLite with better-sqlite3 (WAL mode)
- **Time Handling**: Luxon for timezone/DST support
- **Exports**: CSV (csv-stringify) and Excel (exceljs)
- **Validation**: Zod for settings and input validation

### Process Architecture

- **Main Process**: Timer service, DB access, tray, global shortcuts, power monitoring, file exports
- **Renderer Process**: React UI with Dashboard, Logs, Export, Settings views
- **Preload**: Typed IPC API with contextBridge (no remote module)

### Key Services

- `TimerService`: Core start/stop functionality with state machine
- `DBService`: SQLite operations with migrations
- `TrayService`: System tray with today's total display
- `ShortcutService`: Global keyboard shortcuts
- `ReminderService`: Login/periodic/app-open notifications
- `ExportService`: CSV/Excel generation
- `SettingsService`: Configuration with OS integration (autostart)
