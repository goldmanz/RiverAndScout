# Notes

## Week 2 - html
- *not* a way to style (that's CSS--a presentation language)
- Keep structure separate from style
  - So that you know where to go to make fixes
  - *except* if you're working with teamset (?)...because of how it works
- Javascript is the third language...we're not covering
- Common html terms
  - Elements
    - paragraphs, links, headings, etc.
    - identified by <a> (would be the a here)
  - Tags
    - Used to create elements
    - <div> ... </div>
  - Attributes
    - give you more info about an element
    - ex: id (identifies), class (classifies), src (for images), href (urls)
    - attributes take ="" (eg <a href="www.getty.edu">)
- Browsers do have default styling --> diff browsers might display things differently
  - Differences might not always be clear to you, so check your work in different browsers

#### Structures of a webpage
- Boiler plate = basic structure  
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <!--metadata, like css-->
  </head>
  <body>
  </body>
  </html>
- IN atom, if you type html and hit tab it will auto populate these Tags
- Commenting in html -- <!--notes go in a tag like this --> and when it's closed
  - good for you making notes about certain choices, things you know you need to return to
- Title (in head) is also what displays in google search (and tab)

- Types of elements
  - block elements always on a new line
    - like paragraphs, headers, lists (ul or ol)
      - for list, open with <ul> (unordered list) or <ol> (ordered list) then each item takes <li> </li> (both ul and li require closing tags too)
  - inline are things that are ok in line with other things
    - like emphasis tags (<em> for ital, <strong> for bold, etc.)
      - although emphasis tags seem like formatting, it's a way of providing semantic info--and then you can set how it will present in your CSS
  - Empty Elements
    - not wrapped (ie not opened and closed)
    - like lines breaks <br> or horizontal rules <hr>
      - use these as a structural not design elements -- better to use CSS to change margins or images

#### Readability
  - tab your elements to make it readable. Any space outside of tags aren't read in the final page
    - can use tabs or spaces...but don't mix!
    - In atom you can set what a tab represents (exactly how many spaces)

  - links
    - tag: <a href=""> </a>
    - Types of links
      - Absolute -- most detailed way you can build a links. Typically for outside website
        - https://www.url.com/docs
      - Relative links -- point to another file in the same website from vantage of the same website. Only need path.
        - <a href="favorites.html"> </a>
        - To link within Atom, they need to be in same folder (unless you're adding the folder name in there) and it will link using the file named
        - can use this to link to other folders with a /[file name]
        - to go up a folder level, use ../[file name]
          - each level you go up gets a ../ (so two levels is ../../[file name])
        - These are a little risky bc you need to make sure you know the folder structure and where things are in that structure--and not move them
      - Root-Relative
        - rather than relative to page you're on it's relative to the page you're on. Start with a /, which represents the homepage
    - Naming conventions
      - no spaces in the file names or you can't link right! Use - or _.
      - Easier to use all lowercase for consistency
    - images
      - self closing tag. <img src=""/>
      - Inside the "", you can use a web link/url. Best practice not to link externally...can disappear and you're not hosting. But you can.
  - Semantic tags in HTML5
    - Used to organize information on the site in a standard way (list from HTML5). References the list when you need. And can signal things ot the webcrawler about the importance of various elements
    - Some useful Tags
      - <article></article>
      - <aside></aside> -- typically for a sidebar or content that's less important
      - <figure> <figcaption>[text]</figcaption> <img src=""/> </figure> -- separates element from the main body text and allows you to add a caption. If you want fig caption below the figure, move it below img src tag.
        - used a lot in art. Fig caption is tied to the image and is left aligned and slightly smaller. Can use css to format.
      - <header> </header>
      - <footer> </footer>
      - <main> </main> -- main part of your content. Mostly to signal to web crawler and for css
      - <nav> </nav> for navigation. often a list inside these Tags
      - <section> </section> - a way to group content on the page
      - <div></div>
        - basically a container tag with no symantic meaning (for screen readers) but can help in styling with CSS


#### CSS  
- Cascading Style Sheets
  - originally combined with HTML but is now separate. Styling/presentation (see CSS Zen Garden for examples of what it can do)
  - styles "cascade" down the html--so any style you apply to body will apply to everything inside body, everything you apply to <p> will apply to everything in <p>
  - styles at a lower level override style at a higher level
  - can be used for things like transition, complex grids, etc.
- how
  - use a .css file (Best) or in the head of an html doc head within the <style></style> tags. Style is good for small or page specific design Elements
  - Styles in external file are loosest, those in head will overwrite those in outside file, and those in a specific tag will overwrite everything
- Syntax
  - /*selector*/
  Body {
    /*property: value */
    color: #ff0000;
  }
    - above will apply to all body tags. Replace body with p, h2, etc to style those elements
    - Don't forget the ; at the end of each rule and the } at the end of each selector

    Fonts
    - Font-family -- do a font stack--go from fav to backup, specific to general
    - font-weight -- thickness, italic
    - text-decoration -- like underline or strike through

    Text spacing
    - line-height -- spacing between lines
    - letter-spacing -- spacing between letters
    - "em" = default measurement. So 1em is in relation to a default size of the letter "m". Things are scaled relative to each other

- Classes and ids
  - to call to id, use # (so #aLongTimeAgo).
    - ids should only be used once! If multiple instances, use class
  - to call to class, use . (so .dialogue)

  -"DRY" - don't repeat yourself. If you're applying same CSS to many items, maybe you need a class or to style something at a different levels

  - Checking your work
    - In browser, can use "inspect" (right click-->inspect) to see the code and the Styles
    - Styles are below
    - When things are greyed out in inspect in the styles they're not being used
    -can edit the style and see them live--but they're temporary. You can play around and learn waht looks good, and then you take it back to your CSS sheet.
    - Can also use it to spy on elements--see what other pages are doing, how they're designed

  -Display - inline or block
    - Can help with alignment of elements on page. So inline elements go onto the same line, block need their own lines.
    - Paragraphs tend to be block, lists are actually in-line elements
    -items have a kind of default, so if we want them to behave differently than the default, we use "display:"

  - moving things around
    - In developer tools, you see the "box model" -- shows us the content, the padding, the border, and the margin. It gives you the size of those elements. Margin default 16 px
    - To space out elements, you can do with padding or margin. Padding is inside border, so if you're using a border, the border will be farther out
    - margin is shared with the objs next to it. So if margin is 20 top and bottom for 2 items next to each other, there will still only be 20 px between
    - padding -- if you give one value, it adds to all sides; if 2 values, 1st goes top and bottom, 2nd goes left and right ; with 3, goes top, right/left, bottom; with 4, top, right, bottom, left
    - border shorthand -- give width then style then color after the border:
      - using a border is a good cheat sheet for debugging--gives you a better visualization of margin, where elements are, etc.
    - margin can also center content (esp non-text content)

  #### Flexbox!
  - it helps organize things in containers, you align them
  - see : https://css-tricks.com/snippets/css/a-guide-to-flexbox/




  GITHUB
  - Useful for version control!
  - What is Git? A distributed version control system. Everyone has full access to every version, and everyone can work on their own version (branch)
  - KEY TERMS
    - Repository = a project folder
    - Commit = a "snapshot of time." Give it a good message so you can understand what the changes were
    - Branches = multiple versions of the project. You can work along multiple lines, but wont go into main project until you merge 
