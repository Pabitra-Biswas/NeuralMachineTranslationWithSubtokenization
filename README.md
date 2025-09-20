# NeuralMachineTranslationWithSubtokenization
### Experimental Results Format

The visualization expects data in the following format:

```javascript
// Training Performance Data
const trainingResults = [
  { 
    tokenizer: "BPE",
    validation_loss: 1.99,
    training_loss: 1.65,
    epoch: 3
  },
  { 
    tokenizer: "WordPiece_APE",
    validation_loss: 2.93,
    training_loss: 2.45,
    epoch: 3
  },
  {
    tokenizer: "WordPiece_RoPE", 
    validation_loss: 3.65,
    training_loss: 3.21,
    epoch: 3
  }
];

// Inference Latency Data
const latencyResults = [
  {
    model: "BPE",
    ttft_ms: 7.81,
    tpot_ms: 4.41,
    total_latency_ms: 187.09,
    avg_output_tokens: 41.55
  },
  {
    model: "WordPiece + APE",
    ttft_ms: 7.21,
    tpot_ms: 3.2,
    total_latency_ms: 87.3,
    avg_output_tokens: 17.12
  },
  {
    model: "WordPiece + RoPE", 
    ttft_ms: 10.23,
    tpot_ms: 5.55,
    total_latency_ms: 559.85,
    avg_output_tokens: 100.0
  }
];# Neural Machine Translation Research Visualizations

[![React](https://img.shields.io/badge/React-18.0-blue.svg)](https://reactjs.org/)
[![Recharts](https://img.shields.io/badge/Recharts-2.5-green.svg)](https://recharts.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📊 Project Overview

This project provides interactive visualizations for neural machine translation (NMT) research, comparing three tokenization and positional encoding approaches:
1. **BPE (Byte Pair Encoding)**
2. **WordPiece + Absolute Positional Encoding (APE)**  
3. **WordPiece + Rotary Position Embedding (RoPE)**

The visualizations are designed to support academic research papers with publication-ready charts and comprehensive analysis.

### 🔬 Research Context

Our comprehensive research reveals a clear performance hierarchy:

🥇 **BPE (Winner):** 
- ✅ **Lowest validation loss** (1.99)
- ✅ **Best memory efficiency** (~15% less than APE)
- ✅ **Excellent training convergence**
- ✅ **Balanced output length** (~42 tokens)

🥈 **WordPiece + APE (Runner-up):**
- ✅ **Fast inference speed** (7.21ms TTFT)
- ✅ **Most concise translations** (17 tokens average)
- ✅ **Good overall efficiency**

🥉 **WordPiece + RoPE (Underperformer):**
- ❌ **Highest validation loss** (3.65)
- ❌ **Slowest inference** (10.23ms TTFT)
- ❌ **Excessive memory usage** (~30% more)
- ❌ **Verbose outputs** (100 tokens average)

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** (v16.0 or higher) - [Download here](https://nodejs.org/)
- **npm** or **yarn** package manager
- **VS Code** (recommended) with Live Server extension

### Installation

```bash
# Clone or create project directory
mkdir nmt-visualizations
cd nmt-visualizations

# Initialize React project
npx create-react-app .
```

### Install Dependencies

```bash
# Core visualization libraries
npm install recharts lucide-react

# Optional: For enhanced styling
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### Setup Tailwind CSS (Optional but Recommended)

1. **Configure tailwind.config.js:**
```javascript
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
    "./public/index.html"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

2. **Add to src/index.css:**
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Run the Application

```bash
# Start development server
npm start

# The app will open at http://localhost:3000
```

---

## 📁 Project Structure

```
nmt-visualizations/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── components/
│   │   └── NMTVisualizations.jsx    # Main visualization component
│   ├── data/
│   │   └── experimentData.js        # Research data
│   ├── App.js                       # Main app component
│   ├── App.css                      # Styling
│   └── index.js                     # Entry point
├── package.json
└── README.md
```

---

## 📊 Visualization Components

## 📊 Visualization Components

### 🔽 **Download Features**
Each visualization includes **built-in download functionality**:
- **PNG Export**: High-resolution raster images (perfect for presentations)
- **SVG Export**: Vector graphics (ideal for publications and scaling)
- **One-click download** buttons on every chart
- **Publication-ready quality** with proper resolution and formatting

### 1. **Training Performance Analysis**
![Training Performance](https://img.shields.io/badge/Chart-Line_Chart-blue)

Compares validation loss convergence across all three approaches:
- **X-axis:** Training epochs
- **Y-axis:** Validation loss
- **Key Insight:** BPE achieves the best convergence (1.99), followed by APE (2.93), with RoPE lagging significantly (3.65)
- **Download:** PNG/SVG formats available

### 2. **Inference Latency Breakdown**
![Latency Analysis](https://img.shields.io/badge/Chart-Bar_Chart-green)

Comprehensive latency comparison across all models:
- **TTFT:** Time to First Token
- **TPOT:** Time Per Output Token  
- **Total Latency:** End-to-end inference time
- **Key Insight:** APE offers fastest TTFT, BPE provides balanced performance, RoPE shows significant delays
- **Download:** PNG/SVG formats available

### 3. **Memory Usage Analysis**
![Memory Usage](https://img.shields.io/badge/Chart-Stacked_Bar-orange)

Component-wise memory consumption comparison:
- Token embeddings efficiency
- Position encoding overhead
- Attention computation costs
- Intermediate tensor storage
- **Key Insight:** BPE is most memory efficient, RoPE requires ~30% more than APE
- **Download:** PNG/SVG formats available

### 4. **RoPE Frequency Visualization**
![RoPE Analysis](https://img.shields.io/badge/Chart-Multi_Line-purple)

Detailed analysis of rotary position embedding patterns:
- Multiple frequency components
- Position-dependent rotations
- Computational complexity visualization
- **Key Insight:** Complex RoPE computations don't justify performance trade-offs compared to simpler alternatives
- **Download:** PNG/SVG formats available

### 5. **Output Length Distribution**
![Output Analysis](https://img.shields.io/badge/Chart-Histogram-red)

Translation output length comparison across all models:
- Token count distributions
- Quality vs length analysis
- Translation verbosity patterns
- **Key Insight:** APE generates concise outputs (~17 tokens), BPE produces moderate lengths (~42 tokens), RoPE creates verbose translations (~100 tokens)
- **Download:** PNG/SVG formats available

### 6. **Overall Efficiency Metrics**
![Efficiency Comparison](https://img.shields.io/badge/Chart-Horizontal_Bar-indigo)

Comprehensive performance comparison across all dimensions:
- Training convergence efficiency
- Inference speed performance
- Memory utilization efficiency
- Output quality assessment
- **Key Insight:** BPE leads in training and memory, APE excels in inference speed, RoPE underperforms across all metrics
- **Download:** PNG/SVG formats available't justify performance trade-offs

### 5. **Output Length Distribution**
![Output Analysis]()
![performance_chart (1)](https://github.com/user-attachments/assets/aaeba5b7-17c9-43d7-95a5-9b8f6b38cc47)


Translation output length comparison:
- Token cou<svg xmlns="http://www.w3.org/2000/svg" class="recharts-surface" width="631" height="400" viewBox="0 0 631 400" style="width: 100%; height: 100%;"><title/><desc/><defs><clipPath id="recharts1-clip"><rect x="65" y="5" height="336" width="561"/></clipPath></defs><g class="recharts-cartesian-grid"><g class="recharts-cartesian-grid-horizontal"><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="65" y1="341" x2="626" y2="341"/><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="65" y1="257" x2="626" y2="257"/><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="65" y1="173" x2="626" y2="173"/><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="65" y1="89" x2="626" y2="89"/><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="65" y1="5" x2="626" y2="5"/></g><g class="recharts-cartesian-grid-vertical"><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="65" y1="5" x2="65" y2="341"/><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="345.5" y1="5" x2="345.5" y2="341"/><line stroke-dasharray="3 3" stroke="#ccc" fill="none" x="65" y="5" width="561" height="336" x1="626" y1="5" x2="626" y2="341"/></g></g><g class="recharts-layer recharts-cartesian-axis recharts-xAxis xAxis"><line orientation="bottom" width="561" height="30" x="65" y="341" class="recharts-cartesian-axis-line" stroke="#666" fill="none" x1="65" y1="341" x2="626" y2="341"/><g class="recharts-cartesian-axis-ticks"><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="bottom" width="561" height="30" x="65" y="341" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="65" y1="347" x2="65" y2="341"/><text orientation="bottom" width="561" height="30" stroke="none" x="65" y="349" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="middle" fill="#666"><tspan x="65" dy="0.71em">1</tspan></text></g><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="bottom" width="561" height="30" x="65" y="341" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="345.5" y1="347" x2="345.5" y2="341"/><text orientation="bottom" width="561" height="30" stroke="none" x="345.5" y="349" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="middle" fill="#666"><tspan x="345.5" dy="0.71em">2</tspan></text></g><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="bottom" width="561" height="30" x="65" y="341" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="626" y1="347" x2="626" y2="341"/><text orientation="bottom" width="561" height="30" stroke="none" x="626" y="349" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="middle" fill="#666"><tspan x="626" dy="0.71em">3</tspan></text></g></g></g><g class="recharts-layer recharts-cartesian-axis recharts-yAxis yAxis"><line orientation="left" width="60" height="336" x="5" y="5" class="recharts-cartesian-axis-line" stroke="#666" fill="none" x1="65" y1="5" x2="65" y2="341"/><g class="recharts-cartesian-axis-ticks"><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="left" width="60" height="336" x="5" y="5" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="59" y1="341" x2="65" y2="341"/><text orientation="left" width="60" height="336" stroke="none" x="57" y="341" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="end" fill="#666"><tspan x="57" dy="0.355em">0</tspan></text></g><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="left" width="60" height="336" x="5" y="5" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="59" y1="257" x2="65" y2="257"/><text orientation="left" width="60" height="336" stroke="none" x="57" y="257" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="end" fill="#666"><tspan x="57" dy="0.355em">2</tspan></text></g><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="left" width="60" height="336" x="5" y="5" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="59" y1="173" x2="65" y2="173"/><text orientation="left" width="60" height="336" stroke="none" x="57" y="173" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="end" fill="#666"><tspan x="57" dy="0.355em">4</tspan></text></g><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="left" width="60" height="336" x="5" y="5" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="59" y1="89" x2="65" y2="89"/><text orientation="left" width="60" height="336" stroke="none" x="57" y="89" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="end" fill="#666"><tspan x="57" dy="0.355em">6</tspan></text></g><g class="recharts-layer recharts-cartesian-axis-tick"><line orientation="left" width="60" height="336" x="5" y="5" class="recharts-cartesian-axis-tick-line" stroke="#666" fill="none" x1="59" y1="5" x2="65" y2="5"/><text orientation="left" width="60" height="336" stroke="none" x="57" y="12" class="recharts-text recharts-cartesian-axis-tick-value" text-anchor="end" fill="#666"><tspan x="57" dy="0.355em">8</tspan></text></g></g><text offset="5" transform="rotate(-90, 10, 173)" x="10" y="173" class="recharts-text recharts-label" text-anchor="start" fill="#808080"><tspan x="10" dy="0.355em">Validation Loss</tspan></text></g><g class="recharts-layer recharts-line"><path stroke="#2563eb" stroke-width="3" fill="none" width="561" height="336" class="recharts-curve recharts-line-curve" stroke-dasharray="565.2386474609375px 0px" d="M65,164.6C158.5,185.32,252,206.04,345.5,210.8C439,215.56,532.5,216.75,626,217.94"/><g class="recharts-layer"/><g class="recharts-layer recharts-line-dots"><circle r="3" stroke="#2563eb" stroke-width="3" fill="#fff" width="561" height="336" cx="65" cy="164.6" class="recharts-dot recharts-line-dot"/><circle r="3" stroke="#2563eb" stroke-width="3" fill="#fff" width="561" height="336" cx="345.5" cy="210.8" class="recharts-dot recharts-line-dot"/><circle r="3" stroke="#2563eb" stroke-width="3" fill="#fff" width="561" height="336" cx="626" cy="217.94000000000003" class="recharts-dot recharts-line-dot"/></g></g><g class="recharts-layer recharts-line"><path stroke="#dc2626" stroke-width="3" fill="none" width="561" height="336" class="recharts-curve recharts-line-curve" stroke-dasharray="563.869384765625px 0px" d="M65,139.4C158.5,154.8,252,170.2,345.5,177.2C439,184.2,532.5,185.95,626,187.7"/><g class="recharts-layer"/><g class="recharts-layer recharts-line-dots"><circle r="3" stroke="#dc2626" stroke-width="3" fill="#fff" width="561" height="336" cx="65" cy="139.4" class="recharts-dot recharts-line-dot"/><circle r="3" stroke="#dc2626" stroke-width="3" fill="#fff" width="561" height="336" cx="345.5" cy="177.2" class="recharts-dot recharts-line-dot"/><circle r="3" stroke="#dc2626" stroke-width="3" fill="#fff" width="561" height="336" cx="626" cy="187.7" class="recharts-dot recharts-line-dot"/></g></g><g class="recharts-layer recharts-line"><path stroke="#059669" stroke-width="3" fill="none" width="561" height="336" class="recharts-curve recharts-line-curve" stroke-dasharray="567.2716064453125px 0px" d="M65,181.4C158.5,202.365,252,223.33,345.5,236C439,248.67,532.5,253.045,626,257.42"/><g class="recharts-layer"/><g class="recharts-layer recharts-line-dots"><circle r="3" stroke="#059669" stroke-width="3" fill="#fff" width="561" height="336" cx="65" cy="181.4" class="recharts-dot recharts-line-dot"/><circle r="3" stroke="#059669" stroke-width="3" fill="#fff" width="561" height="336" cx="345.5" cy="236" class="recharts-dot recharts-line-dot"/><circle r="3" stroke="#059669" stroke-width="3" fill="#fff" width="561" height="336" cx="626" cy="257.41999999999996" class="recharts-dot recharts-line-dot"/></g></g></svg>![Uploading performance_chart (1).svg…]()
nt distributions
- Quality vs length analysis
- **Key Insight:** RoPE generates unnecessarily verbose translations

### 6. **Overall Efficiency Metrics**
![Efficiency Radar](https://img.shields.io/badge/Chart-Radar_Chart-indigo)

Comprehensive performance comparison:
- Training convergence
- Inference speed
- Memory efficiency
- Output quality

---

## 🔧 Usage Instructions

### Basic Usage

1. **Replace src/App.js** with the provided visualization component
2. **Start the development server:** `npm start`
3. **Navigate through tabs** to explore different visualizations
4. **Export charts** for your research paper (right-click → Save image)

### Customization

#### Update Research Data
Edit the data objects in the component:

```javascript
const trainingPerformanceData = [
  { epoch: 1, 'WordPiece + APE': 4.2, 'WordPiece + RoPE': 4.8 },
  { epoch: 2, 'WordPiece + APE': 3.1, 'WordPiece + RoPE': 3.9 },
  { epoch: 3, 'WordPiece + APE': 2.93, 'WordPiece + RoPE': 3.65 },
  // Add your experimental data points
];
```

#### Modify Chart Styling
```javascript
<Line 
  type="monotone" 
  dataKey="WordPiece + APE" 
  stroke="#2563eb"        // Change colors
  strokeWidth={3}         // Adjust line thickness
/>
```

#### Add New Visualizations
```javascript
// Add new tab to the tabs array
const tabs = [
  // ... existing tabs
  { id: 'newchart', name: 'Custom Analysis' },
];

// Add corresponding case in renderTabContent()
case 'newchart':
  return (
    <div className="bg-white p-6 rounded-lg shadow-lg">
      <h3 className="text-xl font-bold mb-4">Custom Analysis</h3>
      {/* Your custom chart component */}
    </div>
  );
```

---

## 📈 Research Data Integration

### Experimental Results Format

The visualization expects data in the following format:

```javascript
// Training Performance Data
const trainingResults = [
  { 
    tokenizer: "WordPiece_APE",
    validation_loss: 2.93,
    training_loss: 2.45,
    epoch: 3
  },
  {
    tokenizer: "WordPiece_RoPE", 
    validation_loss: 3.65,
    training_loss: 3.21,
    epoch: 3
  }
];

// Inference Latency Data
const latencyResults = [
  {
    model: "WordPiece + APE",
    ttft_ms: 7.21,
    tpot_ms: 3.2,
    total_latency_ms: 87.3,
    avg_output_tokens: 17.12
  },
  {
    model: "WordPiece + RoPE", 
    ttft_ms: 10.23,
    tpot_ms: 5.55,
    total_latency_ms: 559.85,
    avg_output_tokens: 100.0
  }
];
```

### Loading Your Own Data

```javascript
// Option 1: Import from JSON file
import experimentData from './data/results.json';

// Option 2: Fetch from API
useEffect(() => {
  fetch('/api/experiment-results')
    .then(response => response.json())
    .then(data => setExperimentData(data));
}, []);

// Option 3: Load from CSV (with PapaParse)
import Papa from 'papaparse';

const loadCSVData = (csvFile) => {
  Papa.parse(csvFile, {
    header: true,
    complete: (results) => {
      setData(results.data);
    }
  });
};
```

---

## 🎨 Styling and Themes

### Color Scheme
```javascript
const colors = {
  ape: "#2563eb",        // Blue for APE
  rope: "#dc2626",       // Red for RoPE
  success: "#059669",    // Green for positive metrics
  warning: "#d97706",    // Orange for warnings
  neutral: "#6b7280"     // Gray for neutral elements
};
```

### Responsive Design
All charts are wrapped in `ResponsiveContainer` for automatic resizing:

```javascript
<ResponsiveContainer width="100%" height={400}>
  <LineChart data={data}>
    {/* Chart components */}
  </LineChart>
</ResponsiveContainer>
```

### Dark Mode Support
Add dark mode toggle:

```javascript
const [isDarkMode, setIsDarkMode] = useState(false);

const chartTheme = {
  backgroundColor: isDarkMode ? '#1f2937' : '#ffffff',
  textColor: isDarkMode ? '#f9fafb' : '#374151',
  gridColor: isDarkMode ? '#374151' : '#e5e7eb'
};
```

---

## 📤 Exporting for Publications

### High-Quality Chart Export

1. **Screenshot Method:**
   - Right-click on chart → "Save image as"
   - Use PNG format for best quality

2. **SVG Export (Recommended):**
   ```javascript
   // Add SVG export functionality
   const exportSVG = (chartRef) => {
     const svgElement = chartRef.current.querySelector('svg');
     const svgData = new XMLSerializer().serializeToString(svgElement);
     const blob = new Blob([svgData], {type: 'image/svg+xml'});
     const url = URL.createObjectURL(blob);
     
     const link = document.createElement('a');
     link.href = url;
     link.download = 'chart.svg';
     link.click();
   };
   ```

3. **PDF Generation:**
   ```bash
   # Install jsPDF for PDF export
   npm install jspdf html2canvas
   ```

### Publication-Ready Settings

```javascript
const publicationConfig = {
  width: 800,           // Standard figure width
  height: 600,          // Standard figure height
  fontSize: 14,         // Readable font size
  strokeWidth: 2,       // Clear line visibility
  margins: {            // Proper margins
    top: 40,
    right: 40,
    bottom: 60,
    left: 80
  }
};
```

---

## 🛠️ Development

### Available Scripts

```bash
npm start          # Run development server
npm test           # Run test suite
npm run build      # Build for production
npm run eject      # Eject from Create React App (irreversible)
```

### Development Guidelines

1. **Code Structure:**
   - Keep components modular
   - Use meaningful variable names
   - Comment complex calculations

2. **Performance:**
   - Use React.memo for expensive components
   - Implement lazy loading for large datasets
   - Optimize re-renders with useMemo/useCallback

3. **Accessibility:**
   - Add proper ARIA labels
   - Ensure color contrast meets WCAG guidelines
   - Support keyboard navigation

### Adding New Research Metrics

```javascript
// 1. Define new data structure
const newMetricData = [
  // Your metric data
];

// 2. Add tab configuration
const newTab = { id: 'newmetric', name: 'New Metric' };

// 3. Implement visualization component
const renderNewMetric = () => (
  <ResponsiveContainer width="100%" height={400}>
    <YourChartType data={newMetricData}>
      {/* Chart configuration */}
    </YourChartType>
  </ResponsiveContainer>
);
```

---

## 📚 Dependencies

### Core Dependencies
```json
{
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "recharts": "^2.5.0",
  "lucide-react": "^0.263.1"
}
```

### Development Dependencies
```json
{
  "tailwindcss": "^3.3.0",
  "autoprefixer": "^10.4.14",
  "postcss": "^8.4.24"
}
```

### Optional Enhancements
```bash
# For CSV data loading
npm install papaparse

# For PDF export
npm install jspdf html2canvas

# For advanced animations  
npm install framer-motion

# For data processing
npm install lodash
```

---

## 🐛 Troubleshooting

### Common Issues

#### Charts Not Rendering
**Problem:** Blank chart area
**Solution:** 
```javascript
// Check data format
console.log('Chart data:', data);

// Ensure ResponsiveContainer has dimensions
<ResponsiveContainer width="100%" height={400} minHeight={300}>
```

#### Styling Issues
**Problem:** Tailwind classes not applying
**Solution:**
```javascript
// Verify tailwind.config.js content paths
content: [
  "./src/**/*.{js,jsx,ts,tsx}",
],

// Check if Tailwind CSS is imported in index.css
@tailwind base;
@tailwind components; 
@tailwind utilities;
```

#### Performance Issues
**Problem:** Slow rendering with large datasets
**Solution:**
```javascript
// Use data sampling for large datasets
const sampledData = useMemo(() => 
  data.length > 1000 ? 
    data.filter((_, index) => index % 10 === 0) : 
    data
, [data]);

// Implement virtualization for large lists
import { FixedSizeList } from 'react-window';
```

#### Build Errors
**Problem:** Build fails in production
**Solution:**
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install

# Check for unused imports
npm run build 2>&1 | grep "unused"
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 NMT Research Project

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request.

### Development Setup
```bash
git clone https://github.com/yourusername/nmt-visualizations
cd nmt-visualizations
npm install
npm start
```

### Contribution Guidelines
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📞 Support

- 📧 **Email:** your.email@university.edu
- 🐛 **Issues:** [GitHub Issues](https://github.com/yourusername/nmt-visualizations/issues)
- 📖 **Documentation:** [Project Wiki](https://github.com/yourusername/nmt-visualizations/wiki)
- 💬 **Discussion:** [GitHub Discussions](https://github.com/yourusername/nmt-visualizations/discussions)

---

## 🙏 Acknowledgments

- **Recharts** team for excellent charting library
- **React** team for the amazing framework
- **Tailwind CSS** for utility-first styling
- **Research collaborators** and **reviewers**

---

## 📊 Research Citation

If you use this visualization tool in your research, please cite:

```bibtex
@misc{nmt-visualizations-2024,
  title={Neural Machine Translation Research Visualizations: Comparative Analysis of Tokenization and Positional Encoding Strategies},
  author={Your Name},
  year={2024},
  howpublished={\url{https://github.com/yourusername/nmt-visualizations}},
  note={Interactive visualization tool for NMT research analysis}
}
```

---

**⭐ Star this repository if it helped your research!**

---

*Last updated: September 2025*
