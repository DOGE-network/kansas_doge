# Kansas DOGE

## Maintaining Your Site After It's Built

Once your Kansas DOGE site is up and running, here's how to keep it updated and maintained:

### Overview of Key Files

Your site consists of three main components

#### 1. `index.md` - Your Homepage
This is your main landing page where visitors first arrive. It contains:
- **Layout**: Uses `layout: default` to display the standard site structure
- **Navigation Links**: Found in the header, quick access to all your pages
- **DOGE Network Resources**: Links to DOGE Network documentation, research guides, and calendar
- **Content Sections**: Organized by the headers. Supports YouTube and X embedding. 

To update your homepage:
- Edit the markdown content directly in `index.md`
- Add or remove links in the various sections
- Update descriptions and information as needed
- The file uses simple markdown formatting - just use `##` for headings and `-` for bullet points

#### 2. Individual Pages (`savings.md`, `regulations.md`, etc.)
Each topic has its own dedicated page file:
- **File Structure**: Each page is a separate `.md` file in your root directory
- **Front Matter**: Each page starts with YAML configuration (title, description, permalink, layout)
- **Content**: Markdown-formatted content with headings, bullet points, and links
- **Navigation**: Automatically appears in your site's navigation menu

To maintain your pages:
- Open any `.md` file (like `savings.md`) in your editor
- Update the content, add new information, or modify existing text
- Add new links to reliable sources
- Keep information current and relevant to Kansas government

#### 3. `_config.yml` - Site Configuration
This file controls your entire site's behavior and appearance:
- **Site Information**: Title, email, description, URLs
- **Theme Settings**: Controls the visual appearance
- **Navigation Menu**: Defines which pages appear in your site's navigation
- **Footer Links**: Links that appear at the bottom of every page
- **Logo References**: Points to your DOGE and state logos

To update site configuration:
- Modify site title, email, or description
- Add or remove navigation items
- Update footer links
- Change logo file references

### As Needed
- Add new pages by creating new `.md` files
- Update navigation in `_config.yml` when adding pages
- Modify styling by editing CSS files in the `assets/` folder

## Building the Site From Scratch

Here's how to get your State DOGE site up and running from the beginning:

### Overview

This guide helps beginners turn a hand-drawn layout into a real website with minimal coding, using Jekyll Minimal Mistakes and Vercel.

### 1. Get Your Site Created in the DOGE Network

- Email `community@dogenetwork.org` to let them know what state you are creating for
- You will get an email back with instructions and details

### 2. Get Your Tools

#### Ruby
- **Windows:** Go to [rubyinstaller.org](https://rubyinstaller.org), download the latest, and click "Next" on everything.
- **macOS:** Open Terminal and type `brew install ruby` (install Homebrew if you don't have it).
- **Linux (Ubuntu/Debian):** Open Terminal and type `sudo apt update` then `sudo apt install ruby-full`.

#### Git
- Go to [git-scm.com](https://git-scm.com), download for your OS, and keep clicking "Next" to install.

#### Cursor Editor
- Visit [cursor.so](cursor.so), download, and follow the installation steps.

#### Github Desktop
- Visit [desktop.github.com](desktop.github.com), download, install

### 3. Create Your Website

1. Open Github Desktop, and clone your state DOGE site using the instructions from step 1
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
- After running `jekyll new`, you need to update the `_config.yml` file to use the correct theme (see step 4 below)

### 4. Put Your Layout Into the Homepage

Start the webserver locally with:

```bash
bundle exec jekyll serve
```

Open `index.md` in Cursor Editor. Copy, paste, and edit this (it's super simple!):

```yaml
---
layout: default
---

## Network

- [How to join DOGE Network](https://dogenetwork.org/join-doge-network)
- [How to research](https://dogenetwork.org/docs/howto/how-to-doge-your-state)
- [How to use data](https://dogenetwork.org/docs/howto/vibe-coding-for-beginners)
- [DOGE Network Calendar](https://dogenetwork.org/calendar)

## National

- [National Link 1](https://sample.org/link)

## State

- [State Link 1](https://sample.org/link)
```

### 5. Configure Your Site

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

### 6. Creating Pages

#### 6.1. Planning: What Goes on Each Page?

Each page (like "Savings") should focus on one topic.

Examples: "Savings" for grants and updates, "Payments/Spend" for contracts, "Regulations" for rules, "Workforce" for hiring data, "About" for your site's mission. See [cali-doge.org](https://cali-doge.org) pages as examples.

#### 6.2. Create a New Page File in Your Site

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

#### 6.3. Link Pages Together

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

### 7. Add Your Logos and Custom Styling

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

/* Responsive layout using CSS Grid - prevents content from breaking across columns */
.page-content {
  display: grid;
  grid-template-columns: 1fr;
  gap: 20px;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Medium screens: 2 columns */
@media (min-width: 600px) {
  .page-content {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .page-content > * {
    grid-column: span 1;
  }
}

/* Wide screens: 3 columns */
@media (min-width: 900px) {
  .page-content {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Card styling - headers and content stay together automatically */
.page-content h2 {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 12px 12px 0 0;
  padding: 15px 20px;
  margin: 0;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
  font-weight: 600;
  font-size: 1.3em;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.page-content h2 + ul {
  background-color: #ffffff;
  border: 1px solid #e1e5e9;
  border-top: none;
  border-radius: 0 0 12px 12px;
  padding: 15px 20px;
  margin: 0;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  list-style: none;
}
```

### 8. Preview the Site Locally

In your terminal, type:

```bash
bundle exec jekyll serve
```

Then open `http://localhost:4000` in your browser to see your site!

### 9. Publish with Vercel

Email `community@dogenetwork.org` to let them know you're ready to publish, and they'll set it up so your site updates automatically when you make changes.
