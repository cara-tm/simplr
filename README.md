# Simplr
Simplr template: a Textpattern CMS theme.

![Simplr Textpattern Theme](https://raw.githubusercontent.com/cara-tm/simplr/master/screenshots/simplr-mac-book-air.png "Simplr")

Features:

* a simple, responsive but strong and robust model with a pretty good browsers support: Internet Explorer 6 minimum;
* HTML5 markup (with a inline backward support shim);
* no external dependencies, no huge CSS framwork nor js libraries;
* hero image with a progressive loading (same visual effect as the one in use into the "Medium" website) in order to not blocking the construction of the "Above the Fold" part;
* full support for ltr languages;
* bluring image loading effects (aka Medium website);
* build-in sitemap, build-in JSON-LDs, build-in "Facebook Instant Article";
* support for "smd_thumbnail" plugin included;
* support for "pat_speeder" plugin included;
* good speed score based on the Google "test my website" and the Pingdom online tools.


The package is provided with this file structure:

    dist/
     - fonts/
     - Mobile_Detect.php
	 - white-loader-min.gif
     - simplr/
       - forms/
       - pages/
       - styles/
       - manifest.json
 
The `fonts` directory need to be uploaded into your root server.

The `Mobile_detect.php` file need to be uploaded into your  `/textpattern` folder.

The `white-loader-min.gif` file is to be stored into an `img` directory.

Finally, upload the `simplr` directory and all its content into your `/themes` folder available in the root of your server.

Access to your Textpattern administration interface and activate the `Simplr` theme from the Themes panel (see official documentation for further informations).

You will need to create some sections from the Sections panel:

* `default` associated to the `default` page and the `default` styles;
* `blog` associated to the `archive` page and the `default` styles;
* `contact` associated to the `static_pages` page and the `default` styles;
* `about` associated to the `static_pages` and the `default` styles;
* `search` associated to the `static_pages` and the `default` styles;
* `sitemap` associated to the `sitemap_xml` page and the `blank` styles;
* `fb-instant-articles` associated to the `fb-instant-articles` page and the `blank` styles;
* `sitemap-rss` associated to the `sitemap_rss` page and the `blank` styles.

From the "Override form" option into the "Write" panel, you have some visual choices for your image display:

* `default`: the default with a Lightbox to show individual images into a gallery;
* `default_black_white`: change your images into B&W ones (only visible from modern browsers);
* `default_saturated`: images gallery displaied with a little bit of colors saturation (only visible from modern browsers);
* `default_no_lightbox`: images gallery but without a "Lightbox";
* `default_no_lightbox_black_white`: B&W images gallery but without a "Lightbox";
* `default_no_lightbox_saturated`: images gallery displaied with a little bit of colors saturation but without a "Lightbox".

The Simplr theme has been built to be used “as this: just install it!” without the need of any plugins but you can gaim some advantages to install the following:

- `smd_thumbnail` to generate adapted copies of your images to different screen sizes;
- `com_connect` in order to generate a contact form;
- `pat_speeder` to accelerate the pages display, up to 10%.

After installation of these three plugins, check the `static_pages` page template and change the email address instead of the fake one `recipient@example.com` by yours into this line :

    <txp:com_connect to="recipient@example.com"

Check the `footer` form if you want to add a link list of inner pages and set accordingly the line:

    <txp:section_list active_class="active" default_title="" exclude="blog,about,contact,search,fb-instant-articles,sitemap" sections="" wraptag="ul" break="li" />

Despite we make the use of "in build" text chains for translations support, you may need to change some. Check:

* `share` form for the main title and the close icon;
* `footer` form eventually.

Note: the website footer displays a copyright with dates (e.g. 2018-2019)  where the first year corresponds to your website installation date. If you want to change this first year, check the `copyright_date` form and set this line (e.g. `$first = '2014'`):

    // This website date creation
    $first = get_pref('sql_now_created');

You can create as many "static pages" as you need! Just check the `sitemap` page template in order to include/exclude the sections you don't want to add into the build in sitemap (available from this URL: http://my-website.com/sitemap).

For better SEO results, you have an in build RSS Sitemap for your Blog (available from this URL: http://my-site.com/sitemap-rss)

Optional: Check the `fb-instant-articles` page template to be sure it is configurated to you needs, then refer to the official facebook documentation in order to generate automatic Instant Articles into the social network (available from this URL: http://my-website/fb-instant-articles)

From the Images panel, create this thumbnail profiles:

![Simplr Textpattern Theme](https://raw.githubusercontent.com/cara-tm/simplr/master/screenshots/profiles.png "smd_thumbnail plugin configuration")

### JSON-LD

For your SEO efforts, check the `JSON-LD` form in oder to set your social accounts and remove the sign `/*!` and `*/` (optional):

    /*! Add, delete, set your Social Network links below, then remove this comment line 

### CSS file optimisation

Even it is not necessary, you can gain some advantages to externalise the CSS files. Just use your browser dev console and copy/past the "defaut" CSS into a file named `default.min.css`, then upload it into a css directory and change this line into the `doctype` form:

    <txp:css format="link" name="default,lightbox_min" />

and replace it by this one:

    <link rel="stylesheet" href="<txp:site_url />css/default.min.css" />

Note: for the moment, this theme do not have a specific print css file (will be available later as a separate file).
    

### Favicon

If you want to custumize your favicon, delete this line from the `doctype` form:

    <!-- Blank favicon, change to reflect yours (Best free tool: https://realfavicongenerator.net/) 
    <link href="data:image/x-icon;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQEAYAAABPYyMiAAAABmJLR0T///////8JWPfcAAAACXBIWXMAAABIAAAASABGyWs+AAAAF0lEQVRIx2NgGAWjYBSMglEwCkbBSAcACBAAAeaR9cIAAAAASUVORK5CYII=" rel="icon" type="image/x-icon"> -->

And replace it by these ones:

    <link rel="apple-touch-icon" sizes="180x180" href="<txp:site_url />apple-touch-icon.png">
    <link rel="icon" type="image/png" sizes="32x32" href="<txp:site_url />favicon-32x32.png">
    <link rel="icon" type="image/png" sizes="16x16" href="<txp:site_url />favicon-16x16.png">
    <link rel="manifest" href="<txp:site_url />site.webmanifest">
    <link rel="mask-icon" href="<txp:site_url />safari-pinned-tab.svg" color="#555555">
    <meta name="msapplication-TileColor" content="#555555">
    <meta name="theme-color" content="#555555">

Provided by the excellent online tool available here: https://realfavicongenerator.net/

You have finished. Have a cup of coffee ☕️, then enjoy!

## Acknowledgement

Special thanks to Devs (Bloke, Phil and Oleg, others too) for all their works and their attention to Textpattern users and for all new kind features included into the Textpattern 4.7.2 version.