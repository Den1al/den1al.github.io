.PHONY: dev build preview clean deploy

# Development server
dev:
	npm run dev

# Build the static site
build: clean
	npm run build
	@echo "Build complete! Static files are in ./build"

# Preview the built site
preview: build
	npm run preview

# Clean build artifacts
clean:
	rm -rf build .svelte-kit

# Deploy to parent directory (for GitHub Pages)
deploy: build
	@echo "Deploying to GitHub Pages..."
	# Clean up old files in parent directory (except .git, sveltekit-site, and other important files)
	find .. -maxdepth 1 -type f -name "*.html" -delete
	find .. -maxdepth 1 -type f -name "*.xml" -delete
	find .. -maxdepth 1 -type d -name "_*" -exec rm -rf {} +
	# Copy build files to parent directory
	cp -r build/* ../
	@echo "Deployment complete! Files copied to parent directory"

# Build and deploy in one command
publish: deploy
	@echo "Ready to commit and push to GitHub!"

# Install dependencies
install:
	npm install

# Check TypeScript
check:
	npm run check

# Full build and test
test: check build
	@echo "All checks passed!"