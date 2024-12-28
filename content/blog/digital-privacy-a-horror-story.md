---
author: Abuturab
title: "Digital Privacy in Web 2.0: A Modern Horror Story"
date: 2023-12-05 10:27:00 +0500
tags: ["Blogs", "Privacy", "Digital Freedom"]
cover:
    image: "/blog/digital-privacy-a-horror-story/2023-12-05-digital-privacy-a-horror-story.webp"
    alt: "Rows of gibberish text are falling from above"
comments: true
---

The famous phrase:
> “If you're not paying for it, you become the product.[^1]”

It signifies the long-lost battle of digital privacy[^5]. We gave up our privacy when we signed up for these free-to-use services, thinking that they won't betray us. But they did, and did so bad that there is no way to escape from them (completely), unless we altogether leave the online world and start relying on the caveman's method of communication and access to the information.

Is privacy totally lost, or is this blog title merely a clickbait? I won't claim it's a complete clickbait, but rather a wake-up call for those who perceive their governments, internet providers, and other e-service providers as entities that won't harm them at all. We can't revert to the pre-internet era, given our extensive involvement and reliance on online connectivity, encompassing banking, schooling, shopping, and social interactions. However, we can make a conscious effort to minimize our online footprint and, whenever possible, refrain from contributing to the colossal data-collection machinery.

> [!TIP]
> How do I reduce my digital footprint? It is a topic of some other blog, but in the references section on the bottom, I will share some useful links[^3] to help kick-start your Internet Privacy journey.

## Web 2.0: A Privacy Nightmare!

The advent of Web 2.0 was based on the generous free tiers offered to the consumers. But that freebie came at the cost of our digital life being exposed to those service providers. What we search on Google, what we watch on YouTube and TikTok, and how we interact with our social circle over on Facebook and Instagram, every step of ours is recorded. Then, with the help of complex algorithms, is used to manipulate us through their ads.

But the story doesn't end with the ads, our personal data is sold to the highest paying **3<sup>rd</sup> Party** bidders to make more profit off of it. Unfortunately, the story also doesn't end there, those e-vultures follow us around the web, keep hoarding more and more data about our online activities, and thus generating more profit by selling it.

This collected data can be used to manipulate our thoughts and ideas in a particular direction as intended by the highest bidder. Facebook–Cambridge Analytica data scandal[^2] is a good example of how much dangerous a data collection can be, when used as a weapon of mass manipulation for specialized gains.

## Data Privacy and Its Impact on Mental Health

One alarming consequence of pervasive data collection is its detrimental effect on mental health. Social media platforms such as YouTube, Facebook, Twitter, TikTok, and others, along with major content-serving websites and games, leverage behavioral analysis[^4] and intricate data analytics to keep users engaged.

Consider the deliberate design choices: when you open YouTube, the default landing page is the Home page rather than your subscription feed. This design tactic encourages prolonged usage by suggesting videos based on individual usage patterns. Similarly, the recommended videos section on the side of video playback further extends your stay on the platform.

> [!DANGER]
> Have you ever questioned why your Facebook newsfeed seems endless, despite having only a handful of friends? Or why the YouTube Home Page seems infinite? The continuous scrolling on TikTok, Reels, YT Shorts, and other platforms might make you wonder, why? Additionally, games persistently prompt you with new rewards or artificially limited-time offers on in-game assets.

Moreover, the rise of short-form content on platforms like TikTok, Reels, Shorts, etc., is impacting our attention spans[^22]. These platforms, based on your usage patterns, curate and serve you more short-form content, contributing to a continuous cycle of data collection. Users unwittingly find themselves caught in an endless loop of feedback and response.

Consider this: the rapid succession of short, attention-grabbing videos conditions our minds to seek instant gratification. As a result, our ability to engage with longer, more complex content diminishes. This not only affects our attention spans but also shapes the type of content these platforms prioritize for us.

For instance, the addictive nature of endlessly scrolling through bite-sized videos on TikTok or Reels keeps users glued to their screens, fostering a habit of consuming information in bite-sized portions. This, in turn, fuels the platforms' appetite for more data, perpetuating the cycle.

In essence, the design of these platforms, fueled by data-driven insights, not only influences what we see but also molds our consumption habits, subtly steering us towards content that aligns with their data-collection objectives.

> [!INFO]
> Some researchers[^23] argue against the idea of decreasing attention span, link it to the increasing work load and the adaptation of multitasking in this digital era.

## Communication Privacy

Even our communication privacy is largely at risk due to widespread use of WhatsApp, traditional SMS, iMessage, etc. Although WhatsApp, iMessage[^9] and few others proprietary messaging platforms claim to offer End-to-End Encryption (E2EE), where the sender and receiver are the only ones that can read each other messages. But due to their closed nature, we can't independently verify their claims. Are we comfortable to give those platform access to our chats with our loved ones? Are we willing to see ads based on our chats with our friends and family? I think nobody in their right mind will ever allow this.

> [!WARNING]
> Using unencrypted methods like plain SMS, and carrier calls, are far worse than using WhatsApp or other E2EE proprietary instant messengers.

> [!INFO]
> WhatsApp itself doesn't run any ads, but they do share metadata with their parent company, Meta (formerly Facebook). You will see some flowery language about it, like data sharing for enhanced user experience and improving the infrastructure etc… 

> [!TIP]
> iMessage cloud backups will only use E2EE, when you enable “Advanced Data Protection for iCloud[^8]”.

### Telegram: It's not as private as you think!

Contrary to the widespread notion that Telegram is more private, it's by default even less private than WhatsApp due to no by-default E2EE. Telegram only uses E2EE when you use secret chat's feature. There is no E2EE in group chats, or default regular chats. Telegram uses their own encryption model instead of industry standard ones.

There are many other flaws[^6][^7] which will need the blog post of their own. When average users learn about privacy and see telegram mentioned as one of the ways to privately communicate with others, they don't bother to look further and start using it as is, thinking End-to-End Encryption is there by default.

### Email: A Risk!

Email is another threat to our digital privacy, due to the sole nature of how in-secure an email protocol by-default is. It was designed to quickly and effectively deliver information, security of this sent information wasn't the goal at that time.

Likes of Gmail, Outlook etc., doesn't protect you with E2EE, instead use TLS (in-transit encryption of your emails, in which somebody listening on your network traffic or your ISP won't be able to make sense of them) to protect in-transit snooping of the emails. But hold the encryption keys themselves, in case of any government subpoena, or Server side hack, your private emails will be at the risk of exposure.

Google and Microsoft being the encryption keyholders, they can read your emails, and serve you personalized ads based off them. There are other email provides like [ProtonMail](https://proton.me/mail), [Tuta](https://tuta.com/) (formerly Tutanota) and others, which provide different ways to encrypt your Email communications, but those have flaws[^11][^12] too, due to the constraints of being able to send email to non-encrypted Email providers, or complex nature of using PGP encryption for your emails, and no encryption for Email headers etc.

### ProtonMail and Tuta: Concerns about Encrypted Emails

ProtonMail and Tuta are some of the most popular encrypted email providers, but there is a catch. When a layman learns about the importance of privacy and security, he tends to migrate his Email to some privacy respecting EE2E email providers. Little does he know that, despite using those vendors, he is still at risk (arguably even more) of exposing his private information to the 3rd parties.

As these email providers only offer E2EE when sender and receiver, both are using the same provider (Proton or Tuta). For example, if you send an email from ProtonMail to Gmail or Outlook, though Proton will not able to see the content of your emails. But Gmail or Outlook having no compatible E2EE will easily be able to decipher your message.

Tuta E2EE method allows them to encrypt metadata like subject field, but ProtonMail due to S/MIME and PGP compatibility doesn't encrypt your email subject field. Both providers do provide password-protected emails for non Proton/Tuta email exchanges, but sharing those passwords with the receiver safely would need some other E2EE service.

> [!TIP]
> Tuta[^20] provides E2EE based on [AES-128](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) and [RSA-2048](https://en.wikipedia.org/wiki/RSA_(cryptosystem)). In contrast, ProtonMail[^21] uses [OpenGPG](https://www.openpgp.org/) and also supports compatibility with other email providers that use [PGP](https://en.wikipedia.org/wiki/GNU_Privacy_Guard) and [S/MIME](https://en.wikipedia.org/wiki/S/MIME).

## Privacy, Security, and Anonymity

We often confuse privacy, security, and anonymity. Privacy means being the sole owner of your data, with the assurance that it won't fall into the wrong hands. Security is when the concerned party proves they are what they claim to be. Anonymity involves surfing or using the web without revealing personally identifiable information (PII), though true anonymity is rare even with a TOR Browser.

What we aim for is a balance of all three. Firstly, we seek privacy by minimizing data collection to what's essential for the desired service. Secondly, we desire the security of both our data and confirmation of the legitimacy of the service provider. Lastly, we request anonymity for our collected data, safeguarding it from 3rd parties and other users of the same service.

## Misconceptions about Open-Source Software

When we hear the word open source, we tend to associate it with a high amount of trust and confidence. Though it's generally true that open source software in its core can't harm you, but there are few pointers we need to keep in mind when using open source:
- The software has how many users?
  - More number of users ideally means more eyes on the code base, and the bugs and security flaws will be discovered quickly.
- If you're technical enough, you should yourself look at the code at each major release, to make sure it doesn't include anything that is against the free software philosophy.
- When a software is maintained by a hobbyist/independent developer, there are chances that their goals about that software might change with time, so be on a look-out for any maintainer and philosophy changes.
- A developer may [sell](https://www.androidauthority.com/simple-mobile-tools-acquisition-3391041/) his project without any prior notice (unethically) to a person or entity, which isn't privacy respecting at all.
- A developer may turn [evil](https://www.zdnet.com/article/some-developers-are-fouling-up-open-source-software/) to perceive their political biases or agenda.
- Someone might try to sabotage a free software by introducing an [intentional flaw](https://www.zdnet.com/article/greg-kroah-hartman-bans-university-of-minnesota-from-linux-development-for-deliberately-buggy-patches/).
- All in all, you should be careful not when using a proprietary software (even more, IMHO) but also for free software. Don't just trust the developer or maintainer, see for yourself, or look out what other people who have used/using this software have to say about it.

> [!WARNING]
> I'm not trying to demerit the open source in any sense, the only thing I want is people should remain careful in all scenarios instead of just relying on promises of not turning evil.

## Growing Governments' Intervention

The current landscape of online privacy and security is facing challenges due to increased surveillance[^13] and governmental opposition[^14][^17][^18] towards data encryption and privacy. Notably, governments, including the EU and UK, have made recent attempts[^15][^16] to compromise privacy under the guise of counterterrorism, crime prevention, and child protection. While the EU's GDPR is renowned for safeguarding individual privacy, there are concerns about a shift in approach with initiatives like the Chat Control Bill.

> [!INFO]
> There are so many examples when governments tried to weaken the End-to-End Encryption (EE2E), overall privacy and security for the masses. If I start listing all, the whole blog post will be needed only for those references.

These legislative efforts aim to implement unproven methods to scan end-to-end encrypted communications and data without infringing on individuals' right to privacy. <mark style="background: #BBFABBA6;">Currently, security and privacy advocates have successfully resisted the erosion of privacy rights, but the duration of their success in preventing the compromise of E2EE remains uncertain</mark>.

I see arguments against E2EE as comparable to installing cameras in everyone's homes in the name of national security and child protection. The idea that everyone could pose a threat doesn't justify intrusive surveillance. Governments and law enforcement should prioritize legitimate efforts rather than resorting to injecting spyware into devices. Both actions are not only wrong, but also unlawful, violating the fundamental human right to personal privacy. Intruding into personal devices is, in my opinion, even more invasive, as breaking E2EE opens the door for governments and potential threat actors to hack into ideas and manipulate opinions which is more dangerous than physical surveillance.

## Concluding Thoughts: Navigating the Digital Privacy Maze

As we navigate the intricate landscape of digital privacy, it becomes evident that the foundations of Web 2.0 were laid upon the bedrock of data collection for profit. Simultaneously, governments wield legislative instruments that can compromise our privacy[^19]. In this alarming scenario, our role in safeguarding our digital lives cannot be overstated.

To fortify your digital presence and protect your privacy[^10]:

- **Mindful Engagement:** Deliberately choose services that prioritize user privacy. Be vigilant about the information you share online and the data collected by the platforms you use.

- **Migration to Privacy-First Platforms:** Explore alternative platforms committed to respecting user privacy. Remember, privacy sometimes comes at a cost; consider investing in services aligned with your privacy requirements.

- **Empowerment Through Settings:** If migrating isn't feasible, empower yourself by optimizing the **privacy and security settings** of the services you currently use. Minimize data collection wherever possible.

- **Deconstructing Policies:** Unravel the privacy policies of major service providers. Understand how they leverage your data. Knowledge is power, and being informed about data usage practices is a crucial step in digital self-defense.

- **Stay Informed:** The data mining industry is dynamic, with practices evolving constantly. Keep yourself up-to-date of these changes to stay one step ahead.

In this era of data-driven economies and legislative scrutiny, the duty lies on us to be proactive custodians of our digital privacy. Through informed choices and constant vigilance, we can construct a shield against the creeping threats to our personal space in the digital realm.

## References

[^1]: Dive into S. Goodson's insights on "The Impact of Social Media on Society" in Forbes' piece from March 5, 2012. [Explore More](https://www.forbes.com/sites/marketshare/2012/03/05/if-youre-not-paying-for-it-you-become-the-product/)
[^2]: Unravel the complexities of the "Facebook–Cambridge Analytica data scandal" on Wikipedia. [Get the Scoop](https://en.wikipedia.org/wiki/Facebook%E2%80%93Cambridge_Analytica_data_scandal)
[^3]: Discover Privacy Guides' recommendations for "Privacy Respecting Alternatives for Common Services/Tools." [See Recommendations](https://www.privacyguides.org/en/tools/)
[^4]: Delve into M. Busby's exploration of "How Social Media Creates Psychological Cravings" in The Guardian, May 8, 2018. [Read the Full Article](https://www.theguardian.com/technology/2018/may/08/social-media-copies-gambling-methods-to-create-psychological-cravings)
[^5]: Explore the realm of "Digital Privacy" on Wikipedia. [Learn More](https://en.wikipedia.org/wiki/Digital_privacy)
[^6]: R. Mimoun uncovers "Insecure by Design: 7 Reasons to Question Telegram's Privacy" on HackerNoon. [Get the Details](https://hackernoon.com/7-reason-why-telegram-is-insecure-by-design-but-millions-still-flock-to-it-ignoring-privacy-concerns-qq1o344c)
[^7]: Wired dishes out insights on "Fleeing WhatsApp for Better Privacy? Don't Turn to Telegram." [Read the Article](https://www.wired.com/story/telegram-encryption-whatsapp-settings/)
[^8]: Safeguard your information with Apple's "Advanced Data Protection for iCloud." [Official Documentation](https://support.apple.com/en-us/102651)
[^9]: How-To Geek breaks down why "Apple’s iMessage Is Secure… Unless You Have iCloud Enabled." [Check it Out](https://www.howtogeek.com/710509/apples-imessage-is-secure...-unless-you-have-icloud-enabled/)
[^10]: Dive deep into "Why Privacy Matter" debate over on Privacy Guides [Read More](https://www.privacyguides.org/en/basics/why-privacy-matters/)
[^11]: "Read more about Encrypted Email and Security Nihilism", May 18, 2018. [Check Out](https://www.aclu.org/news/privacy-technology/encrypted-email-and-security-nihilism) (Some parts of this article maybe outdated)
[^12]: Educate yourself about 7 Drawbacks of Encrypted Email, May 22, 2023. [Read More](https://www.consensus.com/blog/7-drawbacks-of-encrypted-email/)
[^13]: Dive into K. Zetter's piece on "How Edward Snowden Leaked the NSA's Dirty Surveillance Business", May 13, 2014. [Learn More](https://www.wired.com/2014/05/greenwald-no-place-to-hide/)
[^14]: "Why FBI don't like the encryption?" [Read FBI's Stance](https://www.fbi.gov/about/faqs/what-concerns-do-the-fbi-and-the-law-enforcement-communities-have-regarding-the-growing-use-of-encryption-products-by-the-public-both-domestically-and-abroad)
[^15]: "UK Government tried to undermine the privacy by breaking the end-to-end encryption", September 6, 2023. [Learn More](https://techcrunch.com/2023/09/06/osb-encryption-scanning-feasibility/)
[^16]: "EU attempt at introducing the Chat Control Bill to introduce client-side scanning of EE2E messages", September 14, 2023. [Educate yourself](https://proton.me/blog/eu-chat-control)
[^17]: "International joint statement to undermine the EE2E in the name of Public Safety", October 11, 2020. [Check it Out](https://www.justice.gov/opa/pr/international-statement-end-end-encryption-and-public-safety)
[^18]: A paper on "Encryption: A Tradeoff Between User Privacy and National Security", July 15, 2021. [Explore More](https://www.american.edu/sis/centers/security-technology/encryption.cfm)
[^19]: A piece on "The government wants access to your encrypted messages — we must act now to defend our right to privacy", July 6, 2023. [Read More](https://thehill.com/opinion/technology/4081907-the-government-wants-access-to-your-encrypted-messages-we-must-act-now-to-defend-our-right-to-privacy/)
[^20]: An FAQ about Tuta's Encryption Methodology, [Read More](https://tuta.com/support/#algorithms)
[^21]: A Explanation given by Proton about their E2EE, December 30, 2021. [Read the Blog](https://proton.me/support/proton-mail-encryption-explained)
[^22]: J. Zaveri piece on "TikTok and the Death of the Attention Span", May 23, 2023. [Read the Full Article](https://theoxfordblue.co.uk/tiktok-and-the-death-of-the-attention-span/)
[^23]: Subramanian, Kalpathy Ramaiyer. "Myth and mystery of shrinking attention span." _ResearchGate.net_ 5.1 (2018): 1-6. [Read the Paper](https://www.researchgate.net/publication/327367023_Myth_and_Mystery_of_Shrinking_Attention_Span)
