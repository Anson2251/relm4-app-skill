# Relm4 App Skill

An AI agent skill for building **GTK4 GUI applications with [Relm4](https://relm4.org/)** — an idiomatic Rust GUI library inspired by the Elm Architecture.

This skill is based on the [Relm4 Book](https://relm4.org/book/stable/) and covers all its core concepts in a format optimized for AI agents.

## Overview

This skill gives AI coding agents deep knowledge of Relm4 0.9.x, including its component model, the `view!` macro, factory patterns, async/threading support, and GTK4/libadwaita integration. When you ask an agent to build a GTK4 app in Rust, it consults this skill to produce idiomatic, working code.

## Installation

```bash
npx skills add Anson2251/relm4-app-skill --agent universal
```

This installs the skill for any AI agent that supports the [skills protocol](https://github.com/anthropics/skills) (Claude Code, Cline, Roo Code, and others).

## What the Skill Covers

| Concept | Reference File |
|---------|---------------|
| `view!` macro — `#[watch]`, signals, containers, conditionals | `references/view-macro.md` |
| Child components — `Controller<T>`, parent↔child communication | `references/child-components.md` |
| Dynamic lists — `FactoryVecDeque`, `#[relm4::factory]` | `references/factories.md` |
| Background threads — `Worker`, `Command`, `AsyncComponent` | `references/threads-and-async.md` |
| Reusable widget patterns — `WidgetTemplate`, `#[template_child]` | `references/widget-templates.md` |
| Efficient UI updates — `#[tracker::track]` | `references/tracker-and-efficiency.md` |
| GTK4 widgets (Entry, ComboBox, SpinButton, etc.), libadwaita, CLI, CSS | `references/gtk-integration.md` |
| Full working examples — Todo App, Alert dialog, manual components | `references/complete-examples.md` |

## How It Works

The skill is activated automatically when you describe a Relm4, GTK4 GUI, or Rust UI task in natural language — for example:

> "Build a Relm4 app with a todo list, text input, and add button"

The agent loads the skill and generates idiomatic Relm4 code with the right patterns (components, `view!` macro, factory lists, etc.).

## Project Structure

```
relm4-app-skill/
├── README.md
├── LICENSE
├── .gitignore
└── skills/
    └── relm4-app/
        ├── SKILL.md                      # Main skill instructions & Quick Start
        └── references/
            ├── child-components.md       # Controller<T> & parent↔child patterns
            ├── complete-examples.md      # Full runnable app examples
            ├── factories.md              # FactoryVecDeque & factory patterns
            ├── gtk-integration.md        # GTK4 widgets, libadwaita, CLI, CSS
            ├── threads-and-async.md      # Workers, Commands, AsyncComponent
            ├── tracker-and-efficiency.md # #[tracker::track] for selective updates
            ├── view-macro.md             # view! syntax reference
            └── widget-templates.md       # WidgetTemplate for reusable UI
```

## Key Traits at a Glance

| Trait | Best For | Macro |
|-------|----------|-------|
| `SimpleComponent` | **90% of cases** — standard UI with buttons, labels, inputs | `#[relm4::component]` |
| `Component` | Background tasks without freezing the UI | manual `impl` |
| `AsyncComponent` | `await` inside `init()` or `update()` | `#[relm4::component(async)]` |
| `Worker` | CPU-heavy work on a separate thread (no widgets) | `impl Worker for ...` |
| `FactoryComponent` | Dynamic lists of similar widgets (todo items, tabs) | `#[relm4::factory]` |
| `WidgetTemplate` | Reuse the same widget subtree in multiple places | `#[relm4::widget_template]` |

## Requirements

- **Rust 2021 edition** or later
- **Relm4 0.9.x**
- **GTK4** development packages installed on your system

### Installing GTK4

```bash
# Ubuntu/Debian
sudo apt install libgtk-4-dev libadwaita-1-dev

# Fedora
sudo dnf install gtk4-devel libadwaita-devel

# macOS (Homebrew)
brew install gtk4 libadwaita

# Windows — use MSYS2 (see gtk-rs installation guide)
```
