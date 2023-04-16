<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Core 0.8.107

Webbplatsens kärnfunktion.

<p align="center"><img src="core-screenshot.png?raw=true" alt="Skärmdump"></p>

## Hur man installerar ett tillägg

[Ladda ner ZIP-filen](https://github.com/annaesvensson/yellow-core/archive/main.zip) och kopiera den till din `system/extensions` mapp. [Läs mer om tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md).

## Hur man redigerar en webbplats på datorn

Du kan ändra allt i filhanteraren på din dator. Mappen `content` innehåller webbplatsens innehållsfilerna. Du kan redigera din webbplats här. Mappen `media` innehåller webbplatsens mediefiler. Du kan lagra dina bilder och filer här. Mappen `system` innehåller webbplatsens systemfilerna. Du kan hitta installerade tillägg och konfigurationsfilar här.

## Hur man använder kommandoraden

Du kan köra kommandon från kommandoraden. Detta ger dig möjlighet att [starta en webbserver](https://github.com/annaesvensson/yellow-serve/tree/main/README-sv.md), [bygga en statisk webbplats](https://github.com/annaesvensson/yellow-static/tree/main/README-sv.md) och göra andra saker. Öppna ett terminalfönster. Gå till installationsmappen där filen `yellow.php` finns. Skriv `php yellow.php` för att visa tillgängliga kommandona. De tillgängliga kommandona beror på installerade tillägg.

Följande kommandon är tillgängliga:

`php yellow.php about` = Visa tillägg, [kräver update-tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md)  
`php yellow.php build` = Bygg statisk webbplats, [kräver static-tillägg](https://github.com/annaesvensson/yellow-static/tree/main/README-sv.md)  
`php yellow.php check` = Kontrollera statisk webbplats, [kräver static-tillägg](https://github.com/annaesvensson/yellow-static/tree/main/README-sv.md)  
`php yellow.php clean` = Rengör statisk webbplats, [kräver static-tillägg](https://github.com/annaesvensson/yellow-static/tree/main/README-sv.md)  
`php yellow.php install` = Installera tillägg, [kräver update-tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md)  
`php yellow.php publish` = Publicera tillägg, [kräver publish-tillägg](https://github.com/annaesvensson/yellow-publish/tree/main/README-sv.md)  
`php yellow.php serve` = Starta inbyggda webbservern, [kräver serve-tillägg](https://github.com/annaesvensson/yellow-serve/tree/main/README-sv.md)  
`php yellow.php traffic` = Skapa trafikanalyser, [kräver traffic-tillägg](https://github.com/annaesvensson/yellow-traffic/tree/main/README-sv.md)  
`php yellow.php uninstall` = Avinstallera tillägg, [kräver update-tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md)  
`php yellow.php update` = Uppdatera webbplats, [kräver update-tillägg](https://github.com/annaesvensson/yellow-update/tree/main/README-sv.md)  
`php yellow.php user` = Skapa användarkonton, [kräver edit-tillägg](https://github.com/annaesvensson/yellow-edit/tree/main/README-sv.md)  

## Hur man döljer en sida

Ställ `Status: unlisted` i [sidinställningarna](#inställningar-page) högst upp på en sida. Sidan är inte längre synlig i navigation och sökresultat. Du kan välja mellan olika [statusvärden](#inställningar-status) för att bestämma vem som kan se och komma åt en sida. 

## Hur man omdirigerar en sida

Ställ `Redirect` i [sidinställningarna](#inställningar-page) högst upp på en sida. Sidan omdirigeras till en annan sida eller URL. Du kan fortsätta att redigera sidan i [webbläsaren](https://github.com/annaesvensson/yellow-edit/tree/main/README-sv.md) och på din dator. 

## Hur man anpassar en sida

Ställ `layout` i [sidinställningarna](#inställningar-page) högst upp på en sida. Alla layoutfiler finns i `system/layouts` mappen. HTML-koden för en sida kan du anpassa i layoutfilen. Ta en titt på layoutfilen för standardsidan och gör dina egna layoutfiler om det behövs. Dina ändringar kommer inte att skrivas över när webbplatsen uppdateras. [Läs mer om layouter](https://datenstrom.se/sv/yellow/help/how-to-customise-a-layout).

## Exempel

Innehållsfil med normal sida:

    ---
    Title: Normal sida
    ---
    Detta är en exempelsida.

Innehållsfil med olistad sida:

    ---
    Title: Olistad sida
    Status: unlisted
    ---
    Den här sidan är inte synlig i navigation och sökresultat.

Innehållsfil med omdirigering:

    ---
    Title: Omdirigera sida
    Redirect: https://datenstrom.se/sv/yellow/
    ---
    Den här sidan omdirigeras till en annan sida.

Innehållsfil för felsidan:

    ---
    Title: Filen hittades inte
    Layout: error
    ---
    Den begärda filen kunde inte hittas. Å nej...

Layoutfil för standardsidan:

    <?php $this->yellow->layout("header") ?>
    <div class="content">
    <div class="main" role="main">
    <h1><?php echo $this->yellow->page->getHtml("titleContent") ?></h1>
    <?php echo $this->yellow->page->getContent() ?>
    </div>
    </div>
    <?php $this->yellow->layout("footer") ?>

## Inställningar

<a id="inställningar-system"></a>Följande inställningar kan konfigureras i filen `system/extensions/yellow-system.ini`:

`Sitename` = webbplatsens namn  
`Author` = webmasterns namn  
`Email` = webmasterns email  
`Language` = standardspråk, t.ex. `sv`  
`Layout` = standardlayout  
`Theme` = standardtema  
`Parser` = standard innehållsparser  
`Status` = standard sidstatus, [stödda statusvärden](#inställningar-status)  
`CoreServerUrl` = webbplatsens URL, `auto` för automatisk detektering  
`CoreTimezone` = webbplatsens tidszon, [stödda tidszoner](https://www.php.net/manual/en/timezones.php)  
`CoreContentExtension` = filformat för innehåll  
`CoreContentDefaultFile` = innehållsfil för mappar  
`CoreContentErrorFile` = innehållsfil för felsida  
`CoreLanguageFile` = fil med språkinställningar  
`CoreUserFile` = fil med användarinställningar  
`CoreWebsiteFile` = loggfilen för webbplatsen  
`CoreMediaLocation` = plats för mediafiler  
`CoreDownloadLocation` = plats för nedladdningar  
`CoreImageLocation` = plats för bilder  
`CoreThumbnailLocation` = plats för miniatyrbilder  
`CoreExtensionLocation` = plats för virtuellt mappade tilläggsfiler  
`CoreThemeLocation` = plats för virtuellt mappade temafiler  
`CoreMultiLanguageMode` = aktivera flerspråkigt läge, 1 eller 0  
`CoreDebugMode` = aktivera felsökningsläget, 0 till 3  

<a id="inställningar-page"></a>Följande inställningar kan konfigureras högst upp på en sida:

`Title` = namn på sidan  
`TitleContent` = namn på sidan som visas i innehållet  
`TitleNavigation` = namn på sidan som visas i navigeringen  
`TitleHeader` = namn på sidan som visas i webbläsaren  
`TitleSlug` = namn för att spara sidan  
`Description` = sidans beskrivning  
`Author` = sidans författare, kommaseparerade  
`Email` = email av sidans författare  
`Language` = sidans språk, t.ex. `sv`  
`Layout` = sidans layout  
`LayoutNew` = sidans layout för att skapa en ny sida  
`Theme` = sidans tema  
`Parser` = sidans innehållsparser  
`Status` = sidans status, [stödda statusvärden](#inställningar-status)  
`Redirect` = omdirigera till en ny sida eller URL  
`Image` = sidans bild  
`ImageAlt` = beskrivning av sidans bild  
`Modified` = sidans ändringsdatum, ÅÅÅÅ-MM-DD format  
`Published` = sidans publiceringsdatum, ÅÅÅÅ-MM-DD format  
`Tag` = taggar för kategorisering av sidan, kommaseparerade  
`Build` = alternativ för att bygga en statisk webbplats, kommaseparerade  
`Comment` = alternativ för att visa kommentarer, kommaseparerade  

<a id="inställningar-status"></a>Följande sidstatusvärden stöds:

`public` = sidan är en vanlig sida  
`private` = sidan är inte synlig, användaren måste ange lösenord, [kräver private-tillägg](https://github.com/schulle4u/yellow-private)  
`draft` = sidan är inte synlig, användaren måste logga in, [kräver draft-tillägg](https://github.com/annaesvensson/yellow-draft/tree/main/README-sv.md)  
`unlisted` = sidan är inte synlig, men kan nås med rätt länk  
`shared` = sidan är inte synlig, men kan ingå i andra sidor  

<a id="inställningar-files"></a>Följande filer kan anpassas:

`content/1-home/page.md` = innehållsfil för hemsidan  
`content/shared/page-error-404.md` = innehållsfil för felsidan  
`system/layouts/default.html` = layoutfil för standardsidan  
`system/layouts/error.html` = layoutfil för felsidan  
`system/layouts/header.html` = layoutfil för standard HTML-header  
`system/layouts/footer.html` = layoutfil för standard HTML-footer  
`system/layouts/navigation.html` = layoutfil för standard HTML-navigering  
`system/layouts/pagination.html` = layoutfil för standard HTML-paginering  

Loggfilen finns i filen `system/extensions/yellow-website.log`.

## Utvecklare

Mark Seuffert, David Fehrmann. [Få hjälp](https://datenstrom.se/sv/yellow/help/).
