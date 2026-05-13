# Advanced Historical Timeline Tool — Research Edition

A powerful, single-file historical timeline builder for creating, exploring, filtering, exporting, and preserving research timelines directly in the browser. It supports BCE/CE dates, approximate dates, date ranges, categories, tags, confidence scores, evidence/source links, pinned events, multiple views, local autosave, snapshots, undo/redo, and spreadsheet-friendly export formats.

The project is designed for historians, students, educators, writers, researchers, archivists, worldbuilders, and anyone who needs to organise chronological information without relying on a backend server.

---

## ✨ Features

### Timeline creation

* Add, edit, duplicate, pin, and delete historical events.
* Store event title, description, category, location, icon, colour, tags, source link, importance, and evidence confidence.
* Supports standard CE dates and BCE dates using negative years.
* Supports exact dates, month-level dates, year-level dates, approximate dates, and date ranges.
* Uses local browser storage so timelines persist between sessions.

### Research-focused metadata

Each event can include:

* **Category** — for example Politics, Science, Culture, War, Technology, Religion, Literature, Archaeology.
* **Tags** — comma-separated keywords for flexible filtering.
* **Location** — place associated with the event.
* **Source / citation link** — useful for evidence tracking.
* **Importance score** — 1 to 5.
* **Evidence confidence** — 0% to 100%.
* **Pinned state** — highlight events that matter most.

### Multiple views

* **Timeline View** — horizontal draggable timeline cards with zoom and date axis.
* **List View** — table layout for quick scanning and research review.
* **Story View** — narrative chronological format for writing or teaching.
* **Print View** — cleaner layout when printing or saving to PDF.

### Filtering and navigation

* Search across title, description, category, location, source, tags, and date labels.
* Filter by year range.
* Filter by category.
* Filter by tag.
* Filter by minimum confidence.
* Filter by minimum importance.
* Show pinned events only.
* Sort by date ascending, date descending, importance, or manual order.
* Zoom timeline card spacing and size.
* Drag empty timeline space to scroll.
* Drag cards to reorder in manual sort mode.

### Data management

* Autosaves to `localStorage`.
* Undo and redo support.
* Save and load local backup snapshots.
* Export as JSON for full backups.
* Export as CSV for spreadsheets.
* Export as Markdown for documentation, reports, or GitHub pages.
* Import JSON, CSV, or Markdown.
* Drag-and-drop text import support.

### UI and accessibility

* Dark and light themes.
* Compact and comfortable density modes.
* Keyboard shortcuts.
* Responsive design for desktop and smaller screens.
* Uses semantic HTML where practical.
* Avoids external libraries and backend dependencies.

---

## 🚀 Quick Start

This project is a standalone HTML file.

1. Download or clone the repository.
2. Open the HTML file in a modern browser.
3. Start adding timeline events.

No build step, package manager, database, or server is required.

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
cd YOUR_REPOSITORY_NAME
```

Then open the HTML file directly in your browser.

For a local development server, you can also run:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

---

## 🧭 How to Use

### Add an event

Click **Add Event** and fill in the event fields:

* Title
* Category
* Start year
* Optional month and day
* Optional end year
* Date precision
* Custom date label
* Icon or image URL
* Colour
* Location
* Tags
* Importance
* Evidence confidence
* Source link
* Description or research notes

Use negative years for BCE dates.

Examples:

```text
-44  = 44 BCE
1066 = 1066 CE
1969 = 1969 CE
```

### Choose date precision

The tool supports several precision modes:

| Precision   | Use case                                     |
| ----------- | -------------------------------------------- |
| Exact day   | A known day, month, and year                 |
| Month known | Month and year are known, but day is unknown |
| Year known  | Only the year is known                       |
| Approximate | Historical estimate, such as circa dates     |
| Date range  | Event spans multiple years                   |

### Search and filter

Use the sidebar to narrow the timeline by:

* Keyword search
* From year
* To year
* Category
* Tag
* Minimum confidence
* Minimum importance
* Pinned-only mode

### Change views

Use the view tabs to switch between:

* **Timeline** — visual chronological cards
* **List** — structured table
* **Story** — narrative timeline

### Export your work

Use the export buttons to save your timeline as:

* **JSON** — best for full backups and re-importing
* **CSV** — best for Excel, Google Sheets, LibreOffice, or data analysis
* **Markdown** — best for README files, reports, documentation, or publishing

### Import data

The tool can import:

* JSON event arrays
* JSON objects containing an `events` array
* CSV files with event columns
* Markdown timeline sections

---

## ⌨️ Keyboard Shortcuts

| Shortcut               | Action                |
| ---------------------- | --------------------- |
| `N`                    | Add new event         |
| `Delete`               | Delete selected event |
| `Ctrl + Z` / `Cmd + Z` | Undo                  |
| `Ctrl + Shift + Z`     | Redo                  |
| `Ctrl + Y` / `Cmd + Y` | Redo                  |
| `/`                    | Focus search          |
| `Esc`                  | Close modal           |

---

## 🧩 Event Data Format

A full event object can include:

```json
{
  "id": "e_example",
  "title": "Assassination of Julius Caesar",
  "year": -44,
  "month": 3,
  "day": 15,
  "endYear": null,
  "precision": "day",
  "dateLabel": "",
  "icon": "🗡️",
  "color": "#ef4444",
  "category": "Politics",
  "location": "Rome",
  "tags": ["rome", "republic", "caesar"],
  "importance": 5,
  "confidence": 88,
  "source": "https://example.com/source",
  "desc": "A major turning point in the late Roman Republic.",
  "order": 0,
  "pinned": false,
  "createdAt": "2026-01-01T00:00:00.000Z",
  "updatedAt": "2026-01-01T00:00:00.000Z"
}
```

### Important fields

| Field        | Description                                  |
| ------------ | -------------------------------------------- |
| `title`      | Event title                                  |
| `year`       | Start year. Negative values represent BCE    |
| `month`      | Optional month from 1 to 12                  |
| `day`        | Optional day from 1 to 31                    |
| `endYear`    | Optional end year for ranges                 |
| `precision`  | `day`, `month`, `year`, `approx`, or `range` |
| `dateLabel`  | Optional custom display label                |
| `category`   | Event grouping                               |
| `tags`       | Array of searchable tags                     |
| `importance` | 1 to 5 score                                 |
| `confidence` | 0 to 100 score                               |
| `source`     | Citation or evidence link                    |
| `desc`       | Notes or description                         |
| `pinned`     | Highlight important events                   |

---

## 📦 Import and Export Compatibility

### JSON

JSON is the recommended backup format because it preserves all fields.

Supported JSON structures:

```json
[
  {
    "title": "Example Event",
    "year": 1500,
    "category": "Culture"
  }
]
```

or:

```json
{
  "events": [
    {
      "title": "Example Event",
      "year": 1500,
      "category": "Culture"
    }
  ]
}
```

### CSV

CSV is useful for spreadsheet workflows. Supported columns include:

```text
id,title,year,month,day,endYear,precision,dateLabel,icon,color,category,location,tags,importance,confidence,source,desc,order,pinned
```

Tags can be separated with commas or semicolons depending on the imported file.

### Markdown

Markdown export is designed for reports and documentation. Markdown import can read timeline sections beginning with `##` headings.

---

## 🧪 Browser API

The app exposes a small testing and automation API on `window.TimelineTool`.

### Add an event

```js
TimelineTool.addEvent({
  title: "Magna Carta sealed",
  year: 1215,
  month: 6,
  day: 15,
  precision: "day",
  category: "Law",
  location: "Runnymede",
  tags: ["law", "england", "rights"],
  importance: 5,
  confidence: 90,
  icon: "📜",
  desc: "A major constitutional document in English legal history."
});
```

### Read all events

```js
const events = TimelineTool.getEvents();
console.log(events);
```

### Replace all events

```js
TimelineTool.setEvents([
  {
    title: "Example",
    year: 1800,
    category: "Demo"
  }
]);
```

### Reset sample data

```js
TimelineTool.reset();
```

### Export JSON string

```js
const json = TimelineTool.exportJSON();
```

---

## 🏗️ Project Structure

This tool is intentionally simple and portable.

```text
.
├── index.html      # Complete app: HTML, CSS, and JavaScript
└── README.md       # Project documentation
```

The app does not require a build system. All features are contained in the HTML file.

---

## 🔒 Privacy and Storage

The timeline is stored locally in the browser using `localStorage`.

This means:

* No account is required.
* No server is required.
* Data stays on the current browser/device unless exported.
* Clearing browser storage may delete saved timelines.

For important research, regularly use **Export JSON** or **Save Snapshot**.

---

## 🧠 Design Goals

The tool was built around these goals:

* Keep everything portable in one file.
* Make historical uncertainty visible through precision and confidence fields.
* Support BCE/CE and long-range timelines.
* Work for both quick classroom timelines and deeper research timelines.
* Preserve data in open formats.
* Avoid backend lock-in.
* Provide enough metadata for citation-aware history work.

---

## 🛠️ Development Notes

The app uses:

* Vanilla HTML
* Vanilla CSS
* Vanilla JavaScript
* Browser `localStorage`
* Browser `Blob` downloads
* Browser `FileReader` imports
* No external dependencies

Important internal concepts:

* Events are normalised through a `normalizeEvent()` helper.
* Undo/redo uses JSON snapshots of the event array.
* Date ordering uses a numeric date key built from year, month, and day.
* BCE dates are represented with negative years.
* View rendering is split into timeline, list, story, details, stats, and snapshots.

---

## 🧭 Roadmap Ideas

Possible future upgrades:

* Event relationship links, such as cause, consequence, influence, or contradiction.
* Map view for geolocated history.
* Image gallery per event.
* Citation quality scoring.
* Timeline comparison mode.
* Multiple timelines in one file.
* Timeline merge and conflict resolution.
* Tag graph visualisation.
* AI-assisted summarisation of exported timelines.
* Version history browser.
* OPML, ICS, YAML, and RDF export.
* Offline PWA support.
* Custom timeline themes.
* Collaborative sync adapter.

---

## 🐛 Troubleshooting

### My events disappeared

Check whether your browser storage was cleared. If you exported JSON or saved a snapshot, import or load it again.

### Imported dates look wrong

For BCE dates, use negative years:

```text
-44 = 44 BCE
```

For precise dates, include separate `year`, `month`, and `day` fields when using JSON or CSV.

### CSV import did not preserve all fields

Use JSON for full-fidelity backups. CSV is designed for spreadsheet compatibility and may lose complex data if columns are missing.

### Drag reorder is not working as expected

Reordering works best in **Manual order** sort mode. If you drag cards while another sort is active, the app switches to manual order.

---

## 🤝 Contributing

Contributions are welcome. Useful contributions include:

* Bug fixes
* UI improvements
* Accessibility improvements
* Import/export improvements
* Historical research workflow features
* Test datasets
* Documentation updates

Suggested workflow:

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Test in modern browsers.
5. Open a pull request.

---

## 📄 License

Add your preferred license here.

Example:

```text
MIT License
```

---

## 🙌 Acknowledgements

Built as a browser-native research timeline tool for exploring historical events, uncertainty, evidence, and chronology in a simple, portable format.
