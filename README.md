# Ops Board

A zero-dependency, single-file Kanban board for AI-assisted workflows.

Built for people who use AI agents (Claude, GPT, etc.) alongside human team members and need a lightweight task board without SaaS overhead.

## Features

- **Single HTML file** — no build step, no dependencies, no framework
- **Drag & drop** — move cards between columns
- **Fully configurable** — custom columns, assignees, categories, colors
- **Checklists** — subtasks with progress tracking on cards
- **Due dates** — with overdue highlighting
- **Search & filters** — by assignee, category, or text
- **Dark/Light theme** — toggle with one click
- **Import/Export** — JSON backup and restore
- **LocalStorage** — data persists in browser, no server needed
- **Responsive** — works on mobile

## Quick Start

```bash
# Option 1: Just open the file
open index.html

# Option 2: Local server
python3 -m http.server 3333
# → http://localhost:3333

# Option 3: Deploy anywhere
# Copy index.html to any static hosting (Nginx, Vercel, GitHub Pages, etc.)
```

## Usage

| Action | How |
|--------|-----|
| Create task | Click **+ Task** or **+ Add** in any column |
| Edit task | **Double-click** any card |
| Move task | **Drag** card to another column |
| Search | Type in the search bar |
| Filter | Click filter tags below stats |
| Configure | Click **Config** to customize columns, assignees, categories |
| Export | Click **Export** to download JSON backup |
| Import | Click **Import** to restore from JSON |
| Theme | Click **Theme** to toggle dark/light |

## Configuration

Click **Config** to customize:

- **Board name** — displayed in header
- **Columns** — add/remove/rename/recolor workflow stages
- **Assignees** — team members, AI agents, or roles
- **Categories** — tag types for filtering

All settings are saved to localStorage.

## AI Workflow Integration

This board was designed for human + AI agent collaboration:

1. **Human** creates tasks and assigns to AI
2. **AI agent** reads tasks via export/API and executes them
3. **AI agent** updates task status when done
4. **Human** reviews in the Review column

### Example with Claude Code

```bash
# Export board state
# AI reads the JSON and picks up assigned tasks
# AI executes and reports back
```

## Self-Hosting

### Nginx

```nginx
server {
    listen 80;
    server_name board.example.com;
    root /var/www/ops-board;
    index index.html;
}
```

### GitHub Pages

Just push `index.html` to a repo and enable Pages.

## Data Format

```json
{
  "config": {
    "name": "My Board",
    "columns": [{"id": "backlog", "name": "Backlog", "color": "#888"}],
    "assignees": [{"id": "me", "name": "Me", "color": "#00cec9"}],
    "categories": ["dev", "design"]
  },
  "tasks": [
    {
      "id": "t1",
      "title": "Task name",
      "desc": "Details",
      "assignee": "me",
      "priority": "high",
      "category": "dev",
      "column": "backlog",
      "due": "2026-04-01",
      "checklist": [{"text": "Subtask", "done": false}],
      "created": "2026-03-31"
    }
  ]
}
```

## License

MIT

## Author

Made by [Jhon Carvalho](https://github.com/jhojuneo) with Claude Code.
