---
layout: article
title: "Plausible: GDPR, CCPA and cookie law compliant site analytics"
description: Plausible provides cookie-less web analytics without collecting
  personal data and while respecting the privacy of website visitors. This is
  our data policy.
permalink: /data-policy
---
Even though the purpose of [Plausible Analytics](https://plausible.io) is to track the usage of a website, this can still be done without collecting any personal data or personally identifiable information (PII), without using cookies and while respecting the privacy of the website visitors.

Here's a closer look at our data policy, the information that we do collect, what we use it for and steps we've taken to comply with the cookie law and the privacy regulations such as the GDPR, CCPA and PECR.

## First thing first: What we collect and what we use it for

The goal of Plausible is to track overall trends in your website traffic, it is not to track individual visitors. We don’t collect or store any personal or identifiable data. All of the data that we do collect is aggregated data only and it has no personal information.

We measure only the most essential data points and nothing else. All the metrics we do collect fit on one single page. Here is the complete list of what we collect and store about your website visitors:

| Data point | Example | Comment |
|---|---|---|---|---|
| **Page URL** | _https://yoursite.com/pricing_ | We track the page URL of each page view on your website. We use this to show you which pages have been viewed and how many times a particular page has been viewed. <br /><br />The hostname and path are collected. Query parameters are discarded, except for these special query parameters: `ref=`, `source=` and `utm_source=`. |
| **HTTP Referer** | _https://facebook.com_ | We use the referrer string to show you the number of visitors referred to your website from links on other sites. |
| **Browser** | _Chrome_ | We use this to show you what browsers people use when visiting your website. This is derived from the User-Agent HTTP header. The full User-Agent is discarded. |
| **Operating system** | _macOS_ | We use this to show you what operating systems people use when visiting your website. We only show the brand of the operating system and don't include the version number or any other details. This is derived from the User-Agent HTTP header. The full User-Agent is discarded. |
| **Device type**  | _Desktop_ | We use this to show you what devices people use when visiting your website. This is derived from window.innerWidth. The actual width of the browser in pixels is discarded. |
| **Visitor Country**  | _United Kingdom_ | We look up the visitor's country using their IP address. We do not track anything more granular than the country of origin and the IP address of the visitor is discarded. We never store IP addresses in our database or logs. |

## How we count unique users without cookies

Counting unique visitors is an integral part of web analytics. Known methods include:
1. Storing a cookie with random identifier on the visitor's device
2. Counting unique IP addresses (often coupled with User-Agent)
3. Browser fingerprinting
4. Abusing the browser cache e.g. [Etag tracking](https://www.futurehosting.com/blog/etags-allow-tracking-without-cookies/)

Each method has its problems and they are all covered by different privacy laws. Plausible attempts to strike a reasonable balance between de-duplicating pageviews and staying respectful of visitor privacy. We do not attempt to generate a device-persistent identifier because they are considered personal data under GDPR.

Instead, we generate a daily changing identifier using the visitor's IP address and User Agent. To anonymize these datapoints, we run them through a hash function with a rotating salt.

```
hash(daily_salt + website_domain + ip_address + user_agent)
```

This generates a random string of letters and numbers that is used to calculate unique visitor numbers for the day. Old salts are deleted to avoid the possibility of linking visitor information from one day to the next. Forgetting used salts also removes the possibility of the original IP addresses being revealed in a brute-force attack.

In our testing, using IP addresses to count visitors is remarkably accurate when compared to using a cookie. In some cases it might even be more accurate than using a cookie because some visitors block cookies altogether.

The biggest limitation with this approach is that we cannot do good retention analysis with Plausible. We cannot show stats like _New vs Returning visitors_ because they rely on having a persistent user identifier.

<small>_Disclaimer:_ We're not lawyers. The information in this post is our view on things and it's here to help give you an introduction to the different privacy regulations and how Plausible is built to help you comply with them. We encourage you to discuss specific issues with your lawyer if you have any concerns.</small>

## Data ownership of your web analytics

By using Plausible, you keep 100% ownership of your website data. Although when using our hosted service, your site analytics are stored on our server in the cloud, you remain completely in control of your site data and you fully own all of your data too:

* Your website data is not shared with advertising companies or any other companies in general.
* Your website data is not sent to any third-parties at all.
* Your website data is not mined and harvested for personal and behavioral trends.
* Your website data is not monetized.

## Why should I trust you?

Plausible is a fully [open-source website analytics tool](https://plausible.io/open-source-website-analytics). Our source code is available and accessible [on GitHub](https://github.com/plausible/analytics/) so you can read it and review it to ensure our code does what we say.

## GDPR, CCPA and PECR compliant web analytics

By using Plausible, you don't need to have any GDPR, CCPA or PECR prompts and you don't need a complex privacy policy about your use of analytics and cookies. With Plausible, you are not tracking any personal data after all. Your visitors can enjoy your site without any annoyances and distractions.

You can [sign up for a 30-day free trial](https://plausible.io/register) and explore our privacy-friendly and GDPR, CCPA and PECR compliant site analytics. You don't need to remove your current analytics provider either until you've tested Plausible and figured out if you like our product.
