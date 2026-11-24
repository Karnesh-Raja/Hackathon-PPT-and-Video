# Mystic Summit 2026 — Team Showcase

A static GitHub Pages website for the Mystic Summit Hackathon. It displays the 36-team directory, departments, leaders, complete member lists, and links to PPT presentations and project videos.

## Files

- `index.html` — website, styling, search, filters, and submission matching
- `teams.json` — team names, departments, leaders, members, and problem-statement identifiers

Keep both files in the **root** of the GitHub repository.

## Publish on GitHub Pages

1. Download and extract this ZIP file.
2. Create a new GitHub repository.
3. Upload **index.html**, **teams.json**, and **README.md** directly to the repository root.
4. Open **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/(root)`, then save.
6. Open the GitHub Pages URL after deployment completes.

## How PPT and video links are matched

The website reads the published Google Sheets CSV URL already configured in `index.html`. It refreshes the links every 60 seconds and also has a **Refresh links** button.

The submission sheet can use **Tam Name** or **Team Name** for the team-label column. The other required columns are a PPT/presentation link column and a video link column.

### Submissions are matched by the leader name

The site reads the leader name to the right of the dash in the submission label and matches it against the team leader in `teams.json`. This is especially important for the five registered teams sharing the name **Tech Titans**; they are displayed as separate entries and do not require a Problem ID column.

The five distinct entries are displayed as:

- Tech Titans — Sri Brindha G
- Tech Titans — Keerthishree D
- Tech Titans — Madhumithaa G
- Tech Titans — Poornashri S
- Tech Titans — Monesh V

For example, `Tech Titans(2) – KEERTHISHREE D` is matched to the Tech Titans team led by **Keerthishree D**. The same leader-based matching is applied to other teams, such as `Circuitnerds – GERUBALAKSHMEE S`. If a leader submits more than once, the latest row in the sheet takes priority and earlier rows are treated as superseded. Identical duplicate rows are collapsed. If a leader has no matching submission, that team's resource buttons remain marked as not linked; the site will not borrow another team's links.

## Adding or correcting a direct link manually

Open `teams.json` and add `pptUrl` and/or `videoUrl` to the relevant team object, for example:

```json
{
  "id": "syntaxians",
  "name": "Syntaxians",
  "department": "Information Technology",
  "leader": "Yuvaraj V",
  "members": ["Yuvaraj V", "Praveenraj A"],
  "pptUrl": "https://example.com/presentation",
  "videoUrl": "https://example.com/video"
}
```

Manual links take priority over links loaded from the sheet. For Google Drive, set General access to **Anyone with the link — Viewer** when the files are intended to be public.

## Updating the team roster

Edit `teams.json` to add or update departments, leaders, members, or SIH problem identifiers. Keep each `id` unique. No build tools are required.
