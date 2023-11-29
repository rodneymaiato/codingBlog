---
title: "How to Setup the Official Hugo Module for Bootstrap 5 SCSS and JS"
date: 2023-10-29T17:56:08-07:00
author: Rodney Maiato
tags: ["hugo"]
draft: false
description: "Supercharge Your Hugo Website with Bootstrap! 🚀 Follow these easy steps to seamlessly integrate Bootstrap into your Hugo project. Elevate your web development skills and create stunning sites effortlessly. Dive into the ultimate guide now! 💻✨ #Hugo #BootstrapMagic #WebDevSecrets"
---
To get started with the Hugo Bootstrap module, follow these simplified steps:

## Step 1 - Initialize Your Project as a Hugo Module
1. Open your terminal.
2. Use the command `hugo mod init github.com/your-username/repository-name`, replacing "your-username" and "repository-name" with your GitHub information.
3. This creates a file called `go.mod` in your project's root.

## Step 2 - Add Hugo Bootstrap Module to Your Config File
1. Locate your project's configuration file, which could be named `config.toml` or `hugo.toml`.
2. Add the following code in the `.toml` format, or adjust if you prefer YAML or JSON:
   ```toml
   [module]
   [[module.imports]]
   path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
   ```

## Step 3 - Update the Added Module
1. In your terminal, run `hugo mod get -u`.
2. This command downloads the module to your project, and you'll find a new file called `go.sum` in your project's root.

## Step 4 - Create SCSS and JS Files in the Assets Directory
1. Inside your project, create a folder named "scss" in the assets directory.
2. In the "scss" folder, create a file named "styles.scss".
3. Create another folder in the assets directory named "js".
4. In the "js" folder, create a file named "index.js".
5. You should now have these files: `/assets/scss/styles.scss` and `/assets/js/index.js`.

## Step 5 - Add CSS and JS Links in Your Project's Head
1. In the head section of your website, add links to the files created in step 4. This allows your pages to access the SCSS and JS files for styling and functionality.
2. Add the following code just above the closing head tag (`</head>`):
   ```html
   {{/* Load Bootstrap SCSS. */}}
   {{ $options := dict "enableSourceMap" true }}
   {{ if hugo.IsProduction}}
   {{ $options := dict "enableSourceMap" false "outputStyle" "compressed" }}
   {{ end }}
   {{ $styles := resources.Get "scss/styles.scss" }}
   {{ $styles = $styles | resources.ToCSS $options }}
   {{ if hugo.IsProduction }}
   {{ $styles = $styles | fingerprint }}
   {{ end }}
   <link href="{{ $styles.RelPermalink }}" rel="stylesheet" />

   {{/* Load Bootstrap JS. */}}
   {{ $js := resources.Get "js/index.js" }}
   {{ $params := dict }}
   {{ $sourceMap := cond hugo.IsProduction "" "inline" }}
   {{ $opts := dict "sourceMap" $sourceMap "minify" hugo.IsProduction "target" "es2018" "params" $params }}
   {{ $js = $js | js.Build $opts }}
   {{ if hugo.IsProduction }}
   {{ $js = $js | fingerprint }}
   {{ end }}  
   <script src="{{ $js.RelPermalink }}" {{ if hugo.IsProduction }}integrity="{{ $js.Data.Integrity }}"{{ end }} defer></script>
   ```

## Step 6 - Import Bootstrap Components for SCSS
1. Open your "styles.scss" file in the "assets/scss" directory.
2. Add the following code to import all Bootstrap styles:
   ```scss
   @import "bootstrap/bootstrap";
   ```

## Step 7 - Import Bootstrap JavaScript Components
1. Open your "index.js" file in the "assets/js" directory.
2. Depending on your needs, import Bootstrap JavaScript components like this:
   ```js
   import "js/bootstrap/src/collapse";
   import "js/bootstrap/src/dropdown";
   ```

Following these steps will help you set up Hugo Bootstrap for your project. If you want to select specific Bootstrap styles, you can refer to the [full list here](https://github.com/gohugoio/hugo-mod-bootstrap-scss/tree/main#scss).
