# CoverScope - Plant Coverage Measurement

Precise, deterministic plant coverage measurement that works entirely on your device.

**📍 Repository:** https://github.com/diekmann-poiss/coverscope

## Features

### Analyse Tab
- **Load Photo** - Upload/drag & drop, auto-downscaled to 640px
- **Calibrate Scale** - 2-point reference for real-world measurements (m/ft)
- **Excess-Green Index Analysis** - Standard remote-sensing formula: `(2 × G) − R − B`
- **Sensitivity Slider** - Aggressive (faint green) to Conservative (strong green)
- **Target Area** - Resizable box for specific region analysis
- **1 m² Square** - Projective square with instant coverage %
- **Cubic Volume** - 5-point height input for volume estimation
- **Manual Correction** - Brush tool with Add/Erase modes
- **Toggle Overlay** - Verify detection results

### History Tab
- View all saved measurements
- Editable names
- Coverage %, area, health index
- Delete measurements
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

**Excess-Green Index:** `ExG = (2 × G − R − B) / 255`

Healthy green vegetation reflects strongly in green while absorbing red and blue light.

**Health Index:** `(Average Green Saturation + Average Green Value) / 2`

**Scale Calibration:** `metresPerPixel = realDistance / pixelDistance`

**Plant Area:** `plantPixels × (metresPerPixel)²`

## Methodology

### RGB Vegetation Indices
CoverScope uses a multi-method voting ensemble with 10 indices from peer-reviewed vegetation remote sensing research. A pixel is classified as plant when it receives sufficient votes (1 Aggressive / 2 Moderate / 3 Conservative) AND green dominates red and blue channels.

- **ExG:** `(2 × G − R − B) / 255` (Woebbecke 1995) — primary greenness amplification.
- **ExG_norm:** `2 × G − R − B` (non-normalised).
- **CIVE:** `(G − R) / (G + R + B)` (Kataoka 2003) — crop/background discrimination, brightness-invariant.
- **GRNDVI:** `(G − R) / (G + R)` — RGB-adapted NDVI for green-red contrast (Gitelson).
- **VARI:** `(G − R) / (G + R − B)` (Gitelson 2002) — atmospherically resistant for stable outdoor detection.
- **ExGR:** `(2 × G − R − B) − (1.4 × R − G)` (Mexson 2010) — ExG with red suppression for soil/flower separation.
- **Enhanced ExG:** `ExG × (G / (R + B + 1))` — ExG weighted by green proportion.

### HSV Colour Space
- **Hue:** `30°–190°` (green to yellow-green)
- **Saturation:** `> 0.05` (catches dark greens)
- **Value:** `> 0.05`

### Additional Methods
- **Bright Green:** `G > 80 ∧ R < 0.9 × G ∧ B < 0.9 × G`
- **Yellow-Green:** `Hue 30°–80° ∧ G > 70 ∧ G > R ∧ G > B`

### Voting & Thresholds
Adaptive thresholds: `base = 0.03–0.22 (sensitivity-dependent) × brightness_factor`. All indices use lenient thresholds for dark/yellow-green detection.

## Limitations

- Colour-based detection, not AI species recognition
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
