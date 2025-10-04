# Kansas DOGE

Here's how to get your State DOGE site up and running, super easy!

## Overview

This guide helps beginners turn a hand-drawn layout into a real website with minimal coding, using Jekyll Minimal Mistakes and Vercel.

## 0. Get your site created in the DOGE Network

- Email `community@dogenetwork.org` to let them know what state you are creating for
- You will get an email back with instructions and details

## 1. Get Your Tools

### Ruby

- **Windows:** Go to [rubyinstaller.org](https://rubyinstaller.org), download the latest, and click "Next" on everything.
- **macOS:** Open Terminal and type `brew install ruby` (install Homebrew if you don't have it).
- **Linux (Ubuntu/Debian):** Open Terminal and type `sudo apt update` then `sudo apt install ruby-full`.

### Git

- Go to [git-scm.com](https://git-scm.com), download for your OS, and keep clicking "Next" to install.

### Cursor Editor

- Visit [cursor.so](https://cursor.so), download, and follow the installation steps.

### Github Desktop

- Visit [desktop.github.com](https://desktop.github.com), download, install

## 2. Create Your Website

1. Open Github Desktop, and clone your state DOGE site using the instructions from step 0
2. Open Cursor and open the cloned state DOGE directory as a project
3. Create a terminal session and run these commands:

```bash
gem install bundler jekyll
bundle init
```

4. Open the new `Gemfile` and add these lines:

```ruby
gem "jekyll"
gem "minima"
```

5. Back in terminal, type:

```bash
bundle install --path vendor/bundle
bundle exec jekyll new . --force
```

**Important Notes:**
- If you get permission errors on macOS, use `bundle install --path vendor/bundle` instead of just `bundle install`
- After running `jekyll new`, you need to update the `_config.yml` file to use the correct theme (see step 6 below)

## 3. Put Your Layout Into the Homepage

Start the webserver locally with:

```bash
bundle exec jekyll serve
```

Open `index.md` in Cursor Editor. Copy, paste, and edit this (it's super simple!):

```yaml
---
layout: default
---

## Pages

- [Savings](/savings)
- [Payments](/payments)
- [Spend](/spend)
- [Regulations](/regulations)
- [Workforce](/workforce)
- [About](/about)

## Network

- [How to join DOGE Network](https://dogenetwork.org/join-doge-network)
- [How to research](https://dogenetwork.org/docs/howto/how-to-doge-your-state)
- [How to use data](https://dogenetwork.org/docs/howto/vibe-coding-for-beginners)
- [DOGE Network Calendar](https://dogenetwork.org/calendar)

## National

- [National Link 1](https://sample.org/link)

## State

- [State Link 1](https://sample.org/link)

## Local

- [Local Link 1](https://sample.org/link)
```

## 4. Configure Your Site

After running `jekyll new`, you need to update the `_config.yml` file:

1. Open `_config.yml` in Cursor Editor
2. Set your site title and basic info:

```yaml
title: "Kansas DOGE"
email: community@dogenetwork.org
description: Kansas State DOGE Network site for government transparency and efficiency.
theme: minima
```

3. Add navigation links:

```yaml
navigation:
  - title: Savings
    url: /savings/
  - title: Regulations
    url: /regulations/
```

## 5. Creating Pages

### 5.1. Planning: What Goes on Each Page?

Each page (like "Savings") should focus on one topic.

Examples: "Savings" for grants and updates, "Payments/Spend" for contracts, "Regulations" for rules, "Workforce" for hiring data, "About" for your site's mission. See [cali-doge.org](https://cali-doge.org) pages as examples.

### 5.2. Create a New Page File in Your Site

In your Jekyll folder (where `index.md` is), create new files like `savings.md`, `payments.md`, etc.

Each file should start like this (example for "Savings"):

```yaml
---
title: Savings
description: Latest updates and efficiency efforts in Kansas government.
permalink: /savings/
layout: page
---

## Kansas Government Savings

- $27B in federal grants announced April 2024
- Recent major cuts: 250K federal job reductions
- Overhaul of 800+ government agencies
- [See more: KS government spending info](https://t.co/eaaE32U7k8)
```

Make similar files for `payments.md`, `spend.md`, `regulations.md`, `workforce.md`, and `about.md`.

Copy, paste, and update the info! Use links to reliable sources.

### 5.3. Link Pages Together

In your `_config.yml` file, add pages like this for navigation:

```yaml
navigation:
  - title: Savings
    url: /savings/
  - title: Payments
    url: /payments/
  - title: Spend
    url: /spend/
  - title: Regulations
    url: /regulations/
  - title: Workforce
    url: /workforce/
  - title: About
    url: /about/
```

## 6. Add Your Logos and Custom Styling

1. Save your DOGE and state logos in the root directory (same level as `index.md`).
2. Create a custom header to display logos in the site header:

Create `_includes/header.html`:
```html
<header class="site-header" role="banner">
  <div class="wrapper">
    <div style="display: flex; align-items: center;">
      <img src="/doge-network.png" alt="DOGE Network Logo" width="50" height="50" style="margin-right: 15px;">
      <img src="/Flag_of_Kansas.svg" alt="Kansas Flag" width="75" height="45" style="margin-right: 15px;">
      <a class="site-title" rel="author" href="{{ "/" | relative_url }}">{{ site.title | escape }}</a>
    </div>
    <!-- Navigation code here -->
  </div>
</header>
```

3. Add custom responsive card styling by creating `assets/main.scss`:
```scss
---
---

@import "minima";

/* Responsive layout using CSS columns */
.page-content {
  column-count: 1;
  column-gap: 20px;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Wide screens: 2-3 columns */
@media (min-width: 600px) {
  .page-content {
    column-count: 2;
  }
}

@media (min-width: 900px) {
  .page-content {
    column-count: 3;
  }
}

/* Card styling - keep headers and content together */
.page-content h2 {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 12px 12px 0 0;
  padding: 15px 20px;
  margin: 20px 0 0 0;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
  font-weight: 600;
  font-size: 1.3em;
  text-transform: uppercase;
  letter-spacing: 1px;
  break-inside: avoid;
}
```

## 7. Preview the Site Locally

In your terminal, type:

```bash
bundle exec jekyll serve
```

Then open `http://localhost:4000` in your browser to see your site!

## 8. Publish with Vercel

Email `community@dogenetwork.org` to let them know you're ready to publish, and they'll set it up so your site updates automatically when you make changes.

