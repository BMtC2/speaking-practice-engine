# How to put these files online with GitHub Pages

This folder holds the speech files for the Blackboard edition of the speaking practice tool. They need to
be on a public web address so that the page in Blackboard can download them. GitHub Pages does this for
free. You only use the GitHub website in your browser; you do not need to install anything.

Allow about 20 minutes the first time. Use Chrome or Edge for the upload (they keep folders when you drag
them in; Safari may not).

## What you need

- A GitHub account. If you do not have one, go to https://github.com, click **Sign up** and follow the steps.
- This folder (`dist-engine`) on your computer. It holds 25 files, none bigger than 5 MB, about 57 MB in
  all. The GitHub website refuses an upload that is too big, so you upload it in three smaller batches
  (step 2).

## 1. Create the repository

1. Go to https://github.com and sign in.
2. Click the **+** button at the top right, then **New repository**.
3. In **Repository name**, type `speaking-practice-engine`.
   (You can choose another name. It becomes part of the web address.)
4. Choose **Public**. GitHub Pages on a free account only works for public repositories. That is fine:
   these are open-source files with no student data.
5. Leave everything else as it is (no README, no .gitignore, no licence).
6. Click **Create repository**.

## 2. Upload the files (four batches)

The files come in four zip files: `upload-1-of-4.zip` to `upload-4-of-4.zip`, each under 20 MB. The GitHub
website refuses one big upload ("Commit failed – the file is too large"), so upload them one at a time.
GitHub merges folders with the same name, so each batch lands in the right place.

For each batch, in order 1, 2, 3, 4:

1. Unzip it. You get a folder such as `upload-1-of-4`.
2. On GitHub, go to the repository's main page.
   - First batch only: on the empty repository page, click **uploading an existing file**.
   - Batches 2 to 4: click **Add file** (top right of the file list), then **Upload files**.
3. Open the `upload-…` folder on your computer, select **everything inside it** (Ctrl+A on Windows, Cmd+A on
   a Mac) and drag it onto the box that says "Drag files here". Drag what is inside, never the
   `upload-…` folder itself.
4. Wait until every file is listed, scroll down and click the green **Commit changes** button.

What is in each batch:

| Batch | Contents | Size |
|---|---|---|
| 1 | `index.html`, `HOW-TO-UPLOAD.md`, `SHA256SUMS.txt`, `.nojekyll`, `LICENSES/`, `vendor/` | about 12 MB |
| 2 | `models/silero-vad/`, and in `models/moonshine-v2-tiny-en/`: `tokens.txt`, `encoder.ort.part1` to `part3` | about 14 MB |
| 3 | `models/moonshine-v2-tiny-en/decoder.ort.part1` to `part4` | about 17 MB |
| 4 | `models/moonshine-v2-tiny-en/decoder.ort.part5` to `part7` | about 13 MB |

`.nojekyll` is a hidden, empty file; on a Mac press Cmd+Shift+. (full stop) in Finder to see it. If it does not
upload, the site still works.

When you are done, `models/moonshine-v2-tiny-en/` on GitHub holds 11 files and `vendor/sherpa-onnx/vad-asr/`
holds 6 files.

## 3. Turn on GitHub Pages

1. In the repository, click **Settings** (the tab with the cog, at the top of the repository page).
2. In the left-hand menu, under "Code and automation", click **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Under **Branch**, choose **main** in the first box and **/ (root)** in the second box. Click **Save**.
5. Wait one to three minutes, then reload the Pages settings page. At the top it now says
   "Your site is live at" followed by an address like
   `https://yourname.github.io/speaking-practice-engine/`.
6. Click **Visit site**. You should see a short page titled "Speaking practice engine files". If you see
   "404", wait a minute and reload.

## 4. Connect the Blackboard page

1. Copy the site address from step 3.5, including the `/` at the end, for example
   `https://yourname.github.io/speaking-practice-engine/`.
2. Open `speaking-practice-bb.html` in a plain text editor (Notepad on Windows, TextEdit on a Mac in
   plain text mode). Near the top, find the line

   `var ENGINE_BASE = 'https://REPLACE-ME.github.io/speaking-practice-engine/';`

   and replace the address between the quotes with yours. Keep the quotes. Save the file.

   Or, without touching that line: on the `<html ...>` line at the very top, fill in
   `data-engine-base="https://yourname.github.io/speaking-practice-engine/"`. When this is filled in, it wins.
3. Upload the saved file to Blackboard the same way as your other HTML modules.
4. Open it in Blackboard and click **Set up speaking practice**. The download (about 57 MB) runs once per
   browser. If the page says "The speech files for this page are not connected yet", the address is still
   the placeholder or does not start with `https://`.

## If something goes wrong

- **The page says the site "did not let this page use them".** The host did not send the header that lets
  other sites read its files. GitHub Pages always sends it, so check that the address is the
  `github.io` one from step 3.5, not the `github.com/...` address of the repository.
- **The page says the speech files are missing.** An address is wrong. Open
  `https://yourname.github.io/speaking-practice-engine/models/silero-vad/silero_vad.onnx` in your browser:
  it should download a small file. If you uploaded the `dist-engine` folder itself, the files are one level
  down: add `dist-engine/` to the end of the address you use in ENGINE_BASE.
- **The page says the files "did not match what we expected".** A file was damaged or replaced. Delete the
  repository's files and upload this folder again.
- **Updating later.** Upload the new files the same way; files with the same name are replaced.
- **Who sees what.** GitHub sees the address and browser of anyone who downloads the files, like any
  website. It never sees students' audio or transcripts: those stay on the student's device.
