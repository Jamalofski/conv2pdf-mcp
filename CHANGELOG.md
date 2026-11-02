# Changelog

## 1.1.1 (2026-11-02)

- The repository moved to the conv2pdf organization: [github.com/conv2pdf/mcp](https://github.com/conv2pdf/mcp). The package, the plugin, the skill and `server.json` point there, and the plugin installs with `/plugin marketplace add conv2pdf/mcp`; the old address redirects.

## 1.1.0 (2026-10-26)

The server now covers every tool of the conv2pdf API.

- `convert_url_to_pdf` converts the public web page at an address to PDF, as a browser prints it. It takes no input file, so its `output_path` is required.
- `convert_to_pdf` also converts PostScript and EPS files (`.ps`, `.eps`) and HTML files (`.html`, `.htm`, `.xhtml`).
- `split_pdf` puts every page of a PDF in its own PDF file, returned in a ZIP file.
- `extract_pdf_pages` calls the `extract-pages` tool of the API and keeps the pages in the order they are written.
- A refused web page address or page range, a blank page and a single-page PDF to split get their own messages, which say what to change.

## 1.0.1 (2026-10-05)

- The instructions given to the assistant follow the quota rule of the API: a refused setting, such as a page range that does not exist, is no longer counted as a conversion. A file that conv2pdf reads and then refuses still is.
- README: on Windows, the Claude Code command needs `cmd /c` before `npx`.

## 1.0.0 (2026-10-05)

First release.

- Thirteen tools: `convert_to_pdf` (Office documents, Apple Pages, images, HEIC photos and EPUB e-books, chosen from the extension), `convert_heic_to_jpg`, `convert_pdf_to_word`, `convert_pdf_to_images`, `merge_pdfs`, `extract_pdf_pages`, `rotate_pdf`, `add_page_numbers`, `add_watermark`, `compress_pdf`, `protect_pdf`, `unlock_pdf` and `get_quota`.
- A tool reads the file at the path it is given, writes the result next to it or at `output_path`, never overwrites a file, and deletes the job from the conv2pdf server once the result is on disk.
- The tools that read a PDF, except `merge_pdfs`, open one that asks for a password when it is passed as `password`.
- Waits for `Retry-After` when the API rate-limits the key or its queue is full, twice at most and for delays of 30 seconds or less.
- stdio transport, no dependency, protocol revisions 2026-07-28 and 2025-11-25 down to 2024-11-05.
