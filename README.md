# device-detector-js

Device-detector-js is a precise user agent parser and device detector written in TypeScript, backed by the largest and most up-to-date open-source user agent database.

Device-detector-js will parse any user agent and detect the browser, operating system, device used (desktop, tablet, mobile, tv, cars, console, etc.), brand and model. Works with Node.js and in the browser.

This library is heavily tested and relies on over 10,000 tests to detect thousands of user agent strings, even from rare and obscure browsers and devices.

#### This is a javascript port of [Matomo device-detector](https://github.com/matomo-org/device-detector) (5.0.1).

[![Coveralls github](https://img.shields.io/coveralls/github/etienne-martin/device-detector-js.svg)](https://coveralls.io/github/etienne-martin/device-detector-js)
[![CircleCI build](https://img.shields.io/circleci/project/github/RedSparr0w/node-csgo-parser.svg)](https://circleci.com/gh/etienne-martin/device-detector-js)
[![node version](https://img.shields.io/node/v/device-detector-js.svg)](https://www.npmjs.com/package/device-detector-js)
[![npm version](https://img.shields.io/npm/v/device-detector-js.svg)](https://www.npmjs.com/package/device-detector-js)
[![npm monthly downloads](https://img.shields.io/npm/dm/device-detector-js.svg)](https://www.npmjs.com/package/device-detector-js)

## Features

- No dependencies
- TypeScript support
- Thoroughly tested

## Demo

https://lx3rzx16x9.codesandbox.io/

## Getting Started

### Installation

To use device-detector-js in your project, run:

```bash
npm install device-detector-js
```

### Usage

##### ES2015 import:
```javascript
import DeviceDetector from "device-detector-js";
```

##### TypeScript import:
```typescript
import DeviceDetector = require("device-detector-js");
```

**Example** - user agent detection:

```javascript
import DeviceDetector from "device-detector-js";

const deviceDetector = new DeviceDetector();
const userAgent = "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.81 Safari/537.36";
const device = deviceDetector.parse(userAgent);

console.log(device);
```

Output:

```json
{
  "client": {
    "type": "browser",
    "name": "Chrome",
    "version": "69.0",
    "engine": "Blink",
    "engineVersion": ""
  },
  "os": {
    "name": "Mac",
    "version": "10.13",
    "platform": ""
  },
  "device": {
    "type": "desktop",
    "brand": "Apple",
    "model": ""
  },
  "bot": null
}
```

**Example** - bot detection:

```javascript
import BotDetector from "device-detector-js/dist/parsers/bot";

const botDetector = new BotDetector();
const userAgent = "Mozilla/5.0 (iPhone; CPU iPhone OS 6_0 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/6.0 Mobile/10A5376e Safari/8536.25 (compatible; Googlebot-Mobile/2.1; +http://www.google.com/bot.html)";
const bot = botDetector.parse(userAgent);

if (bot) {
  console.log(bot);
}
```

Output:

```json
{
  "name": "Googlebot",
  "category": "Search bot",
  "url": "http://www.google.com/bot.html",
  "producer": {
    "name": "Google Inc.",
    "url": "http://www.google.com"
  }
}
```

## API Documentation

#### new DeviceDetector([options])

- `options` <[Object]> Options object which might have the following properties:
  - `skipBotDetection` <[boolean]> If true, bot detection will completely be skipped (bots will be detected as regular devices). Defaults to `false`.
  - `versionTruncation` <[0 | 1 | 2 | 3 | null]> Passing `null` disables version truncation, so full versions will be returned. Defaults to `1`, only minor versions will be returned (e.g. X.Y).
  
## TypeScript

Type definitions are included in this library and exposed via:

```typescript
import { DeviceDetectorResult, DeviceDetectorOptions } from "device-detector-js";
``` 

## ⚠️ Browser Environment

Even though this library can run in the browser, **it is strongly advised against doing so**, unless you are not concerned with performance. Keep in mind that using this library in browser-side code means sending around 432 KB of Regex rules and 144 KB of javascript (uncompressed and unminified), which may result in a poor user experience for people with a slow Internet connection.

**You may experience inconsistencies when running this library in a browser environment, as some browsers like Safari do not yet support lookbehind syntax.**
  
## What device-detector-js is able to detect

The lists below are auto generated and updated from time to time. Some of them might not be complete.

*Last update: 2021/12/07*

### List of detected operating systems:

AIX, Android, AmigaOS, tvOS, Arch Linux, BackTrack, Bada, BeOS, BlackBerry OS, BlackBerry Tablet OS, Brew, Caixa Mágica, CentOS, Chrome OS, CyanogenMod, Debian, Deepin, DragonFly, DVKBuntu, Fedora, Fenix, Firefox OS, Fire OS, Freebox, FreeBSD, FydeOS, Gentoo, GridOS, Google TV, HP-UX, Haiku OS, iPadOS, HarmonyOS, HasCodingOS, IRIX, Inferno, Java ME, KaiOS, Knoppix, Kubuntu, GNU/Linux, Lubuntu, Lumin OS, VectorLinux, Mac, Maemo, Mageia, Mandriva, MeeGo, MocorDroid, Mint, MildWild, MorphOS, NetBSD, MTK / Nucleus, MRE, Nintendo, Nintendo Mobile, OS/2, OSF1, OpenBSD, OpenWrt, Ordissimo, PCLinuxOS, PlayStation Portable, PlayStation, Red Hat, RISC OS, Roku OS, Rosa, Remix OS, REX, RazoDroiD, Sabayon, SUSE, Sailfish OS, SeewoOS, Slackware, Solaris, Syllable, Symbian, Symbian OS, Symbian OS Series 40, Symbian OS Series 60, Symbian^3, ThreadX, Tizen, TmaxOS, Ubuntu, watchOS, WebTV, Whale OS, Windows, Windows CE, Windows IoT, Windows Mobile, Windows Phone, Windows RT, Xbox, Xubuntu, YunOs, iOS, palmOS, webOS

### List of detected browsers:

115 Browser, 2345 Browser, 360 Phone Browser, 360 Browser, 7654 Browser, Avant Browser, ABrowse, ANT Fresco, ANTGalio, Aloha Browser, Aloha Browser Lite, Amaya, Amigo, Android Browser, AOL Desktop, AOL Shield, Arora, Arctic Fox, Amiga Voyager, Amiga Aweb, Arvin, Atom, Atomic Web Browser, Avast Secure Browser, AVG Secure Browser, Avira Scout, AwoX, Beaker Browser, Beamrise, BlackBerry Browser, Baidu Browser, Baidu Spark, Basilisk, Beonex, BlackHawk, Bunjalloo, B-Line, Blue Browser, Bonsai, Borealis Navigator, Brave, BriskBard, BrowseX, Browzar, Biyubi, Byffox, Camino, CCleaner, Chedot, Centaury, Coc Coc, CoolBrowser, Colibri, Comodo Dragon, Coast, Charon, CM Browser, Chrome Frame, Headless Chrome, Chrome, Chrome Mobile iOS, Conkeror, Chrome Mobile, CoolNovo, CometBird, COS Browser, Cornowser, Chim Lac, ChromePlus, Chromium, Chromium GOST, Cyberfox, Cheshire, Crusta, Craving Explorer, Crazy Browser, Cunaguaro, Chrome Webview, dbrowser, Peeps dBrowser, Deepnet Explorer, deg-degan, Deledao, Delta Browser, DeskBrowse, Dolphin, Dorado, Dot Browser, Dooble, Dillo, DuckDuckGo Privacy Browser, Ecosia, Edge WebView, Epic, Elinks, Element Browser, Elements Browser, eZ Browser, EUI Browser, GNOME Web, Espial TV Browser, Falkon, Faux Browser, Firefox Mobile iOS, Firebird, Fluid, Fennec, Firefox, Firefox Focus, Firefox Reality, Firefox Rocket, Flock, Flow, Firefox Mobile, Fireweb, Fireweb Navigator, Flash Browser, Flast, FreeU, Galeon, Ghostery Privacy Browser, GinxDroid Browser, Glass Browser, Google Earth, GOG Galaxy, GoBrowser, Harman Browser, HasBrowser, Hawk Turbo Browser, Helio, hola! Browser, HotJava, Huawei Browser Mobile, Huawei Browser, iBrowser, iBrowser Mini, IBrowse, iCab, iCab Mobile, Iridium, Iron Mobile, IceCat, IceDragon, Isivioo, Iceweasel, Internet Explorer, IE Mobile, Iron, Japan Browser, Jasmine, JavaFX, Jig Browser, Jig Browser Plus, Jio Browser, K.Browser, Kindle Browser, K-meleon, Konqueror, Kapiko, Kinza, Kiwi, Kode Browser, Kylo, Kazehakase, Cheetah Browser, Lagatos Browser, LieBaoFast, LG Browser, Light, Links, Lolifox, Lovense Browser, LT Browser, LuaKit, Lulumi, Lunascape, Lunascape Lite, Lynx, Mandarin, mCent, MicroB, NCSA Mosaic, Meizu Browser, Mercury, Mobile Safari, Midori, Mobicip, MIUI Browser, Mobile Silk, Minimo, Mint Browser, Maxthon, Maelstrom, MxNitro, Mypal, Monument Browser, MAUI WAP Browser, Navigateur Web, NFS Browser, Nokia Browser, Nokia OSS Browser, Nokia Ovi Browser, Nox Browser, NetSurf, NetFront, NetFront Life, NetPositive, Netscape, NTENT Browser, Oculus Browser, Opera Mini iOS, Obigo, Odin, OceanHero, Odyssey Web Browser, Off By One, OhHai Browser, ONE Browser, Opera GX, Opera Neon, Opera Devices, Opera Mini, Opera Mobile, Opera, Opera Next, Opera Touch, Orca, Ordissimo, Oregano, Origin In-Game Overlay, Origyn Web Browser, Openwave Mobile Browser, OpenFin, OmniWeb, Otter Browser, Palm Blazer, Pale Moon, Polypane, Oppo Browser, Palm Pre, Puffin, Palm WebPro, Palmscape, Perfect Browser, Phantom Browser, Phoenix, Phoenix Browser, PlayFree Browser, Polaris, Polarity, PolyBrowser, PrivacyWall, PSI Secure Browser, Microsoft Edge, Qazweb, QQ Browser Lite, QQ Browser Mini, QQ Browser, Qutebrowser, Quark, QupZilla, Qwant Mobile, QtWebEngine, Realme Browser, Rekonq, RockMelt, Samsung Browser, Sailfish Browser, Seewo Browser, SEMC-Browser, Sogou Explorer, Safari, Safe Exam Browser, SalamWeb, Secure Browser, SFive, Shiira, SimpleBrowser, Sizzy, Skyfire, Seraphic Sraf, Sleipnir, Slimjet, SP Browser, Stampy Browser, 7Star, Smart Lenovo Browser, Smooz, Snowshoe, Sogou Mobile Browser, Spectre Browser, Splash, Sputnik Browser, Sunrise, SuperBird, Super Fast Browser, Sushi Browser, surf, Stargon, START Internet Browser, Steam In-Game Overlay, Streamy, Swiftfox, Seznam Browser, T-Browser, t-online.de Browser, Tao Browser, TenFourFox, Tenta Browser, Tizen Browser, Tungsten, ToGate, TweakStyle, TV Bro, UBrowser, UC Browser, UC Browser HD, UC Browser Mini, UC Browser Turbo, UR Browser, Uzbl, Venus Browser, Vivaldi, vivo Browser, Vision Mobile Browser, VMware AirWatch, Wear Internet Browser, Web Explorer, WebPositive, Waterfox, Whale Browser, wOSBrowser, WeTab Browser, Yahoo! Japan Browser, Yandex Browser, Yandex Browser Lite, Yaani Browser, Yolo Browser, xStand, Xiino, Xvast, Zetakey, Zvu

### List of detected browser engines:

WebKit, Blink, Trident, Text-based, Dillo, iCab, Elektra, Presto, Gecko, KHTML, NetFront, Edge, NetSurf, Servo, Goanna, EkiohFlow

### List of detected libraries:

aiohttp, Akka HTTP, Aria2, C++ REST SDK, curl, Embarcadero URI Client, Faraday, Go-http-client, Google HTTP Java Client, GRequests, Guzzle (PHP HTTP Client), gvfs, HTTPie, HTTP_Request2, Jakarta Commons HttpClient, Java, libdnf, LUA OpenResty NGINX, Mechanize, Mikrotik Fetch, Node Fetch, OkHttp, Perl, Perl REST::Client, Postman Desktop, Python Requests, Python urllib, ReactorNetty, REST Client for Ruby, RestSharp, ScalaJ HTTP, uclient-fetch, urlgrabber (yum), uTorrent, Wget, WinHttp WinHttpRequest, WWW-Mechanize

### List of detected media players:

Audacious, Banshee, Boxee, Clementine, Deezer, Downcast, FlyCast, Foobar2000, foobar2000, Google Podcasts, HTC Streaming Player, iTunes, Kodi, MediaMonkey, Miro, MPlayer, mpv, Music Player Daemon, NexPlayer, Nightingale, QuickTime, Songbird, SONOS, Sony Media Go, Stagefright, SubStream, VLC, Winamp, Windows Media Player, XBMC

### List of detected mobile apps:

1Password, 2tch, Adobe Creative Cloud, Adobe Synchronizer, Aha Radio 2, AIDA64, Alexa Media Player, AliExpress, AndroidDownloadManager, AntennaPod, Apple News, Avid Link, Background Intelligent Transfer Service, Baidu Box App, Battle.net, BB2C, BBC News, BetBull, BeyondPod, Bible KJV, Binance, BingWebApp, Bitsboard, Blackboard, Blitz, Blue Proxy, BlueStacks, Bookshelf, Bose Music, bPod, CastBox, Castro, Castro 2, CCleaner, CGN, ChMate, Chrome Update, Ciisaa, Clovia, COAF SMART Citizen, Copied, Cortana, Covenant Eyes, CPU-Z, CrosswalkApp, DevCasts, DeviantArt, DingTalk, Discord, DoggCatcher, douban App, Downcast, Dr. Watson, Edge Update, Emby Theater, Epic Games Launcher, ESET Remote Administrator, eToro, Evolve Podcast, Facebook, Facebook Audience Network, Facebook Groups, Facebook Messenger, Facebook Messenger Lite, FeedR, Flipboard App, Flipp, Gaana, Git, GitHub Desktop, GlobalProtect, GoNative, Google Fiber TV, Google Go, Google Play Newsstand, Google Plus, Google Podcasts, Google Search App, Google Tag Manager, HandBrake, HeyTapBrowser, Hik-Connect, HP Smart, iCatcher, Instacast, Instagram App, Instapaper, JaneStyle, Jungle Disk, KakaoTalk, Keeper Password Manager, Kik, Landis+Gyr AIM Browser, Line, LinkedIn, Logi Options+, MetaTrader, Microsoft Office $1, Microsoft Office Mobile, Microsoft OneDrive, Microsoft Outlook, My World, Naver, Netflix, NewsArticle App, Nextcloud, NPR One, NTV Mobil, NuMuKi Browser, Odnoklassniki, OfferUp, Opal Travel, Opera News, Overcast, Paint by Number, Pandora, Papers, Pic Collage, Pinterest, Player FM, Pocket Casts, Podbean, Podcast & Radio Addict, Podcaster, Podcast Republic, Podcasts, Podcat, Podcatcher Deluxe, Podimo, Podkicker$1, PowerShell, Procast, qBittorrent, QQMusic, QuickCast, RadioPublic, Rave Social, Razer Synapse, rekordbox, Roblox, RoboForm, Rocket Chat, RSSRadio, Samsung Magician, Shopee, ShowMe, Sina Weibo, Siri, Skyeng Teachers, Skype for Business, Slack, Snapchat, SogouSearch App, SPORT1, Streamlabs OBS, Strimio, Swoot, Teams, The Wall Street Journal, Theyub, Thunder, tieba, TikTok, TopBuzz, TuneIn Radio, TuneIn Radio Pro, TVirl, twinkle, Twitter, U-Cursos, Unibox, UnityPlayer, Viber, Visual Studio Code, Vuhuv, Wattpad, WebDAV, WeChat, WeChat Share Extension, WhatsApp, Whisper, WH Questions, Windows CryptoAPI, Windows Delivery Optimization, Windows Push Notification Services, Windows Update Agent, Wireshark, Wirtschafts Woche, Word Cookies!, Y8 Browser, Yahoo! Japan, YakYak, Yandex, Yelp Mobile, YouTube, Zalo, ZEPETO, Zoho Chat and *mobile apps using [AFNetworking](https://github.com/AFNetworking/AFNetworking)*

### List of detected PIMs (personal information manager):

Airmail, Barca, Basecamp, BathyScaphe, DAVdroid, Evernote, Franz, JaneView, Live5ch, Lotus Notes, MailBar, Mailbird, Mailspring, Microsoft Outlook, Notion, Outlook Express, Postbox, Raindrop.io, Rambox Pro, SeaMonkey, The Bat!, Thunderbird, Windows Mail

### List of detected feed readers:

Akregator, Apple PubSub, BashPodder, Breaker, FeedDemon, Feeddler RSS Reader, gPodder, JetBrains Omea Reader, Liferea, NetNewsWire, Newsbeuter, NewsBlur, NewsBlur Mobile App, PritTorrent, Pulp, QuiteRSS, ReadKit, Reeder, RSS Bandit, RSS Junkie, RSSOwl, Stringer

### List of brands with detected devices:

2E, 3GNET, 3GO, 3Q, 4Good, 4ife, 7 Mobile, 360, 8848, A1, Accent, Ace, Acer, Acteck, Adronix, Advan, Advance, AfriOne, AGM, AG Mobile, Ainol, Airness, AIRON, Airties, AIS, Aiuto, Aiwa, Akai, AKIRA, Alba, Alcatel, Alcor, ALDI NORD, ALDI SÜD, Alfawise, Aligator, AllCall, AllDocube, Allview, Allwinner, Altech UEC, Altice, altron, Amazon, AMCV, AMGOO, Amigoo, Amoi, Andowl, Anker, Anry, ANS, AOC, Aocos, AOpen, Aoson, AOYODKG, Apple, Archos, Arian Space, Ark, ArmPhone, Arnova, ARRIS, Artel, Artizlee, Asano, Asanzo, Ask, Aspera, Assistant, Astro, Asus, AT&T, Atom, Atvio, Audiovox, AURIS, Avenzo, AVH, Avvio, Awow, Axioo, Axxion, Azumi Mobile, BangOlufsen, Barnes & Noble, BBK, BB Mobile, BDF, Becker, Beeline, Beelink, Beetel, Bellphone, BenQ, BenQ-Siemens, Benzo, Beyond, Bezkam, BGH, Bigben, BIHEE, BilimLand, Billion, BioRugged, Bird, Bitel, Bitmore, Bkav, Black Bear, Black Fox, Blackview, Blaupunkt, Bleck, Blloc, Blow, Blu, Bluboo, Bluebird, Bluedot, Bluegood, Bluewave, BMAX, Bmobile, Bobarry, bogo, Boway, bq, Brandt, Bravis, BrightSign, Brondi, BS Mobile, Bundy, Bush, CAGI, Camfone, Canal Digital, Capitel, Captiva, Carrefour, Casio, Casper, Cat, Cavion, Celcus, Celkon, Cell-C, CellAllure, Cellution, Centric, CG Mobile, CGV, Changhong, Cherry Mobile, Chico Mobile, China Mobile, Chuwi, Claresta, Clarmin, Clementoni, Cloudfone, Cloudpad, Clout, CnM, Cobalt, Coby Kyros, Colors, Comio, Compal, Compaq, ComTrade Tesla, Concord, ConCorde, Condor, Connectce, Connex, Conquest, Contixo, Coolpad, CORN, Cosmote, Covia, Cowon, CreNova, Crescent, Cricket, Crius Mea, Crony, Crosscall, Cube, CUBOT, CVTE, Cyrus, Daewoo, Danew, Datalogic, Datamini, Datang, Datawind, Datsun, Dazen, Dbtel, Dell, Denver, Desay, DeWalt, DEXP, Dialog, Dicam, Digi, Digicel, DIGIFORS, Digihome, Digiland, Digma, DING DING, Ditecma, Diva, Divisat, DIXON, DMM, DNS, DoCoMo, Doffler, Dolamee, Doogee, Doopro, Doov, Dopod, Doro, Dragon Touch, Droxio, Dune HD, E-Boda, E-Ceros, E-tel, Eagle, Easypix, EBEST, Echo Mobiles, ECON, ECS, EE, Einstein, EKO, Eks Mobility, EKT, ELARI, Electroneum, ELECTRONIA, Elekta, Element, Elenberg, Elephone, Eltex, Energizer, Energy Sistem, Engel, Enot, Epik One, Epson, Ergo, Ericsson, Ericy, Erisson, Essential, Essentielb, eSTAR, Eton, eTouch, Etuline, Eurostar, Evercoss, Evertek, Evolio, Evolveo, EvroMedia, EWIS, EXCEED, Exmart, ExMobile, EXO, Explay, Extrem, Ezio, Ezze, F&U, F2 Mobile, F150, Facebook, Fairphone, Famoco, Fantec, FaRao Pro, FarEasTone, Fengxiang, Fero, FiGO, FiiO, FinePower, Finlux, FireFly Mobile, FISE, Fly, FLYCAT, FMT, FNB, FNF, Fondi, Fonos, FORME, Formuler, Forstar, Fortis, Fourel, Four Mobile, Foxconn, Freetel, Fuego, Fujitsu, G-TiDE, G-Touch, Galaxy Innovations, Garmin-Asus, Gateway, Gemini, General Mobile, Genesis, GEOFOX, Geotel, Geotex, GFive, Ghia, Ghong, Ghost, Gigabyte, Gigaset, Gini, Ginzzu, Gionee, Globex, Glofiish, GLX, GOCLEVER, Gocomma, GoGEN, Gol Mobile, Goly, Gome, GoMobile, Google, Goophone, Gooweel, Gradiente, Grape, Gree, Greentel, Gresso, Gretel, Grundig, Hafury, Haier, HannSpree, Hardkernel, Hasee, Helio, Hezire, Hi, Hi-Level, High Q, Highscreen, HiMax, Hipstreet, Hisense, Hitachi, Hitech, Hoffmann, Hometech, Homtom, Honeywell, Hoozo, Horizon, Hosin, Hotel, Hotwav, How, HP, HTC, Huadoo, Huawei, Humax, Hurricane, Huskee, Hyrican, Hyundai, Hyve, i-Cherry, i-Joy, i-mate, i-mobile, iBall, iBerry, iBrit, IconBIT, iDroid, iGet, iHunt, Ikea, IKI Mobile, iKoMo, IKU Mobile, iLA, iLife, iMan, iMars, IMO Mobile, Impression, INCAR, Inch, Inco, iNew, Infinix, InFocus, InfoKit, Inkti, InnJoo, Innos, Innostream, Inoi, INQ, Insignia, Intek, Intex, Invens, Inverto, Invin, iOcean, iOutdoor, iPro, iQ&T, IQM, Irbis, Iris, iRola, iRulu, iSWAG, IT, iTel, iTruck, IUNI, iVA, iView, iVooMi, ivvi, iZotron, JAY-Tech, Jeka, Jesy, JFone, Jiake, Jiayu, Jinga, Jivi, JKL, Jolla, Juniper Systems, Just5, JVC, K-Touch, Kaan, Kaiomy, Kalley, Kanji, Karbonn, Kata, KATV1, Kazam, Kazuna, KDDI, Kempler & Strauss, Keneksi, Kenxinda, Kiano, Kingsun, KINGZONE, Kiowa, Kivi, Klipad, Kocaso, Kodak, Kogan, Komu, Konka, Konrow, Koobee, Koolnee, Kooper, KOPO, Koridy, KREZ, KRIP, KRONO, Krüger&Matz, KT-Tech, KUBO, Kuliao, Kult, Kumai, Kurio, Kvant, Kyocera, Kyowon, Kzen, L-Max, LAIQ, Land Rover, Landvo, Lanix, Lark, Laurus, Lava, LCT, Leader Phone, Leagoo, Leben, Ledstar, LeEco, Leff, LEMFO, Lemhoov, Lenco, Lenovo, Leotec, Le Pan, Lephone, Lesia, Lexand, Lexibook, LG, Lifemaxx, Lingwin, Linnex, Linsar, Loewe, Logic, Logicom, Loview, LT Mobile, Lumigon, Lumus, Luna, Luxor, LYF, M-Horse, M-Tech, M.T.T., M4tel, MAC AUDIO, Macoox, Magnus, Majestic, Malata, Manhattan, Mann, Manta Multimedia, Mantra, Mara, Masstel, Matrix, Maxcom, Maximus, Maxtron, MAXVI, Maxwest, Maze, Maze Speed, MDC Store, meanIT, Mecer, Mecool, Mediacom, MediaTek, Medion, MEEG, MegaFon, Meitu, Meizu, Melrose, Memup, Metz, MEU, MicroMax, Microsoft, Minix, Mintt, Mio, Miray, Mito, Mitsubishi, Mitsui, MIVO, MIXC, MiXzo, MLLED, MLS, Mobicel, Mobiistar, Mobiola, Mobistel, MobiWire, Mobo, Modecom, Mofut, Motorola, Movic, mPhone, Mpman, MSI, MStar, MTC, MTN, Multilaser, MYFON, MyGica, Mymaga, MyPhone, Myria, Myros, Mystery, MyTab, MyWigo, Nabi, Naomi Phone, National, Navcity, Navitech, Navitel, Navon, NEC, Necnot, Neffos, Neomi, Neon IQ, Netgear, NeuImage, New Balance, Newgen, Newland, Newman, Newsday, NewsMy, NEXBOX, Nexian, NEXON, Nextbit, NextBook, NextTab, NGM, NG Optics, Nikon, Nintendo, NOA, Noain, Nobby, Noblex, NOBUX, Nokia, Nomi, Nomu, Nordmende, NorthTech, Nos, Nous, Novex, NuAns, Nubia, NUU Mobile, Nuvo, Nvidia, NYX Mobile, O+, O2, Oale, OASYS, Obi, Oculus, Odys, OINOM, Ok, Okapia, OKSI, OKWU, Onda, OnePlus, Onix, ONN, ONYX BOOX, OpelMobile, Openbox, OPPO, Opsson, Orange, Orbic, Ordissimo, Ouki, Oukitel, OUYA, Overmax, Ovvi, Owwo, Oysters, Oyyu, OzoneHD, P-UP, Packard Bell, Paladin, Palm, Panacom, Panasonic, Pantech, PCBOX, PCD, PCD Argentina, PEAQ, Pendoo, Pentagram, Perfeo, Phicomm, Philco, Philips, Phonemax, phoneOne, Pico, Pioneer, PiPO, Pixela, Pixelphone, Pixus, Planet Computers, Ployer, Plum, Pluzz, PocketBook, POCO, Point of View, Polar, PolarLine, Polaroid, PolyPad, Polytron, Pomp, Poppox, Positivo, Positivo BGH, PPTV, Premio, Prestigio, Primepad, Primux, Prixton, PROFiLO, Proline, ProScan, Protruly, ProVision, PULID, Q-Touch, Q.Bell, Qilive, QMobile, Qnet Mobile, Qtek, Quantum, Qubo, Quechua, Qumo, R-TV, Rakuten, Ramos, Raspberry, Ravoz, Razer, RCA Tablets, Reach, Readboy, Realme, RED, Reeder, REGAL, Revo, Rikomagic, RIM, Rinno, Ritmix, Ritzviva, Riviera, Rivo, Roadrover, Rokit, Roku, Rombica, Ross&Moor, Rover, RoverPad, RoyQueen, RT Project, RugGear, Ruio, Runbo, Ryte, S-TELL, Saba, Safaricom, Sagem, Salora, Samsung, Sanei, Sansui, Santin, Sanyo, Savio, SCBC, Schneider, Seatel, Seeken, SEG, Sega, Selenga, Selevision, Selfix, SEMP TCL, Sencor, Sendo, Senkatel, Senseit, Senwa, Seuic, SFR, Sharp, Shift Phones, Shtrikh-M, Shuttle, Sico, Siemens, Sigma, Silelis, Silent Circle, Simbans, Simply, Singtech, Siragon, Sirin labs, SKG, Sky, Skyworth, Smadl, Smailo, Smart, Smartab, SmartBook, SMARTEC, Smart Electronic, Smartfren, Smartisan, Smotreshka, Softbank, SOLE, SOLO, Solone, Sonim, SONOS, Sony, Sony Ericsson, Soundmax, Soyes, Spark, SPC, Spectralink, Spectrum, Spice, Sprint, SQOOL, Star, Starlight, Starmobile, Starway, Starwind, STF Mobile, STG Telecom, STK, Stonex, Storex, StrawBerry, STRONG, Stylo, Subor, Sugar, Sumvision, Sunny, Sunstech, SunVan, Sunvell, SUNWIND, SuperSonic, SuperTab, Supra, Suzuki, Swipe, SWISSMOBILITY, Swisstone, SWTV, Symphony, Syrox, T-Mobile, Taiga System, Takara, Tambo, Tanix, TB Touch, TCL, TD Systems, Technicolor, Technika, TechniSat, TechnoTrend, TechPad, Techwood, Teclast, Tecno Mobile, TEENO, Teknosa, Tele2, Telefunken, Telego, Telenor, Telia, Telit, Telpo, Tesco, Tesla, Tetratab, teXet, ThL, Thomson, Thuraya, TIANYU, Time2, Timovi, Tinai, Tinmo, TiPhone, TOKYO, Tolino, Tone, Tooky, Topelotek, Top House, Toplux, Topway, Torex, Toshiba, Touchmate, Transpeed, TrekStor, Trevi, Trident, Trifone, Trio, Tronsmart, True, True Slim, TTEC, Tunisie Telecom, Turbo, Turbo-X, TurboKids, TurboPad, TVC, TWM, Twoe, TWZ, Tymes, U.S. Cellular, Ugoos, Uhans, Uhappy, Ulefone, Umax, UMIDIGI, Unihertz, Unimax, Uniscope, UNIWA, Unknown, Unnecto, Unonu, Unowhy, Urovo, UTime, UTOK, UTStarcom, UZ Mobile, v-mobile, VAIO, Vargo, Vastking, VAVA, VC, Vega, Venso, Verico, Verizon, Vernee, Vertex, Vertu, Verykool, Vesta, Vestel, Vexia, VGO TEL, Videocon, Videoweb, ViewSonic, Vinga, Vinsoc, Vipro, Vision Touch, Vitelcom, Viumee, Vivax, Vivo, VIWA, Vizio, VK Mobile, VKworld, Vodacom, Vodafone, Vonino, Vontar, Vorago, Vorke, Voto, VOX, Voxtel, Voyo, Vsmart, Vsun, Vulcan, VVETIME, Walton, WE, Web TV, Weimei, WellcoM, WELLINGTON, Western Digital, Westpoint, Wexler, Wieppo, Wigor, Wiko, Wileyfox, Winds, Wink, Winmax, Winnovo, Wintouch, Wiseasy, WIWA, Wizz, Wolder, Wolfgang, Wolki, Wonu, Woo, Wortmann, Woxter, X-BO, X-TIGI, X-View, X.Vision, XGIMI, Xgody, Xiaolajiao, Xiaomi, Xion, Xolo, Xoro, Xshitou, Xtouch, Xtratech, Yandex, Yarvik, YASIN, Yes, Yezz, Yoka TV, Yota, Ytone, Yu, Yuandao, YUHO, Yuno, Yusun, Yxtel, Zaith, Zatec, Zebra, Zeemi, Zen, Zenek, Zentality, Zfiner, ZH&K, Zidoo, ZIFRO, Ziox, Zonda, Zopo, ZTE, Zuum, Zync, ZYQ, öwn

### List of detected bots:

360Spider, Aboundexbot, Acoon, Adbeat, AddThis.com, ADMantX, ADmantX Service Fetcher, Adsbot, aHrefs Bot, Alexa Crawler, Alexa Site Audit, Amazon Bot, Amazon Route53 Health Check, Amorank Spider, Analytics SEO Crawler, ApacheBench, Applebot, AppSignalBot, Arachni, archive.org bot, ArchiveBox, Ask Jeeves, AspiegelBot, Awario, Awario, Backlink-Check.de, BacklinkCrawler, Baidu Spider, Barkrowler, BazQux Reader, BDCbot, Better Uptime Bot, BingBot, BitlyBot, Blekkobot, BLEXBot Crawler, Bloglovin, Blogtrottr, BoardReader, BoardReader Blog Indexer, Bountii Bot, BrandVerity, Browsershots, BUbiNG, Buck, BuiltWith, Butterfly Robot, Bytespider, CareerBot, Castro 2, Catchpoint, CATExplorador, ccBot crawler, CensysInspect, Charlotte, Choosito, Cliqzbot, CloudFlare Always Online, CloudFlare AMP Fetcher, Cloudflare Diagnostics, Cocolyzebot, Collectd, colly, CommaFeed, Comscore, ContentKing, Cookiebot, CSS Certificate Spider, Cốc Cốc Bot, Datadog Agent, DataForSeoBot, datagnionbot, Datanyze, Dataprovider, DataXu, Daum, Dazoobot, Discobot, Discord Bot, Domain Re-Animator Bot, Domains Project, DotBot, Dotcom Monitor, DuckDuckGo Bot, Easou Spider, eCairn-Grabber, EMail Exractor, EmailWolf, Embedly, evc-batch, ExaBot, ExactSeek Crawler, Expanse, Ezooms, eZ Publish Link Validator, Facebook External Hit, Feedbin, FeedBurner, Feedly, Feedspot, Feed Wrangler, Fever, Findxbot, Flipboard, FreshRSS, GDNP, Generic Bot, Generic Bot, Genieo Web filter, Gigablast, Gigabot, Gluten Free Crawler, Gmail Image Proxy, Gobuster, Goo, Googlebot, Google Cloud Scheduler, Google Favicon, Google PageSpeed Insights, Google Partner Monitoring, Google Search Console, Google Stackdriver Monitoring, Google StoreBot, Google Structured Data Testing Tool, Gowikibot, Grammarly, Grapeshot, GTmetrix, Hatena Favicon, Heart Rails Capture, Heritrix, Heureka Feed, HTTPMon, httpx, HuaweiWebCatBot, HubPages, HubSpot, ICC-Crawler, ichiro, IDG/IT, IIS Site Analysis, Inktomi Slurp, inoreader, IP-Guide Crawler, IPS Agent, JungleKeyThumbnail, K6, Kaspersky, KomodiaBot, Kouio, l9tcpid, Larbin web crawler, LCC, Let's Encrypt Validation, Lighthouse, Linkdex Bot, LinkedIn Bot, LinkpadBot, LinkPreview, LTX71, LumtelBot, Lycos, Magpie-Crawler, MagpieRSS, Mail.Ru Bot, masscan, Mastodon Bot, Meanpath Bot, Mediatoolkit Bot, MegaIndex, MetaInspector, MetaJobBot, MicroAdBot, Mixrank Bot, MJ12 Bot, Mnogosearch, MojeekBot, Monitor.Us, MTRobot, Munin, MuscatFerret, Nagios check_http, NalezenCzBot, nbertaupete95, Neevabot, Netcraft Survey Bot, netEstate, NetLyzer FastProbe, NetResearchServer, NetSystemsResearch, Netvibes, NewsBlur, NewsGator, Nimbostratus Bot, NLCrawler, Nmap, Notify Ninja, Nutch-based Bot, Nuzzel, oBot, Octopus, Odnoklassniki Bot, Omgili bot, Openindex Spider, OpenLinkProfiler, OpenWebSpider, Orange Bot, Outbrain, PagePeeker, PageThing, PaperLiBot, parse.ly, Petal Bot, Phantomas, PHP Server Monitor, Picsearch bot, PingAdmin.Ru, Pingdom Bot, Pinterest, PiplBot, Plukkie, PocketParser, Pompos, PritTorrent, Project Resonance, PRTG Network Monitor, QuerySeekerSpider, Quora Bot, Quora Link Preview, Qwantify, Rainmeter, RamblerMail Image Proxy, Reddit Bot, Riddler, Robozilla, RocketMonitorBot, Rogerbot, ROI Hunter, RSSRadio Bot, Ryowl, SabsimBot, SafeDNSBot, Scooter, ScoutJet, Scrapy, Screaming Frog SEO Spider, ScreenerBot, Seekport, Semantic Scholar Bot, Semrush Bot, Sensika Bot, Sentry Bot, Seobility, SEOENGBot, SEOkicks, SEOkicks-Robot, seolyt, Seoscanners.net, Serendeputy Bot, serpstatbot, Server Density, Seznam Bot, Seznam Email Proxy, Seznam Zbozi.cz, ShopAlike, Shopify Partner, ShopWiki, SilverReader, SimplePie, SISTRIX Crawler, SISTRIX Optimizer, Site24x7 Website Monitoring, Siteimprove, SitemapParser-VIPnytt, SiteSucker, Sixy.ch, Skype URI Preview, Slackbot, SMTBot, Snapchat Proxy, Sogou Spider, Soso Spider, Sparkler, Speedy, Spinn3r, Spotify, Sprinklr, Sputnik Bot, Sputnik Favicon Bot, Sputnik Image Bot, sqlmap, SSL Labs, Startpagina Linkchecker, StatusCake, Superfeedr Bot, SurdotlyBot, Survey Bot, Tarmot Gezgin, TelegramBot, The Knowledge AI, theoldreader, ThinkChaos, TinEye Crawler, Tiny Tiny RSS, TLSProbe, TraceMyFile, Trendiction Bot, Turnitin, TurnitinBot, TweetedTimes Bot, Tweetmeme Bot, Twingly Recon, Twitterbot, UkrNet Mail Proxy, UniversalFeedParser, Uptimebot, Uptime Robot, URLAppendBot, Vagabondo, Velen Public Web Crawler, Vercel Bot, VeryHip, Visual Site Mapper Crawler, VK Share Button, W3C CSS Validator, W3C I18N Checker, W3C Link Checker, W3C Markup Validation Service, W3C MobileOK Checker, W3C Unified Validator, Wappalyzer, WebbCrawler, WebDataStats, Weborama, WebPageTest, WebSitePulse, WebThumbnail, WellKnownBot, WeSEE:Search, WeViKaBot, WhatCMS, WikiDo, Willow Internet Crawler, WooRank, WooRank, WordPress, Wotbox, XenForo, YaCy, Yahoo! Cache System, Yahoo! Japan BRW, Yahoo! Link Preview, Yahoo! Mail Proxy, Yahoo! Slurp, Yahoo Gemini, YaK, Yandex Bot, Yeti/Naverbot, Yottaa Site Monitor, Youdao Bot, Yourls, Yunyun Bot, Zao, Ze List, zgrab, Zookabot, ZoominfoBot, ZumBot

## Built with

* [Matomo device detector](https://github.com/matomo-org/device-detector) - A powerful device detection library.
* [node.js](https://nodejs.org/en/) - Cross-platform JavaScript run-time environment for executing JavaScript code server-side. 
* [TypeScript](https://www.typescriptlang.org/) - Typed superset of JavaScript that compiles to plain JavaScript.
* [Jest](https://facebook.github.io/jest/) - Delightful JavaScript Testing.

## Contributing

When contributing to this project, please first discuss the change you wish to make via issue, email, or any other method with the owners of this repository before making a change.

Update the [README.md](https://github.com/etienne-martin/device-detector-js/blob/master/README.md) with details of changes to the library.

Execute `yarn test` and update the [tests](https://github.com/etienne-martin/device-detector-js/tree/master/src/tests) if needed.

### How to update to a newer version of matomo?

This library needs to be updated when matomo releases a new version of their library. Here's how to proceed: 

1. Pull the master branch from this repo
2. Update the `https://github.com/matomo-org/device-detector#{version-number}` to the latest version of matomo device detector in the package.json
3. Run `yarn fixtures` to update to the latest fixtures. This will download new fixtures based on the version specified in the package.json
4. Run `yarn test` and update the library if some tests are failing
5. Open a PR

### Why do tests fail after downloading new fixtures?

When matomo releases a new version, they usually add support for new brands. [Those brands](https://github.com/matomo-org/device-detector/blob/1060530615c54796cc2045a030c7c605574060d2/Parser/Device/DeviceParserAbstract.php#L65) needs to be copied over to [this file](https://github.com/etienne-martin/device-detector-js/blob/master/src/tests/fixtures/brands.json).  

## Authors

* **Etienne Martin** - *Initial work* - [etiennemartin.ca](http://etiennemartin.ca/)
* **Alex Beauchemin** - *Contributor* - [linkedin.com/in/alexbeauchemin](https://www.linkedin.com/in/alexbeauchemin/)
* **Ayan Dey** - *Contributor* - [linkedin.com/in/dey-ayan](https://www.linkedin.com/in/iayandey)
* **Julien Maitrehenry** - *Contributor* - [linkedin.com/in/jmaitrehenry](https://www.linkedin.com/in/jmaitrehenry)

## License

This is a free/libre library under license LGPL v3 or later.
