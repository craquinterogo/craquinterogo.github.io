# Jekyll-Scholar Setup Guide

## ✅ What's Installed

Jekyll-Scholar is now configured in your blog to handle BibTeX citations like LaTeX does.

## 📁 File Structure

```
_bibliography/
  └── references.bib    # Your BibTeX entries go here
```

## 🔧 Configuration

In `_config.yml`:
```yaml
scholar:
  style: apa                    # Citation style (apa, ieee, chicago, etc.)
  locale: en
  source: ./_bibliography       # Where BibTeX files are stored
  bibliography: references.bib  # Main BibTeX file
```

## 📝 Usage in Posts

### 1. Inline Citation
```liquid
{% cite quintero2024reinforcement %}
```
Output: (Quintero, Leon, Sandoval & Hernandez, 2024)

### 2. Multiple Citations
```liquid
{% cite quintero2024reinforcement quintero2025deep %}
```

### 3. Bibliography (list all cited works)
```liquid
{% bibliography --cited %}
```

### 4. Full Bibliography (all entries)
```liquid
{% bibliography %}
```

Reference URLs and DOI URLs are clickable and open in a new tab
(`target="_blank"`, with `rel="noopener noreferrer"`). The shared
[`_layouts/reference.html`](./_layouts/reference.html) template preserves APA
formatting and links the URL displayed by the citation style, preferring the DOI
when it is displayed. References without a URL or DOI remain unchanged.
This is enabled globally by `scholar.bibliography_template: reference` in
[`_config.yml`](./_config.yml); no changes to individual posts are needed.

### 5. Filtered Bibliography
```liquid
{% bibliography --query @article %}           # Only articles
{% bibliography --query @*[year=2024] %}      # Only 2024
{% bibliography --query @*[author=Quintero] %} # By author
```

## 🎨 Available Citation Styles

Change the `style:` in `_config.yml`:
- `apa` - APA Style
- `ieee` - IEEE Style
- `chicago` - Chicago Style
- `vancouver` - Vancouver Style
- `harvard` - Harvard Style
- `mla` - MLA Style
- `nature` - Nature Style

## 📚 Adding New References

Just add more BibTeX entries to `_bibliography/references.bib`:

```bibtex
@article{yourkey2025,
  title   = {Your Paper Title},
  author  = {Last, First and Last2, First2},
  journal = {Journal Name},
  year    = {2025}
}
```

Then cite with: `{% cite yourkey2025 %}`

## 🔗 Advanced Features

### Custom Link Text
```liquid
{% cite_details quintero2024reinforcement --text Read More %}
```

### Suppress Author
```liquid
{% cite quintero2024reinforcement --suppress_author %}
```

### Specific Page
```liquid
{% cite quintero2024reinforcement --locator 42 %}
```

## 🚨 Important Notes

1. **GitHub Pages Limitation**: Jekyll-Scholar doesn't work on GitHub Pages due to plugin restrictions
2. **Solution**: Build locally and push the `_site` folder, or use GitHub Actions
3. **Rebuild**: Run `bundle exec jekyll build` after changing BibTeX files

## 🎯 What You Get

- ✅ Automatic citation formatting (like LaTeX)
- ✅ Automatic bibliography generation
- ✅ Multiple citation styles
- ✅ No manual HTML/formatting needed
- ✅ Consistent academic citations

## 📖 More Information

Official docs: https://github.com/inukshuk/jekyll-scholar
