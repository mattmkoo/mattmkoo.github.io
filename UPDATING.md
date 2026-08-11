# How to update your website

You can make every change below directly on GitHub in your browser — open the
file, click the pencil icon to edit, then click **Commit changes**. The site
rebuilds and goes live automatically within about 2 minutes of each commit.

## Where the text lives

**All of your written content is in the `data/` folder**, one clearly-named
file per section:

| Section on the site | File |
|---|---|
| Homepage bio | `data/bio.yaml` |
| Tagline (line under your name) | `data/tagline.yaml` |
| Interests | `data/interests.yaml` |
| Education | `data/education.yaml` |
| Research (papers) | `data/research.yaml` |
| Data Projects | `data/data_projects.yaml` |
| Teaching intro paragraph | `data/teaching_note.yaml` |
| Teaching courses | `data/teaching_courses.yaml` |
| Invited Talks | `data/invited_talks.yaml` |
| Field Notes intro | `data/field_notes.yaml` |

Settings that aren't written content (email, social links, banner photos)
live in `hugo.yaml`. The CV, photos, and Field Notes images are files (see below).

## Add a new paper

1. Open `data/research.yaml` and add an entry:

   ```yaml
   - title: "Your New Paper Title"
     section: working            # "working" or "in-progress"
     coauthors: ["Name (Institution)"]   # omit if solo-authored
     status: "under review"      # working paper / under review / revise and resubmit / accepted / published
     pdf: "files/your-paper.pdf" # omit if no PDF yet
     abstract: "Full abstract text…"   # optional; adds an expandable "Abstract" toggle
   ```

2. If there's a PDF, upload it to `static/files/` (Add file → Upload files).

An `abstract:` line on a working paper or work-in-progress adds a small
"Abstract" toggle that readers click to expand. (The job market paper always
shows its abstract in full.)

## Mark a paper as published

In `data/research.yaml`, change its `status:` to `"published"` and add a
`venue: "Journal Name"` line.

## Change the job market paper

Move `job_market_paper: true` to the relevant entry in `data/research.yaml`.
To show its abstract on the homepage card, add an `abstract: "..."` line.

## Update your bio, tagline, or interests

- Bio paragraphs: `data/bio.yaml` (each list item is one paragraph; Markdown
  links and _italics_ work).
- Tagline: `data/tagline.yaml`.
- Interests: `data/interests.yaml`.
- Email and social links: the `params:` section of `hugo.yaml`.

## Add a teaching entry, invited talk, or edit the teaching note

- Courses: add an entry to `data/teaching_courses.yaml`.
- Invited talks (shown under Teaching): add an entry to `data/invited_talks.yaml`.
- The intro paragraph under the Teaching heading: `data/teaching_note.yaml`.

## Update your CV

Replace `static/files/cv_koo.pdf` with the new version — keep the filename
`cv_koo.pdf` so existing links keep working. The CV opens in an embedded
viewer at `/cv/`; the download link there serves the same file.

## Change your photo

Replace `assets/images/photo.jpg` with a new image (same filename).

## Edit the Field Notes photos

The intro paragraph is in `data/field_notes.yaml`. The photos themselves live
in `content/field-notes/` and all of them appear in the Field Notes section:

- **Add a photo:** upload a `.jpg` into that folder. It appears
  automatically (thumbnails are generated for you).
- **Remove a photo:** delete its `.jpg` from the folder.
- **Reorder photos:** photos appear in filename order — the files are named
  `field-01.jpg`, `field-02.jpg`, … so rename to control the order.
- **Caption or rotate a photo:** open `content/field-notes/index.md` and add
  an entry under `resources:` in the front matter (captions/rotations stay
  with the photos, so they live here rather than in `data/`):

  ```yaml
  resources:
    - src: "field-03.jpg"
      params:
        caption: "Kuala Lumpur, election day 2022."
        rotate: 90   # optional — degrees clockwise (90, 180, or 270)
  ```

  Photos without an entry appear as-is, without a caption.

## Change the banner photos

The homepage's top banner and the photo banners before sections are set in
`hugo.yaml` under `params.banners`. Each entry names a photo, looked up in
`content/banners/` first and then `content/field-notes/`. Each section
banner has a `style`: `"strip"` (cropped full-width band), `"fit"` (whole
photo height shown, blurred fill at the sides), or `"multi"` (an `images:`
list shown side by side, left to right, each optionally with `rotate:`).
Remove an entry to remove that banner.

## Add your social profile links

In `hugo.yaml` under `params.social`, paste your Google Scholar, ORCID, and
GitHub profile URLs into the empty quotes. Buttons appear automatically once
a link is filled in; empty ones stay hidden.

## Remove the footer credit or the invisible marker

In `hugo.yaml`, set `params.mysite.credit: false` (footer credit) or
`params.mysite.discovery: false` (hidden metadata).
