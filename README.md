## Folder Configuration

The __docs__ folder contains all section pages as well as chapter and subchapter index pages.

The path to each type of page in the __docs__ folder is as follows:

- Chapter index page: _chapters/filename
- Subchapter index page: _subchapters/chapter-title/filename
- Section page: _chapter-title/subchapter-title/filename

To have the table of contents update automatically after any updates to the docs, the front matter of the pages contains some information about the respective chapters, subchapters, and section numbers:

- Chapter index pages contain the tag __chapter__ (e.g. __tags: chapter__)
- Similarly, subchapter index pages contain the tag __subchapter__ (e.g. __tags: subchapter__)
- Subchapter index pages have a category named after the respective chapter's title (e.g. __category: support__)
- The section pages have a tag named after the respective subchapter's title (e.g. __tags: faq__)