# Jonas Heering - Personal Website

This is the source code for Jonas Heering's personal academic website built with Quarto.

## Prerequisites

- [Quarto](https://quarto.org/docs/get-started/) installed
- [RStudio](https://posit.co/download/rstudio-desktop/) (optional, but recommended)
- [Git](https://git-scm.com/) installed
- A [GitHub account](https://github.com/)

## File Structure

```
quarto-website/
├── _quarto.yml           # Main configuration file
├── index.qmd             # Home page
├── research.qmd          # Research page
├── teaching.qmd          # Teaching page
├── public-writing.qmd    # Public writing page
├── styles.css            # Custom CSS styles
├── custom.scss           # Custom SCSS theme
├── .gitignore           # Git ignore file
├── files/
│   ├── profile/
│   │   └── jonas-heering-photo.jpg  # Your profile photo
│   └── Jonas-Heering-CV.pdf         # Your CV PDF
└── docs/                # Generated website (created after rendering)
```

## Setup Instructions

### 1. Prepare Your Content

#### Add Your Profile Photo
- Place your professional photo in `files/profile/`
- Name it `jonas-heering-photo.jpg`
- Recommended size: 800x800 pixels or similar square ratio

#### Add Your CV
- Place your CV PDF in `files/`
- Name it `Jonas-Heering-CV.pdf`

#### Update Social Media Links
Open `_quarto.yml` and replace the following placeholders:
- `YOUR-GITHUB-USERNAME` → Your actual GitHub username
- `YOUR-LINKEDIN-PROFILE` → Your LinkedIn profile name
- `YOUR-BLUESKY-HANDLE` → Your BlueSky handle

#### Customize Content
Edit the following files to add your content:
- `index.qmd` - Update your bio and contact information
- `research.qmd` - Add your publications, working papers, and research areas
- `teaching.qmd` - Add your teaching experience and courses
- `public-writing.qmd` - Add your op-eds, interviews, and media appearances

### 2. Preview Your Website in RStudio

1. Open RStudio
2. File → Open Project
3. Navigate to the `quarto-website` folder
4. Open any `.qmd` file
5. Click the "Render" button (or press Ctrl/Cmd + Shift + K)
6. The website will render and open in a preview window

Alternatively, in the RStudio Terminal:
```bash
quarto preview
```

### 3. Render Your Website

To build the full website:

In RStudio Terminal or your command line:
```bash
quarto render
```

This will create a `docs/` folder with your rendered website.

## Publishing to GitHub Pages

### Step 1: Create a GitHub Repository

1. Go to [GitHub](https://github.com/) and log in
2. Click the "+" icon in the top right → "New repository"
3. Name it: `YOUR-USERNAME.github.io` (replace YOUR-USERNAME with your GitHub username)
4. Make it public
5. Do NOT initialize with README, .gitignore, or license
6. Click "Create repository"

### Step 2: Push Your Website to GitHub

In RStudio Terminal or your command line, navigate to your project folder and run:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Commit files
git commit -m "Initial commit"

# Add remote repository (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/YOUR-USERNAME.github.io.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Configure GitHub Pages

1. Go to your repository on GitHub
2. Click "Settings" (top menu)
3. Click "Pages" (left sidebar)
4. Under "Source":
   - Select branch: `main`
   - Select folder: `/docs`
5. Click "Save"

Your website will be published at: `https://YOUR-USERNAME.github.io/`

It may take a few minutes for the site to go live.

## Connecting Your Custom Domain (jonasheering.com)

### Step 1: Configure GitHub Pages for Custom Domain

1. In your GitHub repository → Settings → Pages
2. Under "Custom domain", enter: `jonasheering.com`
3. Click "Save"
4. Wait for DNS check (may take a few minutes)
5. Check "Enforce HTTPS" once available

### Step 2: Configure Your Domain DNS Settings

Go to your domain registrar (where you bought jonasheering.com) and add these DNS records:

#### Option A: Using A Records (Recommended)
Add four A records pointing to GitHub's IP addresses:

```
Type: A
Name: @
Value: 185.199.108.153

Type: A
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153
```

#### For www subdomain:
```
Type: CNAME
Name: www
Value: YOUR-USERNAME.github.io.
```

### Step 3: Create CNAME File

Create a file named `CNAME` (no extension) in your `docs/` folder:
```
jonasheering.com
```

Then update and push to GitHub:
```bash
git add docs/CNAME
git commit -m "Add custom domain"
git push
```

### Step 4: Wait for DNS Propagation

DNS changes can take 24-48 hours to fully propagate, but often work within a few hours.

You can check status at: https://www.whatsmydns.net/

## Updating Your Website

Whenever you make changes:

1. Edit your `.qmd` files in RStudio
2. Render the site: `quarto render`
3. Commit and push changes:
   ```bash
   git add .
   git commit -m "Update content"
   git push
   ```

Your live site will update automatically within a few minutes.

## Customization Options

### Change Colors
Edit `custom.scss` to change the color scheme:
```scss
$primary: #003366;  // Change this to your preferred color
```

### Change Layout
Edit `_quarto.yml` to modify navigation, footer, or other settings.

### Add New Pages
1. Create a new `.qmd` file (e.g., `blog.qmd`)
2. Add it to the navbar in `_quarto.yml`:
   ```yaml
   - text: "Blog"
     href: blog.qmd
   ```

## Troubleshooting

### Website not updating?
- Make sure you ran `quarto render` before pushing
- Check that changes are in the `docs/` folder
- GitHub Pages may take a few minutes to update

### Custom domain not working?
- Verify DNS records are correct
- Wait for DNS propagation (up to 48 hours)
- Check GitHub Pages settings show your domain
- Ensure CNAME file exists in `docs/` folder

### Profile image not showing?
- Make sure the image is in `files/profile/` folder
- Check the filename matches what's in `index.qmd`
- Try rendering again

## Resources

- [Quarto Documentation](https://quarto.org/docs/guide/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Custom Domain Documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

## Questions?

If you need help, check the [Quarto Community](https://github.com/quarto-dev/quarto-cli/discussions) or [GitHub Pages Help](https://docs.github.com/en/pages).
