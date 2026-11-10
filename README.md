# Titan Fittings Accountability Chart

The chart lives in `chart.yaml`. `index.html` reads that file and draws the
chart. GitHub Pages republishes the site every time `chart.yaml` changes, so
editing the file is all it takes to update the chart.

## One-time setup

1. **Create the repository.** On github.com, click **New repository**. Name it
   `accountability-chart`. Choose Public (see the privacy note below) and click
   **Create repository**.
2. **Upload the files.** In the new repository, click **Add file > Upload
   files**. Drag in `index.html`, `chart.yaml` and `README.md`, then click
   **Commit changes**.
3. **Turn on GitHub Pages.** Go to **Settings > Pages**. Under **Build and
   deployment**, set Source to **Deploy from a branch**, Branch to **main** and
   folder to **/ (root)**. Click **Save**.
4. **Open the chart.** After a minute or two the Pages screen shows the site
   address, usually `https://<your-username>.github.io/accountability-chart/`.
   Bookmark it.

## Changing the chart

1. In the repository, open `chart.yaml` and click the pencil icon.
2. Make the change:
   - **Put a person in a seat:** fill in `name: "Jane Smith"`.
   - **Move a seat:** change its `reports_to` to the id of its new boss.
   - **Add a seat:** copy an existing block, give it a new `id`, and set
     `reports_to`.
   - **Remove a seat:** delete its block. Move any seats that reported to it
     first.
3. Update `updated:` to today's date.
4. Click **Commit changes**. The site rebuilds in about a minute. The
   **Actions** tab shows progress.

Spacing matters in YAML: keep the same indentation as the blocks around your
change. If something is wrong, the chart page shows a red box naming the
problem, such as a `reports_to` that points to a seat that doesn't exist.

## Multiple versions

One page can show several charts, such as the current chart, a draft, or a
second company. Each version is its own YAML file, and a menu at the top of the
page switches between them.

1. Open `chart.yaml`, click the copy icon to copy its contents, then click
   **Add file > Create new file**. Name it, for example `tam.yaml`, paste, and
   change `company:` and the seats. Commit.
2. Open `versions.yaml`, click the pencil, and add an entry:

   ```yaml
     - file: tam
       label: Titan Advanced Manufacturing
   ```

   Commit.
3. The menu now lists the new version. Each version also has its own link,
   such as `.../accountability-chart/?v=tam`, which you can bookmark or share.

File names can use letters, numbers, dashes and underscores only. `chart.yaml`
is the version shown when no `?v=` is in the link.

## How the layout works

- Seats appear left to right in the order they are listed in `chart.yaml`.
- A seat whose team members have no reports of their own shows the team
  stacked underneath it, which keeps the chart narrow.
- **Hide roles** shows just seats and names. **Print or save PDF** prints in
  landscape. Choose "Fit to page" in the print dialog for a one-page chart.

## Privacy

On free GitHub accounts, a Pages site is public: anyone with the link can see
it. Paid plans can publish from a private repository, but the site itself is
still public unless your organization is on GitHub Enterprise Cloud. Keep that
in mind before adding names.

## Previewing on your own computer

Opening `index.html` by double-clicking won't work, because browsers block it
from reading `chart.yaml`. From this folder, run `python3 -m http.server` and
open `http://localhost:8000`.
