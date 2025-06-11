# Setup Guide for Website Maintenance

Welcome to the team! This guide will walk you through the necessary steps to set up your local development environment and begin maintaining the website. This project is built using [Hugo](https://gohugo.io/) with the [Hextra theme](https://themes.gohugo.io/themes/hextra/).

## 1. Introduction

This [`SETUP.md`](SETUP.md) provides a comprehensive overview of how to get the website running on your local machine, manage content, and understand the core components. Please read through it carefully.

## 2. Prerequisites

Before you start, ensure you have the following software installed on your system. It's crucial to use the recommended versions to avoid compatibility issues.

  * **[Hugo (extended version)](https://gohugo.io/installation/)**
      * **Purpose:** Hugo is the static site generator that compiles all content, templates, and assets into the final HTML, CSS, and JavaScript files for the website. The "extended" version is required for Sass/SCSS compilation, which Hextra heavily utilizes.
      * **Recommended Version:** Ensure you have a recent extended version (e.g., `v0.120.0` or newer). You can check your version by running:
        ```bash
        hugo version
        ```
  * **[Git](https://git-scm.com/)**
      * **Purpose:** Git is a version control system used to manage the project's source code. You'll use it to clone the repository, track changes, and push updates.
      * **Recommended Version:** `v2.30` or newer. Check with:
        ```bash
        git --version
        ```
  * **[Go](https://go.dev/dl/)**
      * **Purpose:** Go is required because Hugo themes, including Hextra, often use Go Modules to manage their dependencies (e.g., for external libraries or assets).
      * **Recommended Version:** `v1.18` or newer. Check with:
        ```bash
        go version
        ```

### Development Environment Setup (Recommended)

  * **Integrated Development Environment (IDE):** We recommend using [Visual Studio Code (VS Code)](https://code.visualstudio.com/). It's a powerful and popular choice for web development.
  * **VS Code Extensions:** Once you have VS Code installed, consider installing the following extensions for a better development experience:
      * **Hugo:** For syntax highlighting and snippets.
      * **Markdown All in One:** For enhanced Markdown editing.
      * **Go:** If you plan on doing advanced Go module work.
      * **Prettier:** For consistent code formatting (if configured in the project).

## 3\. Preview the Site Locally

You can run a local development server to preview the website changes in real-time. This server automatically rebuilds and refreshes your browser when you save changes.

```bash
hugo server --logLevel debug --disableFastRender -p 1313 --buildDrafts
```

Let's break down the flags used in this command:

  * `hugo server`: Starts Hugo's built-in development server.
  * `--logLevel debug`: Sets the logging level to debug, providing more verbose output in your terminal, which can be helpful for troubleshooting.
  * `--disableFastRender`: Forces Hugo to re-render the entire site on every change. While slightly slower for very large sites, it ensures that all changes are reflected accurately and helps avoid caching issues during development.
  * `-p 1313`: Specifies the port number on which the server will run. By default, Hugo uses port 1313. If this port is in use, you can change it (e.g., `-p 8080`).
  * `--buildDrafts`: Includes content marked as `draft: true` in your front matter. This is essential for previewing work-in-progress content.

**After running the command:**

1.  You will see output in your terminal indicating that the server has started.
2.  Open your web browser and navigate to `http://localhost:1313/` (or the port you specified).
3.  The website should load, and you can now navigate it locally.
4.  As you make changes to content or templates and save them, the browser will automatically refresh to show your updates.

To stop the local server, press `Ctrl + C` in your terminal.

## 4. Content Management

All website content (pages, blog posts, documentation) is stored in Markdown files within the `content/` directory.

  * **Content Structure:** The `content/` directory mirrors the URL structure of your website. For example, `content/posts/my-first-post.md` will likely render at `yourwebsite.com/posts/my-first-post/`.
  * **Markdown:** Content is written in Markdown. Refer to a Markdown cheatsheet if you're unfamiliar.
  * **Front Matter:** Every Markdown file starts with a block of YAML (or TOML/JSON) metadata called "front matter." This defines page-specific settings like title, date, author, tags, draft status, and more.
    ```yaml
    ---
    title: "My New Blog Post"
    date: 2025-06-11T13:30:00+09:00
    draft: true # Set to 'false' to publish
    categories: ["Updates"]
    tags: ["maintenance", "guide"]
    description: "A detailed guide on how to get started with the website setup."
    ---

    # This is the main content of the page.
    You can write your Markdown here.
    ```
  * **Creating New Content:**
      * You can manually create new `.md` files in the appropriate `content/` subdirectory.
      * Alternatively, Hugo provides a command to scaffold new content with basic front matter:
        ```bash
        hugo new posts/my-new-article.md
        ```
        This command will create `content/posts/my-new-article.md` with default front matter inherited from archetypes (found in the `archetypes/` directory).
  * **Drafts:** To work on content without publishing it, set `draft: true` in its front matter. Remember to remove or set it to `false` when you're ready to publish. The `hugo server --buildDrafts` command allows you to preview these drafts.

## 5. Customization and Theming

The website uses the Hextra theme. Most global configurations are handled in the `config.yaml` (or `hugo.toml`) file at the root of the project.

  * **`config.yaml` (or `hugo.toml`):** This file contains global site settings, menu configurations, theme parameters, and more. Refer to the Hextra theme documentation for specific options you can configure here.
  * **Theme Overrides:** If you need to customize a specific part of the Hextra theme (e.g., a header, footer, or specific layout), Hugo allows you to override theme templates by placing a file with the same path in your project's `layouts/` directory. For example, to override `themes/hextra/layouts/_default/single.html`, you would create `layouts/_default/single.html` in your project root.
  * **Hextra Documentation:** For in-depth details on Hextra's features, configuration, and customization options, please refer to the official Hextra documentation: [https://github.com/imfing/hextra](https://github.com/imfing/hextra)

## 6. Resources

  * **Hugo Documentation:** [https://gohugo.io/documentation/](https://gohugo.io/documentation/)
  * **Git Documentation:** [https://git-scm.com/doc](https://git-scm.com/doc)
  * **Go Documentation:** [https://go.dev/doc/](https://go.dev/doc/)
  * **Hextra Theme GitHub Repository & Docs:** [https://github.com/imfing/hextra](https://github.com/imfing/hextra)
  * **Markdown Cheatsheet:** [https://www.markdownguide.org/cheat-sheet/](https://www.markdownguide.org/cheat-sheet/)

Good luck, and happy editing!
