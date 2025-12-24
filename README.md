# My Personal Portfolio

My personal portfolio website built with SvelteKit featuring a Terminal Editorial design aesthetic.

Go to https://abeles.dev for a live view.

## Color Scheme

### Purple Palette

| Name       | Hex       |
| ---------- | --------- |
| Purple 100 | `#CEB3EF` |
| Purple 200 | `#A989F5` |
| Purple 300 | `#7759C2` |
| Purple 400 | `#5943B6` |
| Purple 500 | `#2F2A6B` |
| Purple 600 | `#232150` |

### Teal Palette

| Name     | Hex       |
| -------- | --------- |
| Teal 100 | `#C5F4EC` |
| Teal 200 | `#6FDAC9` |
| Teal 300 | `#10B1B1` |

### Neutrals

| Name     | Hex       |
| -------- | --------- |
| Dark 900 | `#0A0A0F` |
| Dark 800 | `#111118` |
| Dark 700 | `#171321` |
| Dark 600 | `#1E1A2E` |
| Dark 500 | `#2A2440` |

## Development

```bash
cd sveltekit-site

# Install dependencies
make install

# Run development server
make dev

# Build the site
make build

# Deploy to GitHub Pages
make deploy
```

## Structure

- `sveltekit-site/src/routes/` - Page components
- `sveltekit-site/src/lib/components/` - Reusable components
- `sveltekit-site/src/app.css` - Global styles and design system
- `sveltekit-site/static/` - Static assets

## Deployment

The site is configured for GitHub Pages. Use `make deploy` to build and copy files to the parent directory.
