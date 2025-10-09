<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Core 0.9.16

Core functionality of your website.

<p align="center"><img src="SCREENSHOT.png" alt="Screenshot"></p>

## How to install an extension

[Download ZIP file](https://github.com/annaesvensson/yellow-core/archive/refs/heads/main.zip) and copy it into your `system/extensions` folder. [Learn more about extensions](https://github.com/annaesvensson/yellow-update).

## How to edit a website on your computer

You can edit your website in a text editor. The `content` folder contains the content files of the website. You can edit your website here. The `media` folder contains the media files of the website. You can store your images and files here. The `system` folder contains the system files of the website. You can find configuration files here.

At the top of a page you can change `Title` and other [page settings](#settings-page). Below you can change text and images. If you want that a different page title is shown in the navigation, use `TitleNavigation` with a short title for the navigation. Text formatting with Markdown is supported. HTML is also supported. [Learn more about text formatting](https://datenstrom.se/yellow/help/how-to-change-the-content).

## How to customise a website

You can customise the appearance of your website with HTML and CSS. All HTML files are stored in your `system/layouts` folder. All CSS files are stored in your `system/themes` folder. You can change these files as you like and also add your own files. Your changes will not be overwritten when the website is updated. [Learn more about layouts](https://datenstrom.se/yellow/help/how-to-customise-a-layout) and [themes](https://datenstrom.se/yellow/help/how-to-customise-a-theme).

You can customise the appearance of your website with extensions. This allows you to customise nearly every aspect of the system. The idea is that the standard installation includes the most important things for small websites. You can add more features later. We are using the same API everywhere, from layout files to extensions. [Learn more about extensions](https://github.com/annaesvensson/yellow-update) and [making extensions](https://github.com/annaesvensson/yellow-publish).

# How to update a website

You can update your website in a web browser or at the command line. You can find information about the latest [product changes and extensions](https://datenstrom.se/yellow/help/what-s-new) in the help. Keep in mind that only available extensions will be updated, you may need to update experimental extensions manually. [Learn more about extensions](https://github.com/annaesvensson/yellow-update).

## How to hide a page

Set `Status: unlisted` in the [page settings](#settings-page) at the top of a page. The page is no longer visible in navigation, sitemap and search results. You can choose between different [status values](#settings-status), to control who can see and access a page.

## How to redirect a page

Set `Redirect` in the [page settings](#settings-page) at the top of a page. The page is redirected to another page or URL. You can continue to edit the page in the [web browser](https://github.com/annaesvensson/yellow-edit) and on your computer.

## How to use the command line

You can execute commands at the command line. This allows you, for example, to [start a web server](https://github.com/annaesvensson/yellow-serve) and [generate a static website](https://github.com/annaesvensson/yellow-generate). The available commands depend on extensions installed. Open a terminal window. Go to your installation folder, where the file `yellow.php` is. Type `php yellow.php` to show available commands.

The following commands are available:

`php yellow.php about` = Show extensions, [requires update extension](https://github.com/annaesvensson/yellow-update)  
`php yellow.php check` = Find broken links, [requires check extension](https://github.com/annaesvensson/yellow-check)  
`php yellow.php clean` = Clean static website, [requires generate extension](https://github.com/annaesvensson/yellow-generate)  
`php yellow.php generate` = Generate static website, [requires generate extension](https://github.com/annaesvensson/yellow-generate)  
`php yellow.php install` = Install extensions, [requires update extension](https://github.com/annaesvensson/yellow-update)  
`php yellow.php publish` = Publish extensions, [requires publish extension](https://github.com/annaesvensson/yellow-publish)  
`php yellow.php serve` = Start web server, [requires serve extension](https://github.com/annaesvensson/yellow-serve)  
`php yellow.php traffic` = Create traffic analytics, [requires traffic extension](https://github.com/annaesvensson/yellow-traffic)  
`php yellow.php uninstall` = Uninstall extensions, [requires update extension](https://github.com/annaesvensson/yellow-update)  
`php yellow.php update` = Update extensions, [requires update extension](https://github.com/annaesvensson/yellow-update)  
`php yellow.php user` = Create user accounts, [requires edit extension](https://github.com/annaesvensson/yellow-edit)  

## Examples

Content file with normal page:

    ---
    Title: Normal page
    ---
    This is an example page.

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod 
    tempor incididunt ut labore et dolore magna pizza. Ut enim ad minim veniam, 
    quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo.

Content file with short title:

    ---
    Title: Example page
    TitleNavigation: Example
    ---
    This is an example page with a short title for the navigation.

    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod 
    tempor incididunt ut labore et dolore magna pizza. Ut enim ad minim veniam, 
    quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo.


Content file with unlisted page:

    ---
    Title: Unlisted page
    Status: unlisted
    ---
    This page is not visible in navigation, sitemap and search results.

Content file with redirection:

    ---
    Title: Redirect page
    Redirect: https://datenstrom.se/yellow/
    ---
    This page is redirected to another page.

Content file for error page:

    ---
    Title: File not found
    Layout: error
    ---
    The requested file was not found. Oh no...

Layout file for default page:

    <?php $this->yellow->layout("header") ?>
    <div class="content">
    <div class="main" role="main">
    <h1><?php echo $this->yellow->page->getHtml("titleContent") ?></h1>
    <?php echo $this->yellow->page->getContentHtml() ?>
    </div>
    </div>
    <?php $this->yellow->layout("footer") ?>

## Settings

<a id="settings-system"></a>The following settings can be configured in file `system/extensions/yellow-system.ini`:

`Sitename` = name of the website  
`Author` = name of the webmaster  
`Email` = email of the webmaster  
`Language` = default language, e.g. `en`  
`Layout` = default layout  
`Theme` = default theme  
`Parser` = default content parser  
`Status` = default page status, [supported status values](#settings-status)  
`CoreServerUrl` = URL of the website, `auto` for automatic detection  
`CoreTimezone` = timezone of the website, [supported timezones](https://www.php.net/manual/en/timezones.php)  
`CoreContentExtension` = file extension for content  
`CoreContentDefaultFile` = content file for folders  
`CoreContentErrorFile` = content file for error page  
`CoreLanguageFile` = file with language settings  
`CoreUserFile` = file with user settings  
`CoreWebsiteFile` = log file of the website  
`CoreAssetLocation` = location for virtually mapped system files  
`CoreMediaLocation` = location for media files  
`CoreDownloadLocation` = location for downloads  
`CoreImageLocation` = location for images  
`CoreThumbnailLocation` = location for thumbnails  
`CoreMultiLanguageMode` = enable multi language mode, 1 or 0  
`CoreDebugMode` = enable debug mode, 0 to 3  

<a id="settings-page"></a>The following settings can be configured at the top of a page:

`Title` = page title  
`TitleContent` = page title shown in content  
`TitleNavigation` = page title shown in navigation  
`TitleHeader` = page title shown in web browser  
`TitleSlug` = page title used for saving the page  
`Description` = page description  
`Author` = page author(s), comma separated  
`Email` = email of page author  
`Language` = page language, e.g. `en`  
`Layout` = page layout  
`LayoutNew` = page layout for creating a new page  
`Theme` = page theme  
`Parser` = page content parser  
`Status` = page status, [supported status values](#settings-status)  
`Redirect` = redirect to another page or URL  
`Image` = page image  
`ImageAlt` = description of the page image  
`Modified` = page modification date, YYYY-MM-DD format  
`Published` = page publication date, YYYY-MM-DD format  
`Tag` = page tag(s) for categorisation, comma separated  
`Generate` = option(s) for generating a static website, comma separated  
`Comment` = option(s) for showing comments, comma separated  

<a id="settings-status"></a>The following page status values are supported:

`public` = page is a normal page  
`private` = page is not visible, user needs to enter password, [requires private extension](https://github.com/schulle4u/yellow-private)  
`draft` = page is not visible, user needs to log in, [requires draft extension](https://github.com/annaesvensson/yellow-draft)  
`unlisted` = page is not visible, but can be accessed with the correct link  
`shared` = page is not visible, but can be included in other pages  

<a id="settings-files"></a>The following files can be customised:

`content/1-home/page.md` = content file for home page  
`content/shared/page-error-404.md` = content file for error page  
`system/layouts/default.html` = layout file for default page  
`system/layouts/error.html` = layout file for error page  
`system/layouts/header.html` = layout file for default HTML header  
`system/layouts/footer.html` = layout file for default HTML footer  
`system/layouts/navigation.html` = layout file for default HTML navigation  
`system/layouts/pagination.html` = layout file for default HTML pagination  

## Acknowledgements

This extension was previously maintained by Mark Seuffert and David Fehrmann. Thank you for the good work.

## Developer

Anna Svensson. [Get help](https://datenstrom.se/yellow/help/).
