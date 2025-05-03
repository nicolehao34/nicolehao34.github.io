# Folders

- **_drafts/**  
    *(Unpublished blog posts.)*  
    Posts placed here can be previewed locally but won't appear on the live site until moved to `_posts/`.

- **_includes/**  
    Contains partial HTML files (e.g., `analytics.html`) that can be reused across layouts using `{% include %}`.

- **_layouts/**  
    Contains page templates (e.g., `default.html`) that define how different pages look structurally.

- **_posts/**  
    Contains published blog posts.  
    The filenames follow the `YYYY-MM-DD-title.md` format for date-based post management.

- **_sass/**  
    Contains `.scss` files (Sass stylesheets) for modular CSS styling.  
    Likely used with `style.scss` for overall styling.

- **images/**  
    Stores image assets (e.g., blog post images, logos).

- **papers/**  
    A custom directory for academic papers or PDFs.

# Files

- **.gitignore**  
    Specifies files/folders Git should ignore (e.g., build files, local config).

- **404.md**  
    The custom "Page not found" page.

- **CNAME**  
    Used for GitHub Pages custom domains.  
    Empty here—possibly the custom domain was removed.

- **LICENSE**  
    Contains the license for the project, most likely MIT based on the README.

- **README.md**  
    The description of the repo, probably has usage instructions or purpose.

- **_config.yml**  
    The Jekyll config file.  
    Sets variables like `title`, `description`, `baseurl`, `permalink`, etc.  
    Important for controlling site behavior and metadata.

- **blog.html**  
    A layout or index for blog posts. Might be the blog landing page.

- **index.md**  
    Likely the homepage content.  
    Uses front matter (YAML at the top) to hook into the layout defined in `_layouts`.

- **style.scss**  
    The main stylesheet using Sass.  
    Compiled into CSS during the Jekyll build process.
