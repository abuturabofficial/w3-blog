---
draft: false
title: "Google Dorking: The Hacker's Guide to Advance Google Search"
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

Following advance search operators can be used on almost all major search engines.

> [!WARNING]
> I haven't tested all advance operators on every Search Engine. Most common operators will work fine, but more advance or nuance one will only work on Google.

### Switch to Verbatim Mode

If you search for a particular model of a laptop battery on Google search, it will not only include that model's battery but batteries for other models too.

To instruct Google to search only for specific terms given in the search box and avoid showing unnecessary results switch to **verbatim mode**.

![](google-dorking-demystified-5.png)

Click on `Tools` button on the top of the search page, and switch `All results` to `Verbatim`.

While using advance search operators, keep it on **verbatim** mode to get more accurate and precise results.

### `" "` Operator

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

### `site:` Operator

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

### `inurl:` Operator

If you want to search something specifically, inside the URLs of the particular website only. It can be paired with `site:` operator to only include/exclude inURL searches from that particular website.

```
site:microsoft.com -inurl:https
```

![](google-dorking-demystified-2.png)

### `intitle:` and `allintitle` operators

To show only the results which have a signle specified word in the title of the page and rest of the words anywhere:

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

### `*` Wildcard operator

Asterisk acts as a wildcard, as a placeholder for one or more word (Accor. **Thio Joe**, It can hold 5 words). If you search for:

```
"how to make * at home"
```

Here `*` may act as a placeholder for pizza, candles etc.

### `filetype:` Operator

We can search for specific file types:

```
OSINT technique filetype:pdf
```

OR

```
OSINT technique ext:pdf
```

![](google-dorking-demystified-3.png)

> [!TIP]
> Using `filetype:`/`ext:` operator with media file types like, **mp4, mp3, m4a, WebM** etc. wouldn't work, due to copyright issues.

### `AROUND n` Operator

n = Number of words to look AROUND

This operator returns the results for the left and right terms to specified numbers of words in between.

```
"brain" AROUND 20 "first computer virus"
```

This will look for the results which include word **brain** and **first computer virus** within 20 words apart.

![](google-dorking-demystified-7.png)

If you put `AROUND 0`, it means putting the left and right terms together without any word spacing.

### `AND` and `OR` Operators

If I search:

```
Cat Eggs
```

Google will try to look for the results containing both of these terms together.

But If I use `OR` operator between the two words, google will show separate results for both **Cat** and **Eggs** terms.

```
Cat OR Eggs
```

![](google-dorking-demystified-6.png)

If you use `AND` operator:

```
Cat AND Eggs
```

It pretty much shows the same results if you use both of these words together without any advance search operator.


---
## References

- "Refine Google searches" — Google Search Help. [Learn more](https://support.google.com/websearch/answer/2466433?hl=en)
- "Search Operators" — Brave Search Help. [Read more](https://search.brave.com/help/operators)
- Joshua Hardwick, "Google Search Operators: The Complete List (44 Advanced Operators)", (2024). [Read more](https://web.archive.org/web/20250530115310/https://ahrefs.com/blog/google-advanced-search-operators/)
- Chima Mmeje, "62 Advanced Google Search Operators, Use Cases & Cheatsheet", (2025). [Blog post](https://moz.com/learn/seo/search-operators)
- Thio Joe, "You're Using Google WRONG — Do This Instead", (2025). [Watch on YouTube](https://www.youtube.com/watch?v=M3bduu2GGVU)
- Cover Photo by [Freepik](https://www.freepik.com/free-photo/portrait-hacker-with-mask_4473969.htm#fromView=search&page=1&position=26&uuid=1dcd8f82-595e-4d15-a3e7-896fdaf5d752&query=hacker+google+search).