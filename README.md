# Bookmarks Patcher

Updates the URLs of your bookmarks. Useful if a site changed its domain.

## Contents
* [Getting Started](#getting-started)
*    [Prerequisites](#prerequisites)
*    [Installing](#installing)
* [Built With](#built-with)
* [Contributing](#contributing)
* [Versioning](#versioning)
* [Authors](#authors)
* [License](#license)
* [Acknowledgments](#acknowledgments)
*    [Project History](#project-history)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

A browser. I recommend [Firefox](https://www.mozilla.org/en-US/firefox/new/).

### Installing

Visit [this page](https://maxvalue.github.io/Bookmarks-Patcher). The program runs in the browser.

Export your bookmarks from your browser.

Load them into the program.

Choose the options you like.

Hit `Convert`. The browser will automatically present you the patched bookmarks file.

Save this file and _restore_ your bookmarks from this file.

## Built With

* [Sublime Text 3](https://www.sublimetext.com/) - The code editor I use
* [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/) - The web browser I use

## Contributing

Please open an issue if you wanna help or have questions.

### Roadmap
Things I already plan to implement, but didn't have yet:
- [] Above: Turn all patched sites' links into https.
- [] Above: Patch all.
- [] If the user selects a file it will be automatically read.
- [] Infos: name, type, size, last changed.
- [] user can patch multiple times.

## Authors

* **Max Fuxjäger** - *Initial work* - [MaxValue](https://github.com/MaxValue)

## License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.

## Acknowledgments

* **Mozilla Developer Network Documentation** - *Infos about Web Standards* - [MDN](https://developer.mozilla.org/en-US/)
* **Stackoverflow** - *Infos about Implementation Questions* - [Stackoverflow](https://stackoverflow.com/)

### Project History
This project was created because I (Max) was asked by a friend of mine to build him a program
which can update his browser bookmarks. I put this off for a very long time,
because I didn't know how to make a simple GUI with the programming languages I knew.
Since I am now more focused on web development, I realized that a web app is much more suited for this task.

## Technical Notes
While implementing this, I noticed some things about the bookmark container formats.

### Mozilla's JSON Bookmark Export
* Every bookmark is an object.
* There are 3 different types of objects (defined at the `type` key):
    * "text/x-moz-place": This is a bookmark.
    * "text/x-moz-place-container": This is a subfolder of bookmarks.
    * "text/x-moz-place-separator": This is a separator (the horizontal lines in your bookmarks list) between bookmarks or folders.
* If an object has sub-objects, those get stored in an array at the `children` key.
* Such a children array only has objects as elements.
* In an "text/x-moz-place" object, the `uri` key stores the bookmarked link.

### "Netscape" HTML Bookmark Export
* Is an html document, can be parsed by `DOMParser()`.
* Bookmarks are anchor elements, the bookmarked link is stored in `href` attribute.
