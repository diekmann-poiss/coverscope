# CoverScope - Plant Coverage Measurement

Precise, deterministic plant coverage measurement that works entirely on your device.

**📍 Repository:** https://github.com/diekmann-poiss/coverscope

## Features

### Analyze Tab
- **Load Photo** - Upload/drag & drop, auto-downscaled to 640px
- **Calibrate Scale** - 2-point reference for real-world measurements (m/ft)
- **Excess-Green Index Analysis** - Standard remote-sensing formula: `(2×Green) − Red − Blue`
- **Sensitivity Slider** - Aggressive (faint green) to Conservative (strong green)
- **Target Area** - Resizable box for specific region analysis
- **1m² Square** - Projective square with instant coverage %
- **Cubic Volume** - 5-point height input for volume estimation
- **Manual Correction** - Brush tool with Add/Erase modes
- **Toggle Overlay** - Verify detection results

### History Tab
- View all saved measurements
- Editable names
- Coverage %, area, health index
- Select for comparison

### Compare Tab
- Bar chart comparison
- **Excel Export** (.xlsx)
- **PDF Export**

### Methods Info
- Comprehensive methodology explanation
- Formula details
- Application use cases

## How It Works

**Excess-Green Index:** `ExG = (2 × Green) − Red − Blue`

Healthy green vegetation reflects strongly in green while absorbing red and blue light.

**Health Index:** `(Average Green Saturation + Average Green Value) / 2`

**Scale Calibration:** `metresPerPixel = realDistance / pixelDistance`

**Plant Area:** `plantPixels × (metresPerPixel)²`

## Limitations

- Color-based detection, not AI species recognition
- May under-count very yellow/dry or shadowed vegetation
- Manual brush provided for edge cases

## Technical Stack

- HTML5 Canvas for image processing
- Pure JavaScript (no frameworks)
- jsPDF for PDF export
- SheetJS for Excel export
- localStorage for data persistence

## License

MIT License
