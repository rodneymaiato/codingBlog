---
title: "How to Add Google Analytics to a Hugo Site"
date: 2023-03-18T09:22:25-07:00
author: Rodney Maiato
draft: false 
tags: ["google analytics","hugo"]
---

Assuming you've already set up a Google Analytics account, here's how you add it to your Hugo site. (If not then, see this post for instructions.)

Setting up Google Analytics in your Hugo site is extremely simple.

- open your `config.yaml` or `config.toml` file located in the root of your Hugo project folder.

```shellscript
example/
├── archetypes/
│   └── default.md
├── assets/
├── content/
├── data/
├── layouts/
├── public/
├── static/
├── themes/
└── config.toml <-- open and add "googleAnalytics: G-MEASUREMENT_ID"

```
- add the following line of code to your config file with no indentation:
```shellscript
googleAnalytics: G-MEASUREMENT_ID
```

- Replace `G-MEASUREMENT_ID` with the google tag ID found in your google analytics account for that site.
- use the appropriate Google Analytics template that Hugo provides. You're likely going to need the Google Analytics 4 template. You don't need to create a template. Hugo has several internal templates. All you need to do is add the code below immediately after the opening head tag.

```shellscript
{{ template "_internal/google_analytics.html" . }}
```
- Save the changes.
- If you use a hosting platform like Netlify, commit your changes to Github and your site will be updated.

Google will begin the process of tracking your site. When you log into your Google Analytics account, you will see a message indicating that no data has not yet been collected because your site is too new. And, in a day or two, a message that says, your data collection is active and that it may take up to 24 hours to appear in your Analytics account.

![google analytics message](/google_analytics_setup.png)

Setting up Google Analytics should take less than 5 minutes, thanks to Hugo.

