# CoverScope - AI Plant Coverage Measurement

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![HTML5](https://img.shields.io/badge/HTML-5-orange.svg)]
[![CSS3](https://img.shields.io/badge/CSS-3-blue.svg)]
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow.svg)]

A web-based application that measures plant coverage in images using AI-powered computer vision techniques. Inspired by the original CoverScope app, this is a standalone HTML web interface that works entirely in the browser.

## Features

- **Drag & Drop Image Upload**: Easily upload images from your device
- **Multiple Analysis Modes**:
  - 🌿 **Green Detection**: Detects green vegetation using color analysis
  - 📊 **NDVI Simulation**: Simulates the Normalized Difference Vegetation Index
  - 🎯 **Edge Detection**: Uses Sobel edge detection to identify plant boundaries
- **Real-time Results**: Instant analysis with visual feedback
- **Detailed Statistics**: View pixel counts, coverage ratios, and percentages
- **Export Results**: Download analysis results as JSON
- **Responsive Design**: Works on desktop and mobile devices
- **No Backend Required**: Runs entirely client-side in the browser

## Demo

Try the live demo by opening `index.html` in any modern web browser.

```bash
# Simply open the file in your browser
open index.html  # macOS
xdg-open index.html  # Linux
type index.html  # Windows
```

Or start a local server:

```bash
# Python 3
python -m http.server 8000

# Node.js
npx serve

# Then open http://localhost:8000 in your browser
```

## Screenshots

The app features a clean, modern interface with:
- A drag-and-drop upload zone
- Side-by-side image comparison (original vs processed)
- Visual statistics and progress bars
- One-click analysis and download options

## How It Works

1. **Upload an Image**: Drag and drop or click to browse for an image file
2. **Select Analysis Mode**: Choose from three different plant detection algorithms
3. **Analyze**: Click "Analyze Image" to process the photo
4. **View Results**: See the plant coverage percentage and detailed statistics
5. **Export**: Download your results as a JSON file

### Analysis Methods

#### Green Detection
The most straightforward method, this analyzes the RGB color values of each pixel to identify areas that are predominantly green (indicating healthy vegetation). The algorithm checks that:
- Green channel value is high (> 100)
- Green is significantly greater than Red and Blue channels (> 1.2x)
- Red and Blue channels are not too bright (< 200)

#### NDVI Simulation
Normalized Difference Vegetation Index is a standard remote sensing measurement. This mode simulates NDVI by using the green channel as a proxy for near-infrared (NIR) data:

```
NDVI = (NIR - Red) / (NIR + Red)
```

In our simulation:
- NIR proxy = Green channel value
- Red = Red channel value
- Vegetation is identified when NDVI > 0.2

#### Edge Detection
Uses the Sobel operator to detect edges in the image, which often correspond to plant boundaries. This method:
1. Converts the image to grayscale
2. Applies Sobel kernels in both x and y directions
3. Calculates edge magnitude
4. Combines edge detection with green color analysis

## Technical Details

### Built With
- **HTML5 Canvas**: For image rendering and manipulation
- **Vanilla JavaScript**: No frameworks or dependencies
- **CSS3**: Modern styling with CSS variables and Flexbox/Grid
- **File API**: For drag-and-drop image uploads

### Browser Compatibility
- ✅ Chrome (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ⚠️ Internet Explorer (not supported)

### Performance
The app processes images entirely in the browser using the HTML5 Canvas API. Analysis time depends on:
- Image size (larger images take longer)
- Browser performance
- Device capabilities

For best results, use images under 5MB with resolutions up to 4000x4000 pixels.

## Project Structure

```
coverscope-web/
├── index.html          # Main application file
├── README.md           # This file
├── LICENSE             # MIT License
└── .gitignore          # Git ignore file
```

## Customization

### Changing Colors
Edit the CSS variables at the top of `index.html`:

```css
:root {
    --bg-primary: #1a1e1f;
    --bg-secondary: #2a2e2f;
    --accent: #4caf50;
    /* ... */
}
```

### Adding New Analysis Modes
Add a new case to the `performAnalysis()` function switch statement:

```javascript
case 'new-mode':
    analyzeNewMode(data, processed, width, height);
    break;
```

Then implement the `analyzeNewMode()` function.

### Threshold Adjustment
Tune the detection thresholds in each analysis function:
- `analyzeGreen()`: Adjust the green detection parameters
- `analyzeNDVI()`: Modify the NDVI threshold (currently 0.2)
- `analyzeEdges()`: Change the edge magnitude threshold (currently 40)

## Limitations

This is a client-side demonstration with some limitations:

1. **No True AI/ML**: Uses simple color and edge detection algorithms rather than trained machine learning models
2. **No Near-Infrared Data**: Real NDVI requires NIR camera data; this is a simulation
3. **Browser Memory**: Very large images may cause performance issues
4. **Color Accuracy**: Results depend on image lighting and color balance

For production use with higher accuracy, consider:
- Using TensorFlow.js with a trained segmentation model
- Integrating with a backend API for processing
- Using images from specialized agriculture cameras

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by the original CoverScope app on Whacka
- Icon by emoji (🌱)
- Built with standard web technologies (HTML5, CSS3, JavaScript)

## Contact

For questions or feedback, please open an issue on GitHub.

---

**CoverScope** - Measure plant coverage with precise accuracy

*Part of the AI-powered agriculture tools ecosystem*  
