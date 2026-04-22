# Claude Instructions — Todo App

This is a single-file personal todo app (`index.html`). All data lives in the `data` array inside the `<script>` block. There is no backend, no build step.

## How to add items

Find the `data` array in `index.html`. Each entry is a category object:

```js
{
  category: "Category Name",
  items: [
    {
      text: "Task description",        // required — also used as localStorage key, never change once added
      priority: "high|medium|low",     // required
      note: "Optional subtitle",       // optional
      link: "https://...",             // optional
      linkLabel: "Link text",          // required if link is set
      sublinks: [                      // optional list of reference links
        { label: "Link name", url: "https://..." }
      ]
    }
  ]
}
```

## Rules

- **Never rename or change `text` on existing items** — the text is hashed into a localStorage key. Changing it loses the user's checked/in-progress state.
- **Append new items to the end of a category's `items` array** — do not insert in the middle.
- **To add a new category**, append a new object to the `data` array.
- **Priority colors**: high = muted red, medium = amber, low = slate blue.
- The app is fully self-contained — no npm, no build, just open `index.html` in a browser.

## Chat widget (built-in AI)

The app has an embedded chat panel (💬 button, bottom-right) that calls the Anthropic API so users can add tasks by typing naturally. It requires an Anthropic API key entered once in the browser — stored in localStorage, never committed to the repo.

## GitHub Pages

To host publicly: repo Settings → Pages → Deploy from branch `main`, folder `/` (root). The app will be live at `https://username.github.io/repo-name`.
