# About this website

This website was created using [Jekyll](https://jekyllrb.com/)
and hosted using GitHub Pages. This page documents the
implementation and maintenance of the website.

The source can be found at
[https://github.com/OpenC2-org/openc2-org.github.io](https://github.com/OpenC2-org/openc2-org.github.io).

Additions/corrections/suggestions are welcome.

Contents of this README.md file:
- [About this website](#about-this-website)
  - [Website Structure](#website-structure)
  - [Maintaining the Website](#maintaining-the-website)
    - [How to add/remove slides in the carousel on the homepage](#how-to-addremove-slides-in-the-carousel-on-the-homepage)
    - [How to update the news timeline in "OpenC2 in the news" page](#how-to-update-the-news-timeline-in-openc2-in-the-news-page)
    - [How to update the Frequently Asked Questions (FAQ) page](#how-to-update-the-frequently-asked-questions-faq-page)
    - [How To Update the Publication History Page](#how-to-update-the-publication-history-page)
  - [How to run the website on your local computer](#how-to-run-the-website-on-your-local-computer)
  - [Contributing](#contributing)

## Website Structure
The folder and file organization of the website source is shown
here:
```
.
+-- _includes
|   -- footer.html                  # Contains code to include Back to Top button and JavaScript used in this website.
|   -- header.html                  # Contains code to include Stylesheets used in this website.
|   -- navbar.html                  # Contains code to display top level and mobile navigation including website search.
+-- _layouts
|   -- default.html                 # Contains HTML and Jekyll code to implement a re-usable page layout. (Used for index.html)
|   -- page.html                    # Imports the layout used for default.html and adds extra layout to present inner HTML pages.
|
+-- _faqs                           # Folder for collection of FAQ files used to build the FAQ page
|   +-- faq_100-<faq>.md            # First FAQ question / response.
|   +-- faq_110-<faq>.md            # Second FAQ question / response.
|   +-- faq_xxx-<faq>.md            # additional FAQ question / response files
+-- _news                           # Folder for collection of news item files used to build the OpenC2 In The News page
|   +-- news_20200127.md            # News item for January 27, 2020
|   +-- news_20200306.md            # News item for March 6, 2020
|   +-- news_xxxxxxxx.md            # additional news item files
+-- _sass
|   +-- main.scss                   # Contains re-usable SASS properties for the website.
+-- assets
|   +-- css
|       -- main.scss                # Imports the re-usable SASS properties for the website.
|       -- style.css                # Contains CSS for each section of the website.
|   +-- img   
|   +-- js
|       -- main.js                  # Contains JavaScript used for this website.
|   +-- vendor
|       +-- animate.css             # Supports Basic animations like Fade up, Fade Down etc.
|       +-- aos                     # To animate HTML elements when a user slides down a page.
|       +-- bootstrap
|       +-- boxicons
|       +-- icofont
|       +-- jquery-sticky
|       +-- jquery.easing
|       +-- jquery
+-- content
|   +-- homepage
|       +-- carousel
|           -- slide1.html           # HTML imported for First Slide of the Carousel in index.html
|           -- slide2.html           # HTML imported for Second Slide of the Carousel in index.html
|           -- slide3.html           # HTML imported for Third Slide of the Carousel in index.html
|           -- slide4.html           # HTML imported for Fourth Slide of the Carousel in index.html
|       -- current-cyberdefense.md   # Markdown imported in "Current CyberDefense"  paragraph in index.html
|       -- defense-cybertime.md      # Markdown imported in "OpenC2 for Defense in Cyber-Relevant Time" paragraph in index.html
|       -- openc2-help.md            # Markdown imported in "How can OpenC2 help?" paragraph in index.html
|       -- vision.md                 # Markdown imported in "Vision" paragraph in index.html
+-- pub-histories
|   -- ap-dev-cn-hist-table.md       # Markdown file with publication history for AP Development Committee Note.
|   -- arch-hist-table.md            # Markdown file with publication history for Architecture Specifications.
|   -- ...                           # Markdown files with publication history for other TC work products.
+-- vectors
|   -- attackspeed.ai                # Original illustration for the picture used in "Current CyberDefense".
|   -- automate.ai                   # Original illustration for the picture used in "OpenC2 for Defense in Cyber-Relevant Time".
|   -- openc2-help.ai                # Original illustration for the picture used in "How can OpenC2 help?" part of the homepage.
|   -- vision.ai                     # Original illustration for the picture used in "Vision" part of the homepage.
+-- _site                            # Folder generated locally when jekyll serve is run. This should not be checked in to the repo.
-- 404.html                          # Invalid URLs point to this page.
-- CNAME                             # Contains Domain name of the OpenC2 website.
-- _config.yml                       # Jekyll configuration for this website. Requires Server Restart each time it's changed.
-- contact.html                      # https://openc2.org/contact.html
-- faqs.html                         # Automation page to build Frequently Asked Questions from _faqs collection
-- favicon.ico
-- index.html                        # HomePage of this website.
-- joinus.html                       # Join Us
-- news.html                         # OpenC2 in the News
-- oasis.html                        # What is OASIS?
-- openc2.html                       # About this Website
-- opensource.html                   # Opensource Software
-- otc.html                          # OASIS OpenC2 Technical Committee
-- otherdocumentation.html           # Other Documentation
-- pubhist.html                      # Detailed publication histories of TC work products; imports from pub-histories folder
-- README.md                         # Documentation on how to use/contribute to this website
-- specifications.html               # Specifications

```

## Maintaining the Website

### How to add/remove slides in the carousel on the homepage
```index.html``` is the homepage and it uses [Bootstrap
Carousel](https://getbootstrap.com/docs/4.0/components/carousel).
Please refer to it's documentation to learn more about it.

To add a new slide to the carousel, create a HTML content file in
```content/homepage/carousel``` folder similar to other
```slide-*.html``` files

Open ```index.html``` and add the HTML code inside the
```carousel-inner``` section to reflect the following change.

```
        <!-- Slide 5 -->
        <div class="carousel-item">
          <div class="carousel-container">
            <div class="carousel-content container">
            <!-- Include slide5.html using Jekyll's include_relative tag. 
            See here for more info: https://jekyllrb.com/docs/includes 
            -->
            </div>
          </div>
        </div>
```

To remove unwanted slides, delete the HTML code and content file
for the unused slide.

### How to update the news timeline in "OpenC2 in the news" page
The `_news` folder contains the collection of individual news
item files, stored one per file in Markdown format. The file
structure is simple:

```
---
screen-date:  Month dd, yyyy
sort-date: yyyymmdd
title: 
title-url: 

---
<news item text>
```
where
 - `screen-date` is the date the event occurred, which will be
   displayed for the item on the *In The News* page
 - `sort-date` is the same date in a format that permits sorting
   the news items by date
 - `title` is the title text that will be displayed for the item
   on the *In The News* page
 - `title-url` is the website that the news item title text will
   link to
 - `<news item text>` is the content that will display below the
   date and title; content can include additional web links

News item files are named `news_YYYYMMDD.md`; if multiple news
items occur on the same date, the convention is to append a
letter ("a", "b", etc.) to the filename to assign unique
filenames. The filenames are not significant to the sorting of
news items; that is controlled by the `sort-date` property in the
front matter.

The "OpenC2 In The News" page is built from this collection by
the `news.html` file using Jekyll / Liquid scripting, generating
the ```news.html``` page on the website where the timeline is
presented. 

*In The News Maintenance Procedures*

 - **To add a news item**: add a new file in the `_news` folder,
   using the `news_YYYYMMDD.md` file naming convention described
   above (opening an existing item and doing a *Save As* to the
   new filename is the easiest method). Populate the four fields
   in the news item front matter and the news item text in the
   body appropriately, as described above.
 - **To update a news item**: edit the properties in the front
   matter and/or the news item text in the body of the
   corresponding news item file.
 - **To delete a news item**:  delete the corresponding news item
   file.
 - **To re-order the news item**: change the `sort-date` value(s)
   in the relevant news item file(s) to adjust the sorting
   sequence.

Notes:
1) The `title` property in the front matter *cannot* contain a
   colon (":"), as this causes a parsing error resulting in a
   blank title for the news item on the In The News page; use a
   dash ("-") instead.
2) Complete URLs should be employed when placing web links in
   news item bodies; relative URLs within the website should be
   avoided.



### How to update the Frequently Asked Questions (FAQ) page
The `_faqs` folder contains the collection of FAQs, stored one
per file in Markdown format. The file structure is simple:

```
---
question: <question text>
---
<response text>
```
The FAQ page is built from this collection by the `faqs.html`
file using Jekyll / Liquid scripting. The sequence of FAQs on the
page is controlled by the number portion of the individual FAQ
file names. The numbering is deliberately spaced (i.e., faq_100,
faq_110, faq_120) to simplify adding or re-sequencing the FAQs.

The `faq_XXX` filenames can be extended with "explainer"
information to make it easier to identify FAQs from their
filenames. Some examples:

 - `faq_100-W-I-OpenC2.md` -- FAQ file containing the "What is
   OpenC2?" FAQ and response
 - `faq_200-RT-CACAO.md` -- FAQ file containing the "How does
   OpenC2 relate to CACAO?" FAQ and response

Shorthand conventions in this filename scheme include `-W-I-` for "What Is", and
`-RT-` for "relate to" questions. For purposes of FAQ sequencing, the
"explainer" portion of the filename is irrelevant.

*FAQ Maintenance Procedures*

 - **To add an FAQ**: add a new file in the `_faqs` folder, using
   the `faq_nnn.md` file naming convention, where the value of
   `nnn` places the FAQ in the desired order. Populate the
   question text in the header and the response text in the body, as described above.
 - **To update an FAQ**: edit the question text in the header
   and/or the response text in the body of the corresponding FAQ
   file.
 - **To delete an FAQ**:  delete the corresponding FAQ file
 - **To re-order the FAQs**: rename the relevant FAQ file(s) by
   changing the numeric portion of the filename to adjust the
   sequence.

Notes:
1) The question portion of the FAQ file should be plain text
   without formatting and without any web links
2) Complete URLs should be employed when placing web links in FAQ
   responses; relative URLs within the website should be avoided.


### How To Update the Publication History Page

The publication histories are delivered via an HTML page (`pubhist.html`). Each
TC work product has a section in the page which includes the title, a copy of
the document's abstract, and a history for each publication stage showing
version, publication identifier, and date. The publication history tables are
contained in individual markdown files, one per work product, which are imported
by `pubhist.html`. This simplified maintenance by eliminating the need to edit
an HTML table, however the imported Markdown tables use HTML anchors to create
web links that open in new tabs / windows (i.e., `target="_blank"`).

 - To add a publication event to an existing work product: located and edit the
   corresponding history table file in the `pub-histories` folder.
 - To add a new work product:
   - Update `pubhist.html`: Create a new section in the document for the new
     work product (e.g., by copy / paste / edit of an existing section). If
     copying an existing section, update the variable in the import statement
     (`{% capture t10 %}...`) by incrementing the number and modifying the
     imported filename to reflect the new work product.
   - Create a new import history table under `pub-histories/`. Again this can be
     done by copy / renamed / edit of an existing history table file. The
     filename needs to match the name used in `pubhist.html`. 

The first line of the publication history table always refers to the current
work-in-progress version of the work product and should link to the working
branch of the work product's TC repository on GitHub.

## How to run the website on your local computer

- Make sure to install [Jekyll](https://jekyllrb.com/) on your
  computer using the [instructions](https://jekyllrb.com/docs/)
  provided on their website.
- In the Terminal, run this command to check if Jekyll is
  installed. It is recommended to install v4.1.1 and above.
```
jekyll -v
```
- Clone the OpenC2 Website repo
  [https://github.com/OpenC2-org/openc2-org.github.io](https://github.com/OpenC2-org/openc2-org.github.io)
  to your computer.

```bash
cd openc2-org.github.io

jekyll serve
```
- Running ```jekyll serve``` creates a folder called ```_site```
  under the folder ```openc2-org.github.io```. Jekyll uses this
  folder content to serve the website locally. The folder
  ```_site``` should not be checked into the repository.

- Browse the website by going to this URL. Make sure to stop the
  server and run again each time a change is made to the
  ```_config.yml``` file.

```
http://127.0.0.1:4000/openc2-org.github.io/
```


## Contributing
Pull requests are welcome. To request changes, please open an
issue first to discuss what you would like to change.

