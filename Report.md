# Web Development Module Coursework 1

## Introduction

The aim of this project was to develop a four-page informational website exploring the history, present, and
future of human space exploration. The focus was on creating a clear, accessible, and visually consistent
user experience while applying modern web development practices such as semantic HTML, modular CSS,
responsive design, and accessibility considerations. Throughout the development process, I iteratively
refined the layout, styling, and structure of each page, addressing challenges as they emerged and
improving my understanding of CSS specificity, layout techniques, and maintainable code organisation.

## Website Purpose, Target Audience and Design Choices

The purpose of the website is to inform users about the history of space travel, as well as present and
future human space activities, through a clear, accessible, and visually engaging interface. The site is aimed
at a general audience with an interest in space exploration, including students, casual learners, and
individuals seeking an overview of the major milestones and upcoming missions.

The design prioritises readability, accessibility, and consistency across pages. The global navigation bar and
footer provide a consistent structure, while each page uses a <main> container to ensure predictable layout
behaviour. The colour scheme uses dark blue for headings and accents, reflecting the theme of space and
providing strong contrast against a white background. Typography is kept simple and readable using Arial,
chosen for clarity and accessibility. Finally, accessibility features such as alt text for images and ARIA labels
are used throughout to improve accessibility for people using screen readers.

The web pages follow a minimalistic yet eye-catching design. The history, future, and contact pages use
centred content for a clean, streamlined design, while the home page uses a simple two-column layout to
introduce the site’s purpose alongside a relevant image.

## Key Technologies and Design Decisions

HTML5 semantic elements (<nav>, <main>, <footer>, <div >, etc.) were used to create a clear document
structure and improve accessibility. The main layout of each page is wrapped in the <main> tag, while <nav>
and <footer> are used globally to provide consistent navigation and layout. CSS was used extensively for
layout, including flexbox for the homepage’s two-column layout and CSS grid for the history page’s photo
gallery. The future page uses a more complex layout based on absolute positioning and pseudo-elements to
create a vertical timeline with alternating event blocks.

CSS transitions were used for interactive elements such as hover effects on images. The circular images on
the timeline on the future page were created by setting the width and height to equal, fixed dimensions
(300px) combined with ‘object-fit:cover’ and ‘border-radius: 50%’ to create the rounded corners.
‘overflow:hidden’ was used for overflow handling, for example to prevent zoomed images from escaping
their containers. Responsive design considerations included percentage-based widths, auto-scaling images,
and a media query to adapt the timeline layout for smaller screens.

As well as an individual stylesheet for each page, a global stylesheet was used to centralise shared styles for
the navigation bar and footer, ensuring consistency and removing the need for duplication. Page-specific
stylesheets were used for individual layouts to keep the code maintainable and organised.

## Challenges Faced and How They Were Resolved

One of the main challenges was creating layouts that remained consistent and responsive across different
pages. Early attempts at the homepage layout used a <table>, which caused spacing issues and did not
adapt well to different screen sizes. This was resolved by switching to a CSS-based two-column layout using
flexbox, which provided much greater control. This challenge taught me the importance of separating
structure and styling. I decided to use one HTML file and one CSS file for each page, to keep structure and
styling for each page separate, as well as keeping the styling separate between pages.

The timeline on the future page presented a more complex challenge. Positioning the central line,
alternating containers, and circular markers required careful use of absolute positioning and pseudo-
elements. Ensuring that the layout remained readable on smaller screens required a dedicated media query
to collapse the alternative structure into a single-column layout.

At first, I didn’t have many issues with the timeline, as I had used a template from W3Schools which proved
fairly easy to adapt to my needs. However, the introduction of the navigation bar created an unexpected
conflict. I noticed that the navigation bar on the future page took up less space vertically compared to the
other pages. I decided to go through each CSS file, looking for any scoping issues. For example, I changed
the scope of a global ‘img’ selector on the history page to ‘.content img’. The ‘.container’ class was also used
both in the future page timeline and the history page gallery, therefore, I renamed the gallery container to
‘.history-grid’ to prevent the styles from interfering with each other. Finally, I realised that I had given the
individual stylesheets higher priority than the global stylesheet, therefore, I reordered the <link> elements
so that global.css loaded first on each page. However, none of these attempts resolved the issue with the
navigation bar.

After many failed attempts to resolve the issue, I realised that I had initially used an asterisk to select every
element on the future page, and apply ‘box-sizing: border-box;’ to them. However, this unintentionally also
applied to the navigation bar, causing it to take up less space vertically. Although I had kept the styling for
the navigation bar separate to the styling for each individual page, using a ‘global.css’ file, this wasn’t
enough to prevent conflicts between the stylesheets. At first, I tried to resolve this issue by simply removing
the part of code applying ‘box-sizing: border-box’ to the elements, however, this significantly affected the
layout of the timeline, causing the vertical line to no longer be centred and to go through some of the
boxes. I realised that the issue could not be resolved by just removing this code. I had to keep it in but
change the scope. I finally realised that I had to apply ‘box-sizing: border-box’ to just ‘.timeline’, ‘.timeline *’,
‘.timeline *::before’, ‘.timeline *::after’. That centred the vertical line as intended, however, the circles on
the timeline were still slightly off-centre.

These challenges collectively improved my understanding of CSS specificity, layout techniques, responsive
design, and the importance of maintaining clear, modular stylesheets.

## Conclusion

Developing this website allowed me to apply a wide range of web development techniques while gaining
practical experience in structuring, styling, and debugging multi-page layouts. Through iterative refinement,
I learned how to manage CSS specificity, maintain consistent design across pages, and resolve conflicts
between global and page-specific styles. The project strengthened my understanding of responsive design,
semantic HTML, and accessibility best practices. Overall, the development process improved both my
technical skills and my ability to design clear, maintainable, and user-friendly web interfaces.

## Development Summary

The project began with building the homepage structure, including a responsive hero image. An early attempt to create a two‑column layout using a <table> caused spacing and responsiveness issues, so it was replaced with a flexbox‑based layout, reinforcing the importance of separating structure from styling.

The history page was developed next by creating reusable event-card components containing headings, text, and images. Hover effects were added later using border transitions and box shadows. A photo gallery was then assembled and eventually converted into a 4‑column CSS grid layout with captions and accessibility attributes.

Work on the future page started by creating a sequence of event sections, which were later transformed into a full vertical timeline. This involved alternating left/right containers, a central vertical line, circular images, and hover zoom effects. The layout required careful use of absolute positioning, pseudo‑elements, and responsive adjustments via media queries.

The contact page was built with appropriate form input types, a styled submit button, and an embedded Google Map. The content was centred using a wrapper for consistent layout.

A global navigation bar and footer were added to all pages, initially using a dedicated stylesheet that was later renamed to global.css to centralise shared styling. This introduced a layout bug on the future page where the navbar appeared shorter than on other pages. After testing multiple hypotheses — including selector scoping, renaming classes, and reordering stylesheets — the issue was traced to a universal selector in future.css that applied box-sizing: border-box to every element on the page. Removing it broke the timeline layout, so the rule was instead scoped specifically to the timeline elements, resolving the conflict without affecting the navbar.

Final refinements included improving spacing, overflow handling, paragraph styling, and ensuring consistent layout across all pages.
