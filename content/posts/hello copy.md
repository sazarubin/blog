---
title: "Hello"
date: 2023-09-10T12:47:38+06:00
draft: false
---

Hi!

This is a great option for people that don’t want to bother with self-hosting their own commenting engine; however, it has some drawbacks. Because Disqus provides this service for free, they recoup any financial loss by injecting third-party ad trackers onto your website. These trackers help to collect and sell information about your users, while also negatively affecting your site’s speed.

Even still, Disqus may be the best solution depending on your situation (we use it on this demo site). The above paragraph is only meant to highlight its trade-offs and not meant to discourage its use entirely.

Remark42 is a lightweight, open source commenting engine that doesn’t spy on your users. The downside is that you must host it yourself. Checkout the Remark42 documentation to get started. I also found this blog post helpful when setting it up on my site.

Once everything is set up, you can activate it in the Poison theme by including the following in the [params] section of your config.toml file.

[params]
    remark42 = true
    remark42_host = "https://yourhost.com"
    remark42_site_id = "your_site_id"

Series

Sensibly link and display content in “series” (i.e. Tutorial One, Tutorial Two, etc.).

This is done with a custom taxonomy. Just add series to the frontmatter on any content you want to group together.

---
title: "Example to demonstrate how to use series"
date: 2022-10-04
draft: false
series: "How to use poison"
tags: ["Hugo"]
---

KaTeX

Make your mathematical notations pop.

For notations that should appear on their own line, use the block quotes $$ ... $$

5×5=25
5×5=25

For notations that should appear on the same line, use the inline quotes $ ... $
Tabs

Some content is just better viewed in tabs. There’s a shortcode for that.

This is markdown content.

Here’s the code for the tabs above…

{{< tabs tabTotal="2" >}}

{{% tab tabName="First Tab" %}}
This is markdown content.
{{% /tab %}}

{{< tab tabName="Second Tab" >}}
{{< highlight text >}}
This is a code block.
{{< /highlight >}}
{{< /tab >}}

{{< /tabs >}}

Mermaid diagrams

There’s a shortcode for embedding Mermaid diagrams.
JohnBobAliceJohnBobAliceloop[Healthcheck]Rational thoughts prevail!Hello John, how are you?Fight against hypochondriaGreat!How about you?Jolly good!

Here’s the code for the diagram above:

{{< mermaid >}}
sequenceDiagram
participant Alice
participant Bob
Alice->>John: Hello John, how are you?
loop Healthcheck
    John->>John: Fight against hypochondria
end
Note right of John: Rational thoughts <br>prevail!
John-->>Alice: Great!
John->>Bob: How about you?
Bob-->>John: Jolly good!
{{< /mermaid >}}

PlantUML diagrams

There’s a shortcode for embedding PlantUML diagrams.

Here’s the code for the diagram above:

<span id="plantuml-foo" style="display:none">
a -&gt; b
b -&gt; c
</span>
<img class="plantuml" id="plantuml-foo">

Installation

First, clone this repository into your themes directory:

git clone https://github.com/lukeorth/poison.git themes/poison --depth=1

Next, specify poison as the default theme in your config.toml file by adding the following line:

theme = "poison"

Lastly, if there are any future updates to this repository that you wish to include in your local copy, these can be retrieved by running:

cd themes/poison

git pull

For more information on how to get started with Hugo and themes, read the official quick start guide.
How to Configure

After successfully installing Poison, the last step is to configure it.
The Sidebar Menu

Any items you want displayed in your sidebar menu must satisfy two requirements. They must:

    Have a corresponding markdown file in your /content/ directory.
    Be declared in your config.toml file (example below).

There are two types of menu items:

    Single Page – The About menu item (to the left) is a good example of this. It displays a direct link to an individual page.
    List – The Posts menu item is a good example of this. It displays a directory and dynamically lists the contents (i.e. pages) contained by date. List items have two optional configurations: a subheading (like the Recent subheading that appears on the menu to the left), and a maximum number of items to display.

The sidebar menu items are configured with a dictionary value in your config.toml file. I’ve included an example below. Additionally, there is a placeholder for this in the config.toml file shown in the next section.

Remember: You must have a markdown file present at the path specified for the menu item to be displayed.

menu = [
        # Dict keys:
            # Name:         The name to display on the menu.
            # URL:          The directory relative to the content directory.
            # HasChildren:  If the directory's files should be listed.  Default is true.
            # Limit:        If the files should be listed, how many should be shown.

        # SINGLE PAGE
        # Note that you must put your markdown file 
        # inside of a directory with the same name.

        # Example:
        # ... /content/about/about.md
        {Name = "About", URL = "/about/", HasChildren = false},
        
        # LIST
        # This example has a subheading of "Recent"
        # and will display up to 5 items.

        # Example:
        # ... /content/posts/introducing-poison.md
        {Name = "Posts", URL = "/posts/", Pre = "Recent", HasChildren = true, Limit = 5},

        # Example of a list without a subheading or limit.
        {Name = "Projects", URL = "/projects/"},
    ]

Example Config

I recommend starting by copying/pasting the following code into your config.toml file. Once you see how it looks, play with the settings as needed.

NOTE: To display an image in your sidebar, you’ll need to uncomment the brand_image path below and have it point to an image file in your project. The path is relative to the static directory. If you don’t have an image, just leave this line commented out.

baseURL = "/"
languageCode = "en-us"
theme = "poison"
paginate = 10
pluralizelisttitles = false   # removes the automatically appended "s" on sidebar entries

# NOTE: If using Disqus as commenting engine, uncomment and configure this line
# disqusShortname = "yourDisqusShortname"

[params]
    brand = "Poison"                      # name of your site - appears in the sidebar
    # brand_image = "/images/test.jpg"    # path to the image shown in the sidebar
    description = "Update this description..." # Used as default meta description if not specified in front matter
    dark_mode = true                      # optional - defaults to false
    # favicon = "favicon.png"             # path to favicon (defaults to favicon.png)

    # MENU PLACEHOLDER
    # Menu dict keys:
        # Name:         The name to display on the menu.
        # URL:          The directory relative to the content directory.
        # HasChildren:  If the directory's files should be listed.  Default is true.
        # Limit:        If the files should be listed, how many should be shown.
    menu = [
        {Name = "About", URL = "/about/", HasChildren = false},
        {Name = "Posts", URL = "/posts/", Pre = "Recent", HasChildren = true, Limit = 5},
    ]

    # Links to your socials.  Comment or delete any you don't need/use. 
    discord_url = "https://discord.com"
    email_url = "mailto://user@domain"
    facebook_url = "https://facebook.com"
    flickr_url = "https://flickr.com"
    github_url = "https://github.com"
    gitlab_url = "https://gitlab.com"
    instagram_url = "https://instagram.com"
    linkedin_url = "https://linkedin.com"
    mastodon_url = "https://mastodon.social"
    matrix_url = "https://matrix.org"
    telegram_url = "https://telegram.org"
    tryhackme_url = "https://tryhackme.com"
    twitter_url = "https://twitter.com"
    xmpp_url = "https://xmpp.org"
    youtube_url = "https://youtube.com"

    # NOTE: If you don't want to use RSS, comment or delete the following lines
    # Adds an RSS icon to the end of the socials which links to {{ .Site.BaseURL }}/index.xml
    rss_icon = true
    # Which section the RSS icon links to, defaults to all content. See https://gohugo.io/templates/rss/#section-rss
    rss_section = "posts"

    # Hex colors for your sidebar.
    moon_sun_background_color = "#515151"   # default is #515151
    moon_sun_color = "#FFF"                 # default is #FFF
    sidebar_a_color = "#FFF"                # default is #FFF
    sidebar_bg_color = "#202020"            # default is #202020
    sidebar_h1_color = "#FFF"               # default is #FFF
    sidebar_img_border_color = "#515151"    # default is #515151
    sidebar_p_color = "#909090"             # default is #909090
    sidebar_socials_color = "#FFF"          # default is #FFF

    # Hex colors for your content in light mode.
    code_color = "#000"                     # default is #000
    code_background_color = "#E5E5E5"       # default is #E5E5E5
    code_block_color = "#FFF"               # default is #FFF
    code_block_background_color = "#272822" # default is #272822
    content_bg_color = "#FAF9F6"            # default is #FAF9F6
    date_color = "#515151"                  # default is #515151
    link_color = "#268BD2"                  # default is #268BD2
    list_color = "#5A5A5A"                  # default is #5A5A5A
    post_title_color = "#303030"            # default is #303030
    table_border_color = "#E5E5E5"          # default is #E5E5E5
    table_stripe_color = "#F9F9F9"          # default is #F9F9F9
    text_color = "#222"                     # default is #222

    # Hex colors for your content in dark mode
    code_color_dark = "#FFF"                        # default is #FFF
    code_background_color_dark = "#515151"          # default is #515151
    code_block_color_dark = "#FFF"                  # default is #FFF
    code_block_background_color_dark = "#272822"    # default is #272822
    content_bg_color_dark = "#121212"               # default is #121212
    date_color_dark = "#9A9A9A"                     # default is #9A9A9A
    link_color_dark = "#268BD2"                     # default is #268BD2
    list_color_dark = "#9D9D9D"                     # default is #9D9D9D
    post_title_color_dark = "#DBE2E9"               # default is #DBE2E9
    table_border_color_dark = "#515151"             # default is #515151
    table_stripe_color_dark = "#202020"             # default is #202020
    text_color_dark = "#EEE"                        # default is #EEE

    # NOTE: If using Remark42 as commenting engine, uncomment and configure these lines
    # remark42 = true
    # remark42_host = "https://yourhost.com"
    # remark42_site_id = "your_site_id"
    
    # NOTE: The following three params are optional and are used to create meta tags + enhance SEO.
    # og_image = ""                       # path to social icon - front matter: image takes precedent, then og_image, then brand_url
                                          # this is also used in the schema output as well. Image is resized to max 1200x630
                                          # For this to work though og_image and brand_url must be a path inside the assets directory
                                          # e.g. /assets/images/site/og-image.png becomes images/site/og-image.png
    # publisher_icon = ""                 # path to publisher icon - defaults to favicon, used in schema

[taxonomies]
    series = 'series'
    tags = 'tags'

Custom CSS

You can override any setting in Poison’s static CSS files by adding your own /assets/css/custom.css file. For example, if you want to override the title font and font size, you could add this:

.sidebar-about h1 {
  font-size: 1.4em;
  font-family: "Monaco", monospace;
}

Suggestions / Contributions

Please feel free to add suggestions for new features by opening a new issue in GitHub. If you like the theme, let us know in the comments below!