
---

# Local Knowledge Graph Editor (PySide6 / Qt)

An offline-first graph editor for organizing complex information as linked notes and relationships.
Designed for research, learning, project planning, and worldbuilding (e.g. D&D campaigns).

Built with **PySide6 / Qt**.

The application lets you visually map topics, entities, and their connections on an infinite canvas while keeping all data local and exportable as structured JSON.

---

## Features

### Graph editor

* Create nodes representing topics, people, locations, items, notes, etc.
* Drag nodes freely on an infinite canvas
* Connect nodes with labeled relationships

  * Hold **Shift** and click **source → target** to connect
  * Optional relationship label prompt
* Edit relationship labels via double-click
* Delete selected nodes/edges with **Delete** / **Backspace**
* Selectable edges with automatic arrow rendering

### Inspector panel (node details)

Each node stores structured metadata:

* Name
* Category (group)
* Status: `unknown | confirmed | suspected | false`
* Confidence (0–100)
* Tags (comma-separated input)
* Notes
* Attachments (links or local files)

### Attachments

* Drag & drop URLs or files directly onto nodes
* Files stored as `file://...` references
* Inspector “Add” button for manual entry
* Open/preview attachments:

  * Double-click a node opens the first attachment
  * Inspector “Open” opens selected attachment
  * Images preview inside the application (`png/jpg/webp/gif/...`)

### Search

Toolbar search filters nodes by:

* Name
* Tags
* Attachment label/URL text
* Notes

### Theme & UI

* Dark mode by default
* Toggle Dark Mode (**Ctrl+D**)
* Qt “Fusion” style
* Modern, readable UI font handling

---

## Installation

### Requirements

* Python 3.10+
* PySide6

### Dependencies

```bash
pip install PySide6 requests tldextract validators dnspython python-whois
```

---

## Running

Save the script as:

```bash
python mindmap.py
```

---

## Controls & Shortcuts

### Navigation

* Mouse wheel: zoom
* Click-drag: move canvas
* **F**: Fit graph to content
* **+ / =**: zoom in
* **- / _**: zoom out

### Create relationships

* Hold **Shift**
* Click source node → click target node
* Enter optional label

### Edit / delete

* Double-click edge label to edit
* Delete/Backspace removes selected nodes and edges

### Attachments

* Drag/drop URLs onto nodes
* Drag/drop files onto nodes
* Double-click node to open first attachment

---

## Data Model (JSON)

Nodes and edges can be exported/imported as JSON.

### Node fields

* `id` (uuid string)
* `label`
* `group`
* `tags` (list of strings)
* `status`
* `confidence` (0–100)
* `attachments` (list of `{label, url}`)
* `notes`
* `x`, `y` (canvas position)

### Edge fields

* `source` (node id)
* `target` (node id)
* `label`
* `style` (`solid`, supports dashed/dotted rendering)

### Example structure

```json
{
  "nodes": [
    {
      "id": "uuid",
      "label": "Example",
      "group": "note",
      "tags": ["tag1"],
      "status": "unknown",
      "confidence": 50,
      "attachments": [{"label": "link", "url": "https://example.com"}],
      "notes": "",
      "x": 0.0,
      "y": 0.0
    }
  ],
  "edges": [
    {"source": "uuid1", "target": "uuid2", "label": "related to", "style": "solid"}
  ]
}
```

---

## Import / Export

### Export JSON

* Toolbar → Export JSON
* Saves node positions and relationships

### Import JSON

* Toolbar → Import JSON
* Clears scene and loads graph from file

---

## Privacy & Design Principles

* Offline-first by design
* No telemetry
* No background networking
* All data remains local unless explicitly exported by the user

---

## Use Cases

This tool is suitable for:

* Research and information mapping
* Learning and topic exploration
* Project and idea organization
* Worldbuilding and campaign planning
* Any scenario where relationships between notes matter
