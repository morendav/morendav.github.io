

# Migration to Introduction theme
Date: May 2023

## Open tasks


[ ] - P0 - test all pages
[ ] - P0 - Table alignment: html for the tables should middle (vertical) align
[ ] - P2 - search function at menu / blog (search for any term)
[ ] - P1 - blog sort by tags / filter by tags
[ ] - P2 - table of contents at the top of the page, with links to headers (h1, h2, ...)
[ ] - P2 - theme does not resolve emojis
    *  for now a workaround:  manually insert in place
[ ] - P1 - markdown style update: H1 and H2 are very similar, it makes the break up of a post more difficult to spot in a glance at the page. H1 and H2 should be more differentiated




## Completed tasks
[x] - P0 - import images in multimedia projects folder
    * from ipad
[x] - P0 - import images into photography projects folder
    * from google photos, if edited
[x] - P0 - change footer, no links and make it simple
[x] - P0 - instagram connect with me link on home page
[x] - P0 - typescript needs install in intro, all the equations are rip
    Solution 1 - https://github.com/victoriadrake/hugo-theme-introduction/issues/321
        * theme/intro/layouts/_defaults
            * edit 'baseof.html' --> header to include a parial
                    {{ if or .Params.math .Site.Params.math }}{{ partial "head/katex.html" . }}{{ end }}
            * move partial katex to 
                    /Users/davidmoreno/Blogging/new_test_intro_theme/quickstart/themes/introduction/layouts/partials/head/katex.html
    Solution 2 - figure out how to put partials in intro
        * update: May 6 2023 - added katex through solution 1
[x] - P0 - fix dark theme tables, the font color is the same color as the fill of each cell
    * markdown for dark theme is stored in .../introduction/assets/sass/dark-style.sass
        * elements are called from .../dark-variables.sass, though this was not modified
    * included markdown, table in the 'dark-style.sass' file by appending this block
    
    ```
    .markdown
        table
            margin: 2em 0 2em 0
            width: 100%
            border: 1px solid #e5e5e5
            border-collapse: collapse
        td, th
            padding: .25rem .5rem
            border: 1px solid #e5e5e5
            text-align: center
            background-color: #0a0a0a
        tbody tr:nth-child(odd) td,
        tbody tr:nth-child(odd) th
            background-color: darken(#1e1e1e, 0%)
        tbody tr:nth-child(even) td,
        tbody tr:nth-child(even) th
            background-color: #1e1e1e
    ```




# migrating to intro theme

## starting with intro
1. create /en/ folder in content
   * then you can follow instructions for making blog, projects



## migrating posts
* links within posts will not carry forward
* links to images will still work, no-op
    update as follows:
    ```
        href="{{< relref "posts/how_this_all_started.md#build_walkthrough" >}}
    ```
    update to 
    ```
        href="{{< relref "blog/how_this_all_started.md#build_walkthrough" >}}
    ```




# Intoduction theme modificaitons

things I modified from the introduction theme 

* theme/intro/layouts/_defaults
    * edit 'baseof.html' --> header to include a parial
            {{ if or .Params.math .Site.Params.math }}{{ partial "head/katex.html" . }}{{ end }}
    * move partial katex to 
            /Users/davidmoreno/Blogging/new_test_intro_theme/quickstart/themes/introduction/layouts/partials/head/katex.html


 * included markdown, table in the 'dark-style.sass' file by appending this block
    ```
    .markdown
        table
            margin: 2em 0 2em 0
            width: 100%
            border: 1px solid #e5e5e5
            border-collapse: collapse
        td, th
            padding: .25rem .5rem
            border: 1px solid #e5e5e5
            text-align: center
            background-color: #0a0a0a
        tbody tr:nth-child(odd) td,
        tbody tr:nth-child(odd) th
            background-color: darken(#1e1e1e, 0%)
        tbody tr:nth-child(even) td,
        tbody tr:nth-child(even) th
            background-color: #1e1e1e
    ```

* updated the footer to something more simple
    * /Users/davidmoreno/Blogging/morendav.github.io/themes/introduction/i18n/en.toml