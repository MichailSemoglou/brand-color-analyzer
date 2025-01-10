# Brand Color Analyzer

A comprehensive tool for analyzing brand colors based on empirical research in color psychology and marketing. The tool provides detailed analysis of colors including brand personality dimensions, emotional responses, and cultural associations.

## Features

- Research-based color analysis using established theories
- Brand personality dimension analysis (sincerity, excitement, competence, sophistication, ruggedness)
- Emotional response evaluation (arousal, pleasure, dominance, warmth, calmness)
- Cultural association analysis (trust, quality, premium, innovation, tradition)
- Support for multiple image formats: PNG, JPG, JPEG, TIFF, WebP
- Batch processing capabilities
- Multiple output formats (JSON, TXT)
- Progress tracking and detailed summaries
- Comprehensive error handling

## Installation

1. Clone the repository:
```bash
git clone https://github.com/MichailSemoglou/brand-color-analyzer.git
cd brand-color-analyzer
```

2. Create and activate a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install requirements:
```bash
pip install -r requirements.txt
```

## Usage

### Command Line Interface

Single image analysis:
```bash
python brand_color_analyzer.py path/to/image.jpg output/directory
```

Batch processing:
```bash
python brand_color_analyzer.py path/to/image/directory output/directory
```

### Options

- `--min-frequency`: Minimum color frequency to analyze (default: 5.0)
- `--max-frequency`: Maximum color frequency to analyze (default: 100.0)
- `--format`: Output format: json or txt (default: json)
- `-v, --verbose`: Increase output verbosity
- `--version`: Show program version
- `-h, --help`: Show help message

### Python API

```python
from brand_color_analyzer import ColorAnalyzer, ImageAnalyzer

# Analyze a specific color (RGB)
analyzer = ColorAnalyzer()
results = analyzer.analyze_color((255, 0, 0))  # Analyze red
print(results)

# Analyze an image
img_analyzer = ImageAnalyzer(min_frequency=5.0, max_frequency=100.0)
analysis = img_analyzer.analyze_image("path/to/image.jpg", output_format="json")
```

## Output Examples

### JSON Output
```json
{
  "color_attributes": {
    "rgb": [255, 0, 0],
    "hsv": [0, 100, 100],
    "hex": "#FF0000",
    "cmyk": [0, 100, 100, 0],
    "name": "Red"
  },
  "brand_personality": {
    "sincerity": 25.0,
    "excitement": 85.0,
    "competence": 30.0,
    "sophistication": 40.0,
    "ruggedness": 45.0
  }
}
```

### Text Output
```
Color Analysis Results
======================

Color Information:
  Name: Red
  RGB: (255, 0, 0)
  HSV: (0, 100, 100)
  HEX: #FF0000
  CMYK: (0, 100, 100, 0)

Brand Personality Dimensions:
  Sincerity: 25.0%
  Excitement: 85.0%
  Competence: 30.0%
  Sophistication: 40.0%
  Ruggedness: 45.0%
```

## Research Foundation

The tool implements research findings and methodologies from:
- Labrecque & Milne (2013): “Exciting Red and Competent Blue: The Importance of Color in Marketing”
- Singh (2006): “Impact of Color on Marketing”
- Elliot & Maier (2014): “Color Psychology: Effects of Perceiving Color on Psychological Functioning in Humans”

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation

If you use this tool in your work, please cite:

```bibtex
@software{semoglou2025brandcolor,
    author = {Semoglou, Michail},
    title = {Brand Color Analyzer: A Research-Based Tool for Color Psychology in Marketing},
    year = {2025},
    url = {https://github.com/MichailSemoglou/brand-color-analyzer},
    version = {1.0.0}
}
```

## Contact

- Author: Michail Semoglou
- Email: m.semoglou@tongji.edu.cn
