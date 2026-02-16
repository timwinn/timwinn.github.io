Create a new blog post for the Quarto blog.

Ask for:
1. **Title** — the post title
2. **Description** — a one-sentence summary for SEO and listing pages
3. **Categories** — choose from: tools, mathematics, programming, data-science, medical-education, reflections

Then:
- Generate a slug from the title (kebab-case, lowercase)
- Use today's date (YYYY-MM-DD format)
- Create the directory: `posts/{date}-{slug}/`
- Create `posts/{date}-{slug}/index.qmd` with this frontmatter:

```yaml
---
title: "{title}"
description: "{description}"
author: "Timothy Winn, MD"
date: "{date}"
categories: [{categories}]
draft: false
---
```

Include starter section headings based on the post topic. For technical posts, include Introduction, an appropriate middle section, and Conclusion. For reflections, use a more narrative structure.

After creating the file, remind the user:
- Preview with `quarto preview`
- If the post has executable code, run `quarto render` and commit `_freeze/` changes
- Push to `main` to publish
