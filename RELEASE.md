# Release Guide for PyPI and Zenodo

This guide will walk you through publishing the Brand Color Analyzer to PyPI and obtaining a DOI from Zenodo.

## Prerequisites

Before you begin, ensure you have:
- A PyPI account (register at https://pypi.org/account/register/)
- A TestPyPI account for testing (register at https://test.pypi.org/account/register/)
- A Zenodo account (login at https://zenodo.org/ using your GitHub account)

## Part 1: Prepare for PyPI Release

### 1. Install build tools

```bash
pip install --upgrade build twine
```

### 2. Build the package

```bash
python -m build
```

This will create two files in the `dist/` directory:
- `brand-color-analyzer-1.0.0.tar.gz` (source distribution)
- `brand_color_analyzer-1.0.0-py3-none-any.whl` (wheel distribution)

### 3. Test on TestPyPI (Recommended)

First, test your package on TestPyPI:

```bash
# Upload to TestPyPI
python -m twine upload --repository testpypi dist/*

# Test installation from TestPyPI
pip install --index-url https://test.pypi.org/simple/ --no-deps brand-color-analyzer
```

### 4. Upload to PyPI

Once testing is successful:

```bash
python -m twine upload dist/*
```

You'll be prompted for your PyPI username and password.

### 5. Verify installation

```bash
pip install brand-color-analyzer
```

## Part 2: Create GitHub Release for Zenodo

### 1. Enable Zenodo GitHub integration

1. Go to https://zenodo.org/account/settings/github/
2. Find your `brand-color-analyzer` repository
3. Toggle the switch to ON
4. This enables automatic DOI creation for each GitHub release

### 2. Create a GitHub Release

#### Option A: Via GitHub Web Interface

1. Go to https://github.com/MichailSemoglou/brand-color-analyzer
2. Click on "Releases" (right sidebar)
3. Click "Create a new release"
4. Fill in the release form:
   - **Tag version**: `v1.0.0`
   - **Release title**: `Brand Color Analyzer v1.0.0`
   - **Description**: 
     ```
     # Brand Color Analyzer v1.0.0
     
     First stable release of the Brand Color Analyzer tool.
     
     ## Features
     - Research-based color analysis using established theories
     - Brand personality dimension analysis
     - Emotional response evaluation
     - Cultural association analysis
     - Support for multiple image formats (PNG, JPG, JPEG, TIFF, WebP)
     - Batch processing capabilities
     - Multiple output formats (JSON, TXT)
     
     ## Research Foundation
     Based on empirical research from:
     - Labrecque & Milne (2012)
     - Singh (2006)
     - Elliot & Maier (2014)
     
     ## Installation
     ```
     pip install brand-color-analyzer
     ```
     
     ## PyPI
     This release is available on PyPI: https://pypi.org/project/brand-color-analyzer/
     ```
5. Click "Publish release"

#### Option B: Via Command Line

```bash
# Make sure you're on the main branch with all changes committed
git checkout main
git pull origin main

# Create and push a tag
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0

# Then create the release on GitHub's website
```

### 3. Get your DOI from Zenodo

1. After creating the GitHub release, go to https://zenodo.org/account/settings/github/
2. Find your repository - it should show the new release
3. Click on the DOI badge or the repository name
4. Your DOI will be displayed (format: `10.5281/zenodo.XXXXXXX`)
5. Copy the DOI and the badge markdown

### 4. Add DOI badge to README

Once you have your DOI, add it to your README.md:

```markdown
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)
```

## Post-Release Checklist

- [ ] Package successfully uploaded to PyPI
- [ ] Package can be installed via `pip install brand-color-analyzer`
- [ ] GitHub release v1.0.0 created
- [ ] Zenodo DOI obtained and badge added to README
- [ ] CITATION.cff updated with DOI (if desired)
- [ ] Documentation updated with installation instructions

## Future Releases

For future releases:

1. Update version number in:
   - `brand_color_analyzer.py` (`__version__`)
   - `pyproject.toml` (`version`)
   - `CITATION.cff` (`version` and `date-released`)

2. Commit changes:
   ```bash
   git add .
   git commit -m "Bump version to X.Y.Z"
   git push
   ```

3. Rebuild and upload to PyPI:
   ```bash
   rm -rf dist/ build/ *.egg-info
   python -m build
   python -m twine upload dist/*
   ```

4. Create new GitHub release with tag `vX.Y.Z`
   - Zenodo will automatically create a new DOI version

## Troubleshooting

### PyPI Upload Issues

- **Authentication error**: Use API tokens instead of password
  - Generate token at https://pypi.org/manage/account/token/
  - Use `__token__` as username and token as password

- **Package name already taken**: Change package name in `pyproject.toml`

- **Version already exists**: Increment version number (you cannot overwrite)

### Zenodo Issues

- **DOI not created**: Check that the repository toggle is ON in Zenodo settings
- **Missing metadata**: Ensure `.zenodo.json` is present in the repository before creating release

## Resources

- PyPI Documentation: https://packaging.python.org/
- Twine Documentation: https://twine.readthedocs.io/
- Zenodo GitHub Guide: https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content
- Semantic Versioning: https://semver.org/

## Contact

For issues or questions, please open an issue on GitHub or contact:
- Email: m.semoglou@tongji.edu.cn
- GitHub: @MichailSemoglou
