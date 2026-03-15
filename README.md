
# Training: Looker Studio

This repository contains materials for a hands-on training on Looker Studio (formerly Google Data Studio). It includes the presentation slides, assets, example data, and all resources needed to run and customize the workshop.

## Presentation

- **Live presentation:** http://surquest.github.io/training-lookerstudio
- **Slides source:** [src/content/slides.md](src/content/slides.md)

## Project Structure

```
src/
	index.html                # Main HTML file for the presentation
	assets/
		logo.svg                # surQuest logo used in slides
		data/
			zs.data.sample.xlsx   # Sample data for Looker Studio exercises
		img/                    # (empty) Place for additional images
	content/
		slides.md               # Markdown source for all presentation slides
	css/
		reset.css               # CSS reset
		reveal.css              # Reveal.js core styles
		theme.css               # Custom theme for the presentation
	fonts/                    # Custom font files used in slides
	js/
		reveal.js               # Reveal.js presentation framework
		plugin/
			highlight.js          # Syntax highlighting plugin
			markdown.js           # Markdown support plugin
			markdown.mjs          # ES module for markdown
			math.js               # Math rendering plugin
			notes.js              # Speaker notes plugin
			highlight/            # (empty) Reserved for highlight.js assets
		utils/                  # (empty) Reserved for custom JS utilities
```

## Usage

Open the [live presentation](http://surquest.github.io/training-lookerstudio) to view the workshop slides. To edit or customize the slides, modify the markdown file at `src/content/slides.md` and reload the presentation in your browser.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

