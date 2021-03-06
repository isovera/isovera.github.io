# Drupal Design Guide
This is a living document developed by [Isovera](https://www.isovera.com/) to help design agencies work better with developers in creating responsive websites with Drupal. 

The guide documents the best practices and pitfalls that we’ve experienced when collaborating with external design agencies on responsive websites. This guide is a work in progress and we are constantly refining our development process. Please [contact us](https://www.isovera.com/contact-us) with any feedback or questions.

## Preface

Front-end web development has entered an exciting and volatile phase. Responsive web design has moved from a novelty to a client expectation. Meanwhile, the agile development methodology has moved from its roots in product development and software applications to web design agencies. Along with this change, came new technologies and more efficient and adaptive workflows.


## TL;DR

1. Collaboration and feedback channels: Slack, Google Hangouts
1. Planning and scheduling: Google Calendar, Basecamp and GitHub Milestones
1. User stories: GitHub issues
1. Use real content and design for both common cases and edge cases
1. Never introduce features or unusual structures in Photoshop comps. Provide lo-fi wireframes and sketches.
1. Design to accommodate older displays, visual disabilities and keyboard navigation
1. Provide assets to accomodate high resolution displays: vector and high resolution image assets
1. Obtain aspect ratios, composition and production capability from client
1. Fluid Grid system, percentage-based layout, rem units
1. Start with small (mobile) breakpoint sizes to establish priority and source order
1. Help our developers build a component-based design system
1. Plan to brainstorm and sketch interactive behaviors and animations with developer. The design is how it works.
1. If a design takes ten seconds to load, nobody will stay to see it. Consult with our developers to strike a balance between aesthetics and performance.

## Content-Driven Design

Design prototypes need placeholder text and graphics. In this section, we recommend spending the additional time to engage the client to obtain real client content for the production website. This makes us more dependent on a busy or possibly unmotivated client, but it is critical to the implementation and long-term success of the project.

### Use real, representative content

It’s tempting to use Bacon ipsum for placeholder text, and in certain circumstances, there’s nothing wrong with "ham hock bresaola". But the client content is the single most important thing about the site. All too often designers bake assumptions into the design as simple as the length, or even presence, of a line of text.

Whether the final copy already exists or not, you will need real content to flesh out the real-world display of content displays and user interfaces.

#### Content varies

Paragraph and line length are variable but have patterns. Identify the edge cases and include those in your decision making process. Using several pieces of real content (rather than a single, repeated item) can help expose a design’s unrealistically rigid assumptions about character length.

In the following screenshot from the front page of the Huffington Post,  "Battery" is unintentionally hidden.

![image alt text](image_0.jpg)

The space allotted for the title mirrors the space for the image, which preserves the alignment between the two rows. Unfortunately, this hard-coded design decision hides the end of the headline.

Try to think in terms of structured content and variable, fluid heights. Sometimes, selectively display different fields depending on viewport size, e.g. long title versus short title.

[Truncation is not a content strategy](https://twitter.com/karenmcgrane/status/520576694210801665).

Get the aspect ratios and image sizes of the client’s available and potential image library.

Interactions between bitmap images and overlapping text can be especially delicate. Text should almost never be rendered within an image, but overlaid as a separate element. Expect the font to be resized by the user.

[Example: text overlaid on an image at various screen sizes. Change font size?]

#### Identify the client’s capabilities

Clients have a limited amount of time and resources. Do they have a dedicated content creator? Will they have time allocated to work on the content of that special feature? Do they have access to Photoshop and are they comfortable working with HTML? Don’t assume they will use the tools that  you have access to as a designer. Limit content to what the client can provide and maintain.

### Resilient, not brittle

People don’t read, they scan the web. Design for sub-optimal attention spans. The site visitor could be cognitively impaired, distracted or in a crisis.

## Universal Design

### Accessibility is for everyone

Curb cuts are good for baby strollers, lever door handles are useful when your hands are full or there’s an emergency. Every user benefits from websites that are more accessible and easier to use. Seemingly innocuous design decisions can make a site impossible to use for some people. Read up on [WCAG 2.0](http://www.w3.org/TR/WCAG20/). Accessibility is also a human right.

[An Alphabet of Accessibility Issues](https://the-pastry-box-project.net/anne-gibson/2014-July-31) points out some of the less obvious challenges users may face when navigating websites.

* good contrast
* distinctive element appearance (buttons look like buttons)
* don't just use color to differentiate between elements
* Pay special attention to links.  Represent links consistently so the user can predict what is a link and what is not.  Prefer usability to perfect aesthetics
* spacing
* line lengths
* design shouldn't break if user resizes text
* don't include text as a part of images (alt text) (non-responsive images)
* visual backup for audio cues
* keyboard-only navigation (menus, forms)

## Mobile-First Design

### Start small

Don’t start with the best case scenario. Design for small devices first to prioritize content and user actions. Design for low bandwidth, small screens and enhance.

Designing for small, mobile devices also streamlines the development of the HTML source code order. Once the HTML source order is established, the site is amenable to mobile device support and accessibility. Large screen size layouts can be built on top of this base. It can be more difficult and time-consuming to extract the source order from a large screen size layout.

Don’t assume optimal bandwidth.

Art direction for responsive design: landscape/portrait, small/large:

[http://usecases.responsiveimages.org/#art-direction](http://usecases.responsiveimages.org/#art-direction)

Performance is critical. Consider image file sizes and count. Too many widgets or too large images will degrade the page load.

[How we make RWD sites load fast as heck](http://www.filamentgroup.com/lab/performance-rwd.html)

### On Design Artifacts

Models, scaffolding and stencils.

[Responsive deliverables](http://daverupert.com/2013/04/responsive-deliverables/)

Ultimately, the working website is the only deliverable.

### Formats

If you’re working with photoshop, provide the original PSD files with layers, not static image exports. Don’t waste precious developer time decomposing and reverse engineering basic things like relative font sizes and color values. Make sure that font family, sizes and weights are identified or identifiable

Always provide high resolution images and vector art when available.

Use progressive JPEGs or interlaced PNG file formats. Users perceive them as faster and they preserve responsive layouts while the image is loaded.

[example of loading responsive layout]

#### Web fonts

Users can and will change the default font size.

Reference other sites that implement similar techniques.

Complex features like dynamic forms, calendars or search results filtering may require close coordination with the developer. Collaborating with working, browser-testable prototypes is best.

Time-sensitive features especially can expose unexpected design challenges: expiration, time zones, daylight savings time, archiving, etc.

## Fluid Design

### Pixel perfect is dead

Think relative units and not absolute pixels. Unfortunately, tools like Photoshop base their conceptual model on fixed widths. This becomes an unwieldy liability as mockups multiply exponentially for a range of pages and viewport sizes.

Use percentages or root em (rem) units instead of pixels. Root em units scale in proportion to the base font size. Pixel-based designs are fixed and brittle. Relative units scale appropriately for the device size and browser settings.

### Use a fluid grid

Typography has an established history of grid-based layouts. In the mid-2000’s, the 960 pixel grid system became a popular tool for website layouts. Instead of designing in terms of pixels, the designer could evenly subdivide the interior 960 pixels of the screen into a number of columns.

For example, each column in an 8 column layout is 120 pixels wide. Then, instead of using pixels, a sidebar can be described as occupying the first 2 columns of the grid and the main content area the last 6.

This was a tidy solution until the explosion of the mobile devices and retina screens. The 960 pixel grid system quickly showed its limitations. Ethan Marcotte subsequently [popularized fluid grid systems](http://alistapart.com/article/fluidgrids), which base their widths on percentages instead of pixels. Fluid grids, along with flexible images and CSS media queries are the basis for [responsive web design](http://www.abookapart.com/products/responsive-web-design).

##### Acknowledge remainders in grids

For some components, the total count of items in a grid will not conform to a predetermined grid count. The items in the bottom row often will not complete the allotted column spaces. For example, a search result may return five items in four-column grid. In this case, there is no reason to expect a rounded result set. Moreover, this scenario is exacerbated when using responsive grids. When a three-column grid switches to two-columns, unless the total count is divisible by six, there will be a straggler. These gaps are not inherently a problem, but they open up seams in the design that are typically disregarded in static comps. Instead of creating the illusion of perfect content with no gaps, they should be presented. With this shared knowledge, they can even be used opportunistically to present supplementary information or decoration.

### Breakpoints

The web is fluid. Web browsers are a continuum of shapes, sizes, resolutions and capabilities. Instead of focusing exclusively on one, two or three breakpoints, consider appearance at interstitial viewport sizes. Remember that users often don’t maximize their browser windows or may be on a mobile device. [Think about device classes (smartphones) instead of specific devices (iPhone 6+).](http://alistapart.com/article/designing-for-breakpoints)

[Bootstrap](http://getbootstrap.com/), [Foundation](http://foundation.zurb.com/), and other frameworks can help. They come with well-tested, responsive CSS styles that work as a base for building responsive websites. 

## Style Guide-Driven Design

### Style guides

A style guide details how individual site elements and components should look, rather than an entire page.  [Pattern Lab](http://demo.patternlab.io/) is a nice example of an interactive style guide and there are lots of others listed on [Website Style Guide Resources](http://styleguides.io/examples.html).

Style guides have two main parts--base elements and components. Base elements [basic elements, base styles, foundational elements] are the building blocks of a site. These include things like content headers, lists, links, color schemes, form fields, and other simple elements. Components [patterns, feature blocks] are larger sets of elements reused throughout the site (see Glossary). Some examples are pagers, tabs, AJAX throbbers, search results, and system messages. User interactions like hovers, taps, clicks, and scrolling can also be included, as well as any animations used ([Adding items](http://codepen.io/valhead/full/adnKt), [jQuery Approach](http://srobbin.com/jquery-plugins/approach/)). 

[Boilerplate guides](https://zurb.com/expo/lessons/creating-a-killer-style-guide) and [generators](https://github.com/davidhund/styleguide-generators) can speed up both the creation and maintenance processes.

## Agile Workflows

### Mockups

* Low fidelity is good
* High fidelity is expensive

### Iterate

How does a design work? What is the user experience? There is a growing need to flesh out implicit assumptions about how a user interface will work in the real world.

Explore breakpoints.

Sketch, screen share and explain your ideas and assumptions. Or meet in person.

As [Ben Callan of Sparkbox has emphasized](http://www.uie.com/brainsparks/2014/11/07/ben-callahan-dissecting-design-live/), humility and empathy are key virtues for a successful responsive web design team. No one person on the project will be able to dictate the operational design of the site.

[Why Designers and Web Developers Must Work Together](http://designmodo.com/designers-developers-work/) emphasizes the important of collaboration between those two roles in particular.

## Glossary

*Component* - A repeatable pattern composed of text, form fields, images, or other elements. We use this term in place of *module*, which can be confused with the Drupal programming term.

## Further reading

### Online

* [This is Responsive](http://bradfrost.github.io/this-is-responsive/) by Brad Frost
* [Website Style Guide Resources](http://styleguides.io) by Anna Debenham and Brad Frost
* [Responsive Web Design podcast](http://responsivewebdesign.com/podcast/) featuring Ethan Marcotte and Karen McGrane
* [Style Tiles](http://styletil.es) by Samantha Warren
* [Content-out Layout: the Resources](http://alistapart.com/blog/post/content-out-layout-the-resources/) by Nathan Ford
* [About HTML semantics and front-end architecture](http://alistapart.com/blog/post/content-out-layout-the-resources/) by Nicolas Gallagher
* [Designing for the Web](http://www.designingfortheweb.co.uk/) by Mark Boulton

### Books

* [Responsive Web Design](http://abookapart.com/products/responsive-web-design) by Ethan Marcotte
* [The Responsive Web](http://www.manning.com/carver/) by Matthew Carver
* [Mobile First](http://abookapart.com/products/mobile-first) by Luke Wroblewski
* [Responsible Responsive Design](http://abookapart.com/products/responsible-responsive-design) by Scott Jehl
