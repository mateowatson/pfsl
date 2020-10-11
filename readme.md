# Personal File System Library

Personal File System Library is a method of storing e-books and articles from periodicals in a manner that offers longevity, organization, and ease of access. It can also be used to store meta information for real, physical books and articles in one's possession, as well as Kindle or other proprietary-format books if not yet made available in an open format for storing directly in the Library. Additionally, works of other media may be stored, such as audiobooks and films. It is up to you what constitutes a "work." All implementation details are specified in this readme document.

## Overview

PFSL was created by [Matt Watson](https://www.mattwatson.org/) as a way to organize not only his e-book collection, but also his reading and comprehension progress of those books. At first he tried using spreadsheets, then a WordPress-powered database, but he finally realized the regular computer file system was his ticket out of chaos and disorder. The file system is like library shelves, and PFSL is like the Dewey Decimal System (but less complicated and no numbering!). If the Dewey Decimal System was created with the ambition of organizing all knowledge, PFSL was created to organize all *of an individual's* knowledge. No two PFSLs are the same! You can't break the rules; you can only extend your own implementation spec!

## Benefits

- It focuses on open formats. While it allows for any kind of work, PDFs and e-pubs are the best fit for PFSL.
- It doesn't lock you in to a third-party services, such as AirTable, Google Docs (for notes), etc. Your PFSL will live forever, unless you don't back it up or we enter a post-apocalyptic world with no electricity.
- It is interactive, in a sense. Imagine going to your local library or bookstore and being able not only to read a book and put it back, but also put it back with your notes, annotations, and bookmarks safely attached to it.
- It keeps things separate. It makes heavy use of folders and folder naming conventions to organize chaotic files. Your note files may be insane and unorganized, but they will all be in the `notes` folder of the book in question.
- It keeps things together. All of your books and book knowledge can be stored in a PFSL (given an infinite time scale). The possibilities are endless. No more tracking down random files on your computer.
- It's good for developers. It's plain text files using [Markdown](https://daringfireball.net/projects/markdown/). A PFSL can be opened in a text editor. In VSCode you can even install an extension to read your PDFs right there in the editor, which helps with note-taking. You could even git version it if you wanted, although you would probably want to gitignore the actual PDF files and any other large media files.

## The rules of the PFSL method

Enough talk. Let's get down to brass tacks. Below are the rules for creating a PFSL:

1. The top level of the library contains an `inbox` folder, a `work` folder, a `bookmarks.md` file, a `meta-template.md` file, and a `readme.md` file with the text you are reading now. Other files and folders can be included at the top level for personal convenience but are not part of the library. (Note: For any standard plain text files, such as `meta-template.md` file or any other mentioned hereafter, you may drop the md extension or use another extension of your choice, such as txt.)
2. A book should consist of a single folder, with a near-unique name, that is, at least unique to other file or folder names at its level and at best unique to the entire library. The folder name for a book should:
    1. be camel cased with the first letter being capitalized
    2. have the articles *a*, *an*, and *the* placed at the end preceded by an underscore
    3. not include subtitles.
3. Additionally, a book folder name can:
    1. be shortened as appropriate
    2. contain extra words to uniquely identify it where necessary, in which case, all extra words should be camel cased and preceded by an underscore, as in, for example, `HolyBible_The_Benziger1914` for a bible published by the Benziger Brothers publishing company in 1914.
4. A book folder should contain at its top level only the folders specified in this document, and no files. The allowed folders are `main`, `meta`, `notes`, `bookmarks`, and `annotations`. It is required to have at least a `main` and a `meta` folder.
5. The file(s) that comprise the book should be dumped in the book's `main` folder. No other files should be placed in `main`, only the primary text, which hopefully is only one file. However, there are times when more than one file might comprise a work, including books chunked into multiple PDFs, static websites, photos of pages, and the like. Since the actual book file(s) is in the `main` folder, it does not itself have any naming rules. However, it should be clear (to at least yourself, since it's **your** personal library, after all) how the book should be read. If the book is a real, physical book, or a Kindle or other proprietary-format book, then simply put a note in this folder indicating where to find the book. It is recommended to put this note in a file called where.md.
6. All meta info for the book goes in the `meta` folder. You must create at least one file there called `meta.md`. We refer to this as a "standard meta file." It is simply a series of key-value pairs, or fields, with the field name being a Markdown heading one (denoted by a hashtag) and the value being the text underneath it. The value ends at the next heading one or end of file. To create this file, copy and paste the contents of the `meta-template.md` file at the library root and fill in as many values as are necessary and appropriate.
7. You may add additional "custom fields" to a `meta.md` file, but it is highly recommended to also add these fields to your `meta-template.md` file so that you will remember to include the field in future books where necessary. This gives you wide latitude to expand your personal library meta data tracking to fit your own needs.
8. Although you have wide liberty to change your `meta-template.md` file as needed, it should at least contain a **Title** field and an **Author** field.
9. Put all notes in the `notes` folder of a book folder. You may organize your `notes` files however you want, but plain text Markdown files are recommended. Keeping `notes` to one file named simply notes.md is recommended where possible.
10. An `annotations` folder in the book folder should hold PDFs that have been annotated in any way using PDF annotation software. It may also include any other scenarios that may be construed as an *annotation* -- any virtual manner of highlighting, underlining, writing marginal notes, etc. This is done in order to keep the original book file pristine in its original form and to keep things separate. An example would be to copy a PDF file from `main` to `annotations` and annotate it there. When possible, it is good to use annotation software, such as Xournal, that allows you to make an annotation file that simply points to the PDF file in `main`, in order to keep the size on disk to a minimum.
11. The `bookmarks` folder within a book folder should contain at least a `bookmarks.md` file that indicates the last page you left off on, or any other page numbers or locations you would like to mark.
12. Going back up to the root level of the library, the `inbox` folder contains "new arrivals" that have not yet been sorted. This is where you will drop a new file, such as a PDF, e-pub, etc. It is always good to sort new arrivals immediately rather than use `inbox`, because some book meta may be harder to track down later, such as url and web access date. Nonetheless, if you are lazy or in a hurry, drop the new text there. The `inbox` folder should mostly be kept to a flat list of files, no folders. However, if a work is spread over multiple files, as in a website or several PDFs, then put all files that comprise the work in a single folder named whatever you want.
13. All books (book folders) should be placed in the `works` folder. They can be further organized within the `works` folder in two ways:
    1. You can use the `/works/authors` folder. The `authors` folder, if you use it, has certain rules. Namely, it should be a flat list of folders named after the author in question, kebab-case, with the first name last and preceded my an underscore. For example, a book folder named `TomSawyer` could be placed in the file system as `/works/authors/twain_mark/TomSawyer/`. The book folder `CalculusMadeEasy` could be placed as `/works/authors/thompson_silvanus-p/CalculusMadeEasy/`.
    2. Another option is to drop the book folder in "category folders" named in kebab case. All category folders should be placed in `/works/categories/`. Category folders can be nested however many levels you want. Since they are in kebab case, they will be distinguishable from book folders even if they coexist with book folders in the same parent folder. Category folders are ideal for works by multiple authors, or collections of works you want to group together for whatever reason. As a general rule of thumb, use `authors` for works associated with a single main author, and `categories` for bibles, reference works, etc. For example, the book folder we mentioned earlier named `HolyBible_The_Benziger1914` could be placed as `/works/categories/bibles/HolyBible_The_Benziger1914/` or `/works/categories/religion/bibles/douay-rheim/HolyBible_The_Benziger1914/`. Be careful not to get too carried away with categories. It needs to be something that makes sense and enhances findability, not hinders it.
14. The `bookmarks.md` file at the root level of the library is for writing down the books you are currently reading, or any other books, pages, or book locations you want to keep track of for whatever reason. In fact, you can use this file instead of the bookmarks file associated with an individual book, if you prefer. In that case, you should not create a bookmarks folder for the book in question.
15. Don't create empty folders or files. Very often, you might not have an `annotations`, `bookmarks`, or `notes` folder for a given work.

## File tree view examples

As we have already said, all books should be placed in the `works` folder. In a simple scenario, your library file tree could look like this:

```
inbox/
    tomsawyer.pdf
works/
    AdventuresOfHuckleberryFinn_The/
        annotations/
            huckfinn.xoj
        main/
            huckfinn.pdf
        meta/
            meta.md
        notes/
            notes.md
    DeepWork/
        annotations/
            deep-work.xoj
        main/
            deep-work.pdf
        meta/
            meta.md
        notes/
            notes.md
bookmarks.md
meta-template.md
readme.md
```

But if we expanded it to include the `authors` folder, it would look like:

```
inbox/
    tomsawyer.pdf
works/
    authors/
        mark_twain/
            AdventuresOfHuckleberryFinn_The/
                annotations/
                    huckfinn.xoj
                main/
                    huckfinn.pdf
                meta/
                    meta.md
                notes/
                    notes.md
        newport_cal/
            DeepWork/
                annotations/
                    deep-work.xoj
                main/
                    deep-work.pdf
                meta/
                    meta.md
                notes/
                    notes.md
bookmarks.md
meta-template.md
readme.md
```

If we added a dictionary, we could place it to the top level of `works`, like this:

```
inbox/
    tomsawyer.pdf
works/
    authors/
        mark_twain/
            AdventuresOfHuckleberryFinn_The/
                annotations/
                    huckfinn.xoj
                main/
                    huckfinn.pdf
                meta/
                    meta.md
                notes/
                    notes.md
        newport_cal/
            DeepWork/
                annotations/
                    deep-work.xoj
                main/
                    deep-work.pdf
                meta/
                    meta.md
                notes/
                    notes.md
    MerriamWebstersSchoolDictionary/
        main/
            Merriam-Websters-School-Dictionary.pdf
        meta/
            meta.md
bookmarks.md
meta-template.md
readme.md
```

Or we could expand our library to use the `categories` folder, like this:

```
inbox/
    tomsawyer.pdf
works/
    authors/
        mark_twain/
            AdventuresOfHuckleberryFinn_The/
                annotations/
                    huckfinn.xoj
                main/
                    huckfinn.pdf
                meta/
                    meta.md
                notes/
                    notes.md
        newport_cal/
            DeepWork/
                annotations/
                    deep-work.xoj
                main/
                    deep-work.pdf
                meta/
                    meta.md
                notes/
                    notes.md
    categories/
        reference/
            dictionaries/
                MerriamWebstersSchoolDictionary/
                    main/
                        Merriam-Websters-School-Dictionary.pdf
                    meta/
                        meta.md
bookmarks.md
meta-template.md
readme.md
```

## The meta template file

The `meta-template.md` file must contain at least the **Title** and **Author** heading and a value under it, as mentioned, but the following is the currently recommended content for that file:

```
# Author
# Author Full Name
# Secondary Authors
# Title
# Full Title
# Version
# Language
# Description
# Tags
# Type
# Format
# Provider
# Publisher
# Publisher City
# Publication Date
# Original Publication Date
# Editors
# Translators
# Permalink
# Web Access Date
# Pages


# Publication Name
# Publication Volume
# Publication Issue
# Publication Page Range


# ISBN


# Citation - MLA
```

Again, use `meta-template.md` to copy to your newly created `meta.md` files. Note that spacing is added to separate fields that seem to belong together, but this is arbitrary.

It is OK to leave fields blank in a `meta.md` file.

Most of the fields are self explanatory, but some need more explanation and use certain conventions:

- Author: This follows similar rules to those of naming author folders, but written with spacing and natural punctuation. If the author folder is named `thompson_silvanus-p`, then this field should be "Thompson, Silvanus P.".
- Author Full Name: This should be the author's full name, naturally written, as in "Silvanus P. Thompson".
- Secondary Authors: Any additional authors listed, one per line, written in the same format as Author Full Name
- Title: This follows similar rules to those of naming the book folder, but written with spacing and natural punctuation. If the book folder is named `AdventuresOfHuckleberryFinn_The`, this field should be "Adventures of Huckleberry Finn, The". If the book folder name includes additional words preceded by an underscore, the Title should reflect that. Therefore, if the book folder is named `AdventuresOfHuckleberryFinn_The_1960Edition`, this field should be "Adventures of Huckleberry Finn, The, 1960 Edition".
- Full Title: This is the full title of the book, written normally, including the subtitle, and in title caps. For example, the book with the Title of "Calculus Made Easy" has a Full Title of "Calculus Made Easy: Being a Very-Simplest Introduction to Those Beautiful Methods of Reckoning Which Are Generally Called by the Terrifying Names of the Differential Calculus and the Integral Calculus".
- Version: This field is for specifying "Second Edition" etc.
- Type: The media type, such as book, periodical, video, audio, etc.
- Format: The file format or physical format, such as PDF, Kindle, e-pub, physical book, etc.
- Provider: The website or other source the text came from, especially for PDF scans of real books and the like, such as archive.org.

The reason **Title** and **Author** are required in the meta template file is because they have that special connection to the naming rules of a book folder and an author folder. While no fields are required in an actual `meta.md` file for a book, you will need these two fields most of the time, and their special meaning should be kept in mind.