# About this website

This website was created using [Jekyll](https://jekyllrb.com/)
and hosted using GitHub Pages. This page documents the
implementation and maintenance of the website.

The source can be found at
[https://github.com/OpenC2-org/openc2-org.github.io](https://github.com/OpenC2-org/openc2-org.github.io).

Additions/corrections/suggestions are welcome.

Contents of this README.md file:
 - [Website Structure](#website-structure)
 - [Maintenance Procedures](#maintaining-the-website)
   - [Home page
     carousel](#how-to-addremove-slides-in-the-carousel-on-the-homepage)
   - [In The News
     timeline](#how-to-change-the-timeline-in-openc2-in-the-news-page)
   - [FAQ
     Page](#how-to-update-the-frequently-asked-questions-faq-page)
 - [Running the website
   locally](#how-to-run-the-website-on-your-local-computer)
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
-- README.md                         # Documentation on how to use/contribute to this website
-- specifications.html               # Specifications

```

## Maintaining the Website

### How to add/remove slides in the carousel on the homepage?
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

### How to change the timeline in "OpenC2 in the news" page?
```news.html``` is the page where a timeline is present.

To add or remove cards in the timeline, Open ```news.html``` and
find the date you would like to insert a new card and copy paste
this HTML. Please make sure to change the Date and Link as
necessary.

```
<div class="timecard" data-aos="fade-up">
    <div class="content">
        <h6>March 06, 2020</h6>.  <!-- This section has the date of the entry -->
            <p> <!-- This section has the content of the entry -->
               <a rel="noopener noreferrer" target="_blank" href="https://codesync.global/media/making-iot-safer-with-beam-otp-cbf20/">
              Making IoT safer with BEAM OTP
              </a>
            </p>
     </div>
</div>
```

### How to update the Frequently Asked Questions (FAQ) page?
The `_faqs` folder contains the collection of FAQs, stored one
per file in Markdown format. The file structure is simple:

```
---
question: <question text>
---
<response text>
```
The FAQ page is build from this collection by the `faqs.html`
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

Shorthand conventions in this filename scheme include `-W-I-` for
"What Is", and `-RT-` for "relate to" questions.

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
3) From purposes of FAQ sequencing, the "explainer" portion of
   the filename is irrelevant.

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

