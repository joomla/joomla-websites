# Banner Ads Implementation Guide for all joomla.org sites
This file describes how Joomla.org web masters should implement the ad serving code on our web properties.

## ads.joomla.org
We are running our own internal ([Revive](https://www.revive-adserver.com/)) ad server that should be serving all our ads. *We should not be serving ads directly from AdSense.*

## Ad code
The code to show ads is simple and in two parts.

### General script
```html
<script async src="//ads.joomla.org/www/delivery/asyncjs.php"></script>
```
This code should be included **once** per page. The best way to include this code is most likely by pasting it into the template of the site. The code should be inside the `<body>` of the page near the `</body>` closing tag.

### Zone specific code
```html
<ins data-revive-zoneid="xx" data-revive-id="4bacaeba2f8655edc9ca810c946aab5a"></ins>
```
The xx should be replaced with a zone ID given to you by the team managing the ad server. A good way to do this is to create a Joomla module with custom html. Make sure you disable the editor when pasting in or editing this code as it might otherwise strip some of the html.

If you need to get one or more zone id's for a site then please contect soren.beck-jensen@community.joomla.org

## Ad formats
We currently have two (well kind of three) ad formats that you can implement on your site.

### 728 x 90 (Leaderboard)
This ad format is the most popular online and we should aim to have at least one of these on every page. Placing it above, below or in the middle of content are all good options.

![Eample banner](http://placehold.it/728x90)

### 300 x 250 (Medium rectangle)
This ad format is also very popular and generally attracts more clicks, but is currently not easy to fit into our generic template (*See below for solution*). 

![Eample banner](http://placehold.it/300x250)

### 270 x 225 (Custom size)
The width of the right hand column the current standard Joomla template is only 270px wide so fitting the above banner into breaks layout. To overcome this, we have developed a little code snippit that will scale the above medium rectangle down a little.

#### Scaling CSS code
```html
<style>
.ad270 {
    width:270px;
    padding: 0;
    overflow:hidden;
}

.ad270 > ins > iframe {

    -ms-transform: scale(0.90);
    -moz-transform: scale(0.90);
    -o-transform: scale(0.90);
    -webkit-transform: scale(0.90);
    transform: scale(0.90);

    -ms-transform-origin: 0 0;
    -moz-transform-origin: 0 0;
    -o-transform-origin: 0 0;
    -webkit-transform-origin: 0 0;
    transform-origin: 0 0;
}
</style>
```
This code can be written inline or added to you custom.css file. Then simply add a `<div>` with the class `ad270` and your ad will be scaled.

```html
<div class="ad270"><ins data-revive-zoneid="xx" data-revive-id="4bacaeba2f8655edc9ca810c946aab5a"></ins></div>
```


![Eample banner](http://placehold.it/270x225)




## General guidelines
- Do not add too many ads to each page. 2-3 ad positions should be enough.
