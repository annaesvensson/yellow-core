<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Core 0.8.89

Core functionality of the website.

<p align="center"><img src="core-screenshot.png?raw=true" alt="Screenshot"></p>

## How to edit a website on your computer

You can change everything in the file manager on your computer. The `content` folder contains the content files of the website. You can edit your website here. The `media` folder contains the media files of the website. You can store your images and files here. The `system` folder contains the system files of the website. You can customise installed extensions and configuration files here.

## How to hide a page

Set `Status: unlisted` in the [page settings](#settings-page) at the top of a page. The page is no longer visible in navigation and search results. You can choose between different [status values](#settings-status), to control who can see and access a page.

## How to redirect a page

Set `Redirect` in the [page settings](#settings-page) at the top of a page. The page is redirected to another page or URL. You can continue to edit the page in the [web browser](https://github.com/annaesvensson/yellow-edit) and on your computer.

## How to customise a page 

Set `Layout` in the [page settings](#settings-page) at the top of a page. All layout files are stored in your `system/layouts` folder. The HTML code of a page can be customised in the layout file. Have a look at the default layout file and make your own layout files when needed. Your changes will not be overwritten when the website is updated.

## Examples

Content file with normal page:

    ---
    Title: Normal page
    ---
    This is an example page.

Content file with unlisted page:

    ---
    Title: Unlisted page
    Status: unlisted
    ---
    This page is not visible in navigation and search results.

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
    <?php echo $this->yellow->page->getContent() ?>
    </div>
    </div>
    <?php $this->yellow->layout("footer") ?>

## Settings

<a id="settings-system"></a>The following settings can be configured in file `system/extensions/yellow-system.ini`:

`Sitename` = name of the website  
`Author` = name of the webmaster  
`Email` = email of the webmaster  
`Layout` = default layout  
`Theme` = default theme  
`Language` = default language  
`Parser` = default page parser  
`Status` = default page status, [supported status values](#settings-status)  
`CoreServerUrl` = URL of the website, when used as a content management system  
`CoreStaticUrl` = URL of the website, when used as a static site generator  
`CoreTimezone` = timezone of the website, [supported timezones](https://www.php.net/manual/en/timezones.php)  
`CoreContentExtension` = file extension for content  
`CoreContentDefaultFile` = content file for folders  
`CoreContentErrorFile` = content file for error page  
`CoreUserFile` = file with user settings  
`CoreLanguageFile` = file with language settings  
`CoreWebsiteFile` = log file of the website  
`CoreMediaLocation` = location for media files  
`CoreDownloadLocation` = location for downloads  
`CoreImageLocation` = location for images  
`CoreThumbnailLocation` = location for thumbnails  
`CoreExtensionLocation` = location for virtually mapped extension files  
`CoreThemeLocation` = location for virtually mapped theme files  
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
`Layout` = page layout  
`LayoutNew` = page layout for creating a new page  
`Theme` = page theme  
`Language` = page language  
`Parser` = page parser  
`Status` = page status, [supported status values](#settings-status)  
`Redirect` = redirect to another page or URL  
`Image` = page image  
`ImageAlt` = description of the page image  
`Modified` = page modification date, YYYY-MM-DD format  
`Published` = page publication date, YYYY-MM-DD format  
`Tag` = page tag(s) for categorisation, comma separated  
`Build` = page option(s) for building a static website, comma separated  
`Comment` = page option(s) for showing comments, comma separated  

<a id="settings-status"></a>The following page status values are supported:

`public` = page is a normal page  
`private` = page is not visible, user needs to enter password, [requires private extension](https://github.com/schulle4u/yellow-extensions-schulle4u/tree/main/private)  
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

## Installation

[Download extension](https://github.com/annaesvensson/yellow-core/archive/main.zip) and copy zip file into your `system/extensions` folder. Right click if you use Safari.

## Developer

Datenstrom. [Get help](https://datenstrom.se/yellow/help/).
