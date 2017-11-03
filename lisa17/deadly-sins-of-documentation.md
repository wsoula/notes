7 Deadly Sings of Documentation
---
* should have a runbook and a description of the entire system
* runbooks
  * address specific questions, link to answers from alerts
  * use inverted pyramid format, put the most important info or common questions at the top
  * make sure your example commands will be benign
  * have explanations of why you're doing this, but keep them short - one or two sentences
  * make sure the steps in the runbook actually work
* repository overload - docs everywhere, should be in one central location, at least links
  * don't use email, chat logs, or tickets as primary sources of docs
  * make sure repository is seachable and can track changes
  * provide portal that give easy access points into docs, especially one that surfaces
    critical or top-level docs
* Outdated, conflicting, or misleading
  * not updated to reflect new realities
  * keeping docs around for historical purposes clutters searches and can slow incident response
  * old, incorrect docs around, lead to longer outages as people try to find the correct one
* Pruning the Garden
  * include documentation in project goals
  * instead of keeping old docs around, pull out what is still useful and incorporate into new docs
  * if you need them archive them to not show up in searches
  * Best way is to use and update the docs regularly
* Comment Neglect
  * even good code does not show the context of how decisions were made about why the code was written that way
  * tendency to assume code is easy to read because you have been working in it for weeks
  * someone else may not have as good an understanding of the language or functionality of the code
* Video
  * video is more engaging than text (maybe)
  * can be easier to present and explain complex topics in a video than a flat document
  * can be more memorable than a flat document
  * big problem is not easily searched
  * if there's no content marks, you've got to watch the whole thing to find what you need
  * Much harder to edit if the content needs updating
  * Accessibility is harder - screen readers don't work well with them and video need subtitles
* Summary
  * have runbooks and in-depth tech docs but not in same place
  * store docs in one or two repos that keep history and are easily searchable
  * docs arent extra work but necessary work
