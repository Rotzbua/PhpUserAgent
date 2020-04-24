# PHP User Agent Parser

[![Join the chat at https://gitter.im/PhpUserAgentParser/Lobby](https://badges.gitter.im/PhpUserAgentParser/Lobby.svg)](https://gitter.im/PhpUserAgentParser/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


[![Latest Stable Version](https://poser.pugx.org/donatj/phpuseragentparser/version)](https://packagist.org/packages/donatj/phpuseragentparser)
[![Total Downloads](https://poser.pugx.org/donatj/phpuseragentparser/downloads)](https://packagist.org/packages/donatj/phpuseragentparser)
[![License](https://poser.pugx.org/donatj/phpuseragentparser/license)](https://packagist.org/packages/donatj/phpuseragentparser)
[![Build Status](https://travis-ci.org/donatj/phpUserAgent.svg?branch=master)](https://travis-ci.org/donatj/phpUserAgent)
[![Build Status](https://github.com/donatj/phpUserAgent/workflows/CI/badge.svg?)](https://github.com/donatj/phpUserAgent/actions?query=workflow%3ACI)


## What It Is

A simple, streamlined PHP user-agent parser!

Licensed under the MIT license: http://www.opensource.org/licenses/mit-license.php

## Upgrading to `1.*`

The new `1.*` release **does not break compatibility** with `0.*` and nothing need to change to upgrade. However, the global `parse_user_agent` is now deprecated; it has been replaced with the namespaced `\donatj\UserAgent\parse_user_agent` and functions exactly the same. You can easily replace any existing call to `parse_user_agent` with `\donatj\UserAgent\parse_user_agent`

In addition, 1.x adds a convenience object wrapper you may use should you prefer. More information on this is in the Usage section below.

## Why Use This

You have your choice in user-agent parsers. This one detects **all modern browsers** in a very light, quick, understandable fashion.
It is less than 200 lines of code, and consists of just three regular expressions!
It can also correctly identify exotic versions of IE others fail on.

It offers 100% unit test coverage, is installable via Composer, and is very easy to use.

## What It Does Not Do

This is not meant as a browser "knowledge engine" but rather a simple parser. Anything not adequately provided directly by the user agent string itself will simply not be provided by this.


### OS Versions

User-agent strings **are not** a reliable source of OS Version!

- Many agents simply don't send the information.
- Others provide varying levels of accuracy.
- Parsing Windows versions alone almost nearly doubles the size of the code.

I'm much more interested in keeping this thing *tiny* and accurate than adding niché features and would rather focus on things that can be **done well**.

All that said, there is the start of a [branch to do it](https://github.com/donatj/PhpUserAgent/tree/os_version_detection) I created for a client if you want to poke it, I update it from time to time, but frankly if you need to *reliably detect OS Version*, using user-agent isn't the way to do it. I'd go with JavaScript.

### Undetectable Browsers

- **Brave** - Brave is simply not differentiable from Chrome. This was a design decision on their part.

## Requirements

- **php**: >=5.3.0

## Installing

PHP User Agent is available through Packagist via Composer.

Install the latest version with:

```bash
composer require 'donatj/phpuseragentparser'
```

## Usage

The classic procedural use is as simple as:

```php
$ua_info = parse_user_agent();
/*
array(
	'platform' => '[Detected Platform]',
	'browser'  => '[Detected Browser]',
	'version'  => '[Detected Browser Version]',
);
*/
```


The new object oriented wrapper form:

```php
$parser = new UserAgentParser();

$ua = $parser->parse();
// or
$ua = $parser();

$ua->platform();
$ua->browser();
$ua->browserVersion();
```

## Currently Detected Platforms

- Macintosh  
- Chrome OS  
- Linux  
- Windows  
- Android  
- BlackBerry  
- FreeBSD  
- iPad  
- iPhone  
- iPod  
- Kindle  
- Kindle Fire  
- NetBSD  
- New Nintendo 3DS  
- Nintendo 3DS  
- Nintendo DS  
- Nintendo Switch  
- Nintendo Wii  
- Nintendo WiiU  
- OpenBSD  
- PlayBook  
- PlayStation 3  
- PlayStation 4  
- PlayStation Vita  
- Tizen  
- Windows Phone  
- Xbox  
- Xbox One

## Currently Detected Browsers

- AdsBot-Google  
- Android Browser  
- Baiduspider  
- bingbot  
- BlackBerry Browser  
- Browser  
- Bunjalloo  
- Camino  
- Chrome  
- curl  
- Edge  
- facebookexternalhit  
- FeedValidator  
- Firefox  
- Googlebot  
- Googlebot-Image  
- Googlebot-Video  
- HeadlessChrome  
- IEMobile  
- Kindle  
- Lynx  
- Midori  
- MSIE  
- msnbot-media  
- NetFront  
- NintendoBrowser  
- OculusBrowser  
- Opera  
- Puffin  
- Safari  
- SamsungBrowser  
- Silk  
- TizenBrowser  
- UC Browser  
- Valve Steam Tenfoot  
- Vivaldi  
- Wget  
- WordPress  
- Yandex  
- YandexBot

More information is available at [Donat Studios](http://donatstudios.com/PHP-Parser-HTTP_USER_AGENT).