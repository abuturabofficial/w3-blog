---
draft: false
title: "Search Engine Hacking: The Hacker's Guide to Advance Google Search"
imageNameKey: "google-dorking-demystified"
date: '2025-07-04T07:25:18+05:00'
description:
author: "AbuTurab"
image: 'google-dorking-demystified-cover.png'
tags: ['OSINT']
categories: ['Blog']
keywords: ['google dorking techniques', 'google power searching', 'google like a hacker' , 'beyond search box', 'google search like a pro', 'google dorking for good', 'advance google search for researcher and hackers', 'how to google like a power user', 'you are using google wrong', 'how to properly use power of google search']
lastmod: '2025-07-05T15:31:12+0500'
---

## What is Google Dorking?

Google Dorking is an **advance search technique**, which can find information about anything and everything from **the darkest and the deepest corners of the Internet**.

Google being the most used search engine, these techniques come-in handy to do Open Source Intelligence about your targets including **POI** (Point of Interest), **SOI** (Subject of Interest), **EOI** (Entity of Interest), or **NFI** (Need for Information).

Almost every Search Engine including Brave Search, DuckDuckGo, Startpage etc. support advance search operators. But the Google search have the most extensive support.

## Advance Search Operators

Following advance search operators can be used on almost all major search engines[^google-dorks-1] [^google-dorks-2] [^google-dorks-3].

> [!WARNING]
> I haven't tested all advance operators on every Search Engine. Most common operators will work fine, but more advance or nuance one will only work on Google.

### Switch to Verbatim Mode

If you search for a particular model of a laptop battery on Google search, it will not only include that model's battery but batteries for other models too.

To instruct Google to search only for specific terms given in the search box and avoid showing unnecessary results switch to **verbatim mode**.

![](google-dorking-demystified-5.png)

Click on `Tools` button on the top of the search page, and switch `All results` to `Verbatim`.

While using advance search operators, keep it on **verbatim** mode to get more accurate and precise results.

### The `" "` operator

This operator lets you search for the specific word inside the quotes, regardless of its spelling.

If you add other words beside the quoted word, google search must include quoted word in the results beside other words.

```
How to spell "mispell" in American English?
```

To get more specific results you quote the whole string, and the individual words inside the string too.

```
"How to spell "mispell" in American English?"
```

It's a bad example, as it may not return any results, but conveys the point well. 

![](google-dorking-demystified-4.png)

### The `+` and `-` operator

The `+` operator returns web pages containing the specified term either in the title or the body of the page.

```
The Office +'tv series'
```

It will search for pages that feature the term **The Office** referring to the TV series, not the Microsoft Office products.

To search the term **The Office**, we can exclude the web pages containing `Microsoft` in the title or the body of the page by using `-` operator.

```
The Office -microsoft
```

Using these operators, we can include or exclude specified words from title or body of the resultant webpages.



### The `site:` operator

It helps you include or exclude searches from specific websites.

```
Why iPhones are Sh*t! site:reddit.com
```


To exclude a site from the results

```
Why iPhones are Sh*t! -site:reddit.com
```

`-site:` will exclude the website mentioned after it. To include a website in the search results, you can use `+` operator like this `+site:`, but it's definitely redundant.

![](google-dorking-demystified.png)

To search on top-level domain only:

```
How to boil an egg? site:gov
```

To get results from all the subdomains of a particular top-level domain:

```
How to file tax returns? site:*.gov.pk
```

### The `inurl:` operator

If you want to search something specifically, inside the URLs of the particular website only. It can be paired with `site:` operator to only include/exclude inURL searches from that particular website.

```
site:microsoft.com -inurl:https
```

![](google-dorking-demystified-2.png)

### The `intitle:` and `allintitle` operators

To show only the results which have a single specified word in the title of the page and rest of the words anywhere:

```
intitle:max hard disk capacity
```

To search for different terms in the title separately:

```
allintitle:hard disk capacity minimum
```

The `allintitle` operator basically matches the terms like `OR` operator, if any of the mentioned terms have no results, they will still show if there are any results for the other mentioned terms.

| Operator      | Matches in Title    | Matches Elsewhere    | Use Case                                                     |
| ------------- | ------------------- | -------------------- | ------------------------------------------------------------ |
| `intitle:`    | Single word only    | Other words anywhere | When you want at least one word in title and others anywhere |
| `allintitle:` | All words specified | No                   | When you want all words to appear in the title               |

If you want to search for pages whose titles contain all the searched words use `allintitle`. If you want pages whose title contains first word only and others anywhere in the search result use `intitle`.

> [!INFO]
> There are `inanchor:` and `allinanchor:` operators which generally output the same results as `intitle` and `allintitle` combinations.

### The `*` wildcard operator

Asterisk acts as a wildcard, as a placeholder for one or more word (Accor. to **Thio Joe**[^thio-joe-youtube], It can hold 5 words). If you search for:

```
"how to make * at home"
```

Here `*` may act as a placeholder for pizza, candles etc.

### The `filetype:` operator

We can search for specific file types:

```
OSINT technique filetype:pdf
```

OR

```
OSINT technique ext:pdf
```

![](google-dorking-demystified-3.png)

> [!ERROR]
> Using `filetype:`/`ext:` operator with media file types like, **mp4, mp3, m4a, WebM** etc. wouldn't work, due to copyright issues.

### The `AROUND n` operator

n = Number of words to look AROUND

This operator returns the results for the left and right terms to specified numbers of words in between.

```
"brain" AROUND 20 "first computer virus"
```

This will look for the results which include word **brain** and **first computer virus** within 20 words apart.

![](google-dorking-demystified-7.png)

If you put `AROUND 0`, it means putting the left and right terms together without any word spacing.

### The `AND` and `OR` operators

If I search:

```
Cat Eggs
```

Google will try to look for the results containing both of these terms together.

But If I use `OR` operator between the two words, Google will show separate results for both **Cat** and **Eggs** terms.

```
Cat OR Eggs
```

![](google-dorking-demystified-6.png)

If you use `AND` operator:

```
Cat AND Eggs
```

It pretty much shows the same results if you use both of these words together without any advance search operator.


## Brave Search Operators

[Brave Search](https://search.brave.com) support all the [above-mentioned](#advance-search-operators) search operators.

But it also supports some **extra operators**[^brave-search-help]. I tested these on Google Search, but most of them either don’t work at all or don’t function as smoothly as they do in Brave Search.

The support for search operators is currently experimental in the Brave Search[^brave-search-help].

> [!TIP]
> While using quotes to include multiple words for an operator like `The Office inbody:"tv series"`, using `' '` will not work, and it shows an error. But if you use double quotes `" "`, the operator will apply properly.
> ![](google-dorking-demystified-8.png)

### The `inbody:` operator

It returns webpages containing the specified term in the body of the page.

Let's search:

```
DuckDuckGo inbody:"search operator"
```

![](google-dorking-demystified-9.png)

### The `inpage:` operator

It output webpages containing the specified term either in the title or in the body of the page.

```
inpage:"DuckDuckGo search operators"
```

It will only show the results where all these words are either present in the title or in the body of the page it displays. Likewise, it doesn't matter if they appear together or scattered throughout the webpage.

### The `lang:` or `language:` operator

If you want to search for pages in the language of your choice. The language code must be in the [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes), English as `en`, Urdu as `ur` and Arabic as `ar`.

> [!ERROR]
> This search operator truly depicts why **Brave Search Team** says, this functionality is experimental[^brave-search-help]. Occasionally it shows the results in the specified language, and another time it didn't work at all, and it provides all kinds of nonsense hits.

### The `loc:` or `location:` operator

It returns webpages from the specified country or region. The country code must be in [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements) format.

> [!ERROR]
> The operator is poorly supported. And almost never works as originally intended.

### The `NOT` operator

Brave Search support `AND` and `OR` logical operators. But `NOT` operator is a unique search operator supported only by Brave Search.

According to help page, you can use it like:

```
brave search NOT site:brave.com
```

It will exclude all the brave.com subdomains too.

> [!TIP]
> To achieve similar behavior on Google:
> ``` {linenos=false}
> brave search -site:brave.com
> ```
> It excludes subdomains too. While doing something like `-site:*.brave.com` doesn't work.

### The `!bang` support

You can directly search on websites from your Brave search homepage using `!bangs`[^brave-search-bangs]

```
!yt systemd is evil!
```

You will be directed to YouTube page with search results for term **systemd is evil!** 🙂.

[^google-dorks-1]: "Refine Google searches" — Google Search Help. [Learn more](https://support.google.com/websearch/answer/2466433?hl=en)
[^brave-search-help]: "Search Operators" — Brave Search Help. [Read more](https://search.brave.com/help/operators)
[^google-dorks-2]: Joshua Hardwick, "Google Search Operators: The Complete List (44 Advanced Operators)", (2024). [Read more](https://web.archive.org/web/20250530115310/https://ahrefs.com/blog/google-advanced-search-operators/)
[^google-dorks-3]: Chima Mmeje, "62 Advanced Google Search Operators, Use Cases & Cheatsheet", (2025). [Blog post](https://moz.com/learn/seo/search-operators)
[^thio-joe-youtube]: Thio Joe, "You're Using Google WRONG — Do This Instead", (2025). [Watch on YouTube](https://www.youtube.com/watch?v=M3bduu2GGVU)
[^cover-photo]: Cover Photo by [Freepik](https://www.freepik.com/free-photo/portrait-hacker-with-mask_4473969.htm#fromView=search&page=1&position=26&uuid=1dcd8f82-595e-4d15-a3e7-896fdaf5d752&query=hacker+google+search).
[^brave-search-bangs]: "What !bangs can I use in Brave Search?" - Brave Help Center. [See more](https://support.brave.app/hc/en-us/articles/4410152384781-What-bangs-can-I-use-in-Brave-Search)