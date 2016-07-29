# EBook generation (beta)
Inspired by *GitBook*  
**Markdown Preview Enhanced** can output content as ebook (ePub, Mobi, PDF).   

To generate ebook, you need to have `ebook-convert` installed.  

## Installing ebook-convert
**OS X**  
Download the [Calibre Application](https://calibre-ebook.com/download). After moving the calibre.app to your Applications folder create a symbolic link to the ebook-convert tool:
```shell
$ sudo ln -s ~/Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin
```
**Windows**  
Download and Install the [Calibre Application](https://calibre-ebook.com/download).  
Add `ebook-convert` to your system path.

## Start writing EBook    
You can set up a ebook configuration by simply inserting `<!-- ebook -->` into your markdown file.  
General settings:  
* **title**  
title of your book  
* **authors**  
author1 & author2 & ...  
* **publisher**  
who is the publisher?  
* **book-producer**  
who is the book producer  
* **pubdate**  
publish date  
* **isbn**  
ISBN of the book  
* **cover**  
http://path-to-image.png  
* **epub-toc-at-end**  
whether to put TOC at the end
* **margin-top**  
Set the top margin in pts. Default is 5.0. Setting this to less than zero will cause no margin to be set (the margin setting in the original document will be preserved). Note: 72 pts equals 1 inch
* **margin-right**
* **margin-bottom**
* **margin-left**  
* **cdn**  
Load css and javascript files from `cdn.js`. This option is only used when exporting `.html` file.  

All values of settings should be within **double quotes**.     
For example, I created a `SUMMARY.md` file, and I added the following configuration.

```
<!--  ebook
      title:"Markdown Preview Enhanced"
      author:"shd101wyy" -->
```

The `SUMMARY.md` should also have a TOC to help organize the book:
```markdown
<!--  ebook
      title:"Markdown Preview Enhanced"
      author:"shd101wyy" -->

# Preface  
This is the preface, but not necessary.

# Table of Contents
* [Chapter 1](/chapter1/README.md)
  * [Introduction of Markdown Preview Enhanced](/chapter1/intro.md)
  * [Features](/chapter1/feature.md)
* [Chapter 2](/chapter2/README.md)
  * [Known issues](/chapter2/issues.md)
```

The link's title is used as the chapter's title, and the link's target is a path to that chapter's file.  

---

To export ebook, open the `SUMMARY.md` with the preview opened. Then right click at the preview, choose `Export to Disk`, then choose `EBOOK` option. You can then export your ebook.

## EBook Example
An EBook example project can be found [here](https://github.com/shd101wyy/ebook-example).   

## About .html export
Exporting `.html` doesn't depend on `ebook-convert`.  
If you are exporting `.html` file, then all local images will be included as `base64` data inside a single `html` file.

## Known Issues & Limitations
* All SVG graph generated by `mermaid`, `PlantUML`, etc will not work in the ebook generated. Only `viz` works.   
* Only **KaTeX** can be used for Math Typesetting.   
  And the generated ebook file doesn't render math expression properly in **iBook**.
* **PDF** and **Mobi** generation is buggy.