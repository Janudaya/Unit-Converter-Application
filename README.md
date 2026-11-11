# Unit Converter Application (Android Studio · Java · XML)

A modern, responsive, and robust Android application built with **Java** and **XML** that converts values across measurement categories: **Length**, **Weight**, **Temperature**, **Volume**, and **Speed**.

---

## 📱 Feature Checklist Compliance

| Feature | Status | Details |
| :--- | :---: | :--- |
| **Input field for numeric value** | ✅ | `EditText` with `numberDecimal\|numberSigned` supporting positive and negative numbers (e.g., negative temperatures). |
| **Dropdown (Spinner) for Source Unit** | ✅ | `Spinner` dynamically populated with category-specific units (symbol & name). |
| **Dropdown (Spinner) for Target Unit** | ✅ | `Spinner` with automatic default selection (Source: index 0, Target: index 1). |
| **Convert Button** | ✅ | Prominent `Button` triggering conversion calculation, formatting, and formula breakdown. |
| **Result TextView** | ✅ | Formats converted value with commas, precision capping, and unit symbol (e.g. `39.3701 in`). |
| **At least 3 measurement categories** | ✅ | Supports **5 categories**: Length, Weight, Temperature, Volume, and Speed. |
| **Input Validation & Toast feedback** | ✅ | Checks for empty string, non-numeric values, negative checks (length/mass), and absolute zero (-273.15°C / 0K). |
| **Category Selector** | ✅ | Category `Spinner` that resets and re-populates both unit spinners dynamically. |
| **Bonus Polish Features** | ✅ | **Swap Units Button** (instant reversal), **Quick Clear Button**, **One-Tap Copy to Clipboard**, **Formula Breakdown**, and **Dark Mode Support**. |

---

## 🗂️ Project Structure

```text
UnitConverterApp/
├── app/
│   ├── build.gradle                              # App-level build config (compileSdk 34, minSdk 24)
│   ├── proguard-rules.pro
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml               # App manifest with theme and launcher activity
│       │   ├── java/com/example/unitconverter/
│       │   │   ├── MainActivity.java             # Controller handling UI, events & validation
│       │   │   └── converter/
│       │   │       ├── Category.java             # Category domain model
│       │   │       ├── Unit.java                 # Unit domain model
│       │   │       └── UnitConverter.java        # Core conversion logic & math engine
│       │   └── res/
│       │       ├── drawable/                     # Custom rounded backgrounds, ripples, vector icons
│       │       ├── layout/
│       │       │   ├── activity_main.xml         # Main UI layout (ScrollView, Cards, Spinners)
│       │       │   ├── spinner_item.xml          # Spinner selected item view
│       │       │   └── spinner_dropdown_item.xml # Spinner dropdown item view
│       │       ├── values/
│       │       │   ├── colors.xml                # Modern Material design color scheme
│       │       │   ├── strings.xml               # Centralized text and error strings
│       │       │   └── themes.xml                # App theme styling
│       │       └── values-night/
│       │           └── themes.xml                # Night / Dark mode theme styling
│       └── test/java/com/example/unitconverter/
│           └── UnitConverterTest.java            # Comprehensive JUnit 4 test suite
├── gradle/wrapper/gradle-wrapper.properties      # Gradle 8.4 wrapper configuration
├── build.gradle                                  # Top-level Gradle configuration
├── settings.gradle                               # Project settings
└── README.md                                     # Project guide and documentation
```

---

## 📐 Conversion Categories & Formulas

### 1. Length (Base: Meter `m`)
- **Millimeter (`mm`)**: $\times 0.001$
- **Centimeter (`cm`)**: $\times 0.01$
- **Meter (`m`)**: $\times 1.0$
- **Kilometer (`km`)**: $\times 1000.0$
- **Inch (`in`)**: $\times 0.0254$ ($1\text{ in} = 2.54\text{ cm}$)
- **Foot (`ft`)**: $\times 0.3048$ ($1\text{ ft} = 12\text{ in}$)
- **Yard (`yd`)**: $\times 0.9144$ ($1\text{ yd} = 3\text{ ft}$)
- **Mile (`mi`)**: $\times 1609.344$ ($1\text{ mi} = 5280\text{ ft}$)

### 2. Weight / Mass (Base: Kilogram `kg`)
- **Milligram (`mg`)**: $\times 10^{-6}$
- **Gram (`g`)**: $\times 0.001$
- **Kilogram (`kg`)**: $\times 1.0$
- **Metric Ton (`t`)**: $\times 1000.0$
- **Ounce (`oz`)**: $\times 0.028349523$ ($1\text{ oz} \approx 28.35\text{ g}$)
- **Pound (`lb`)**: $\times 0.45359237$ ($1\text{ lb} = 16\text{ oz}$)
- **Stone (`st`)**: $\times 6.35029318$ ($1\text{ st} = 14\text{ lb}$)

### 3. Temperature (Affine Transformations)
- **Celsius to Fahrenheit**: $F = (C \times \frac{9}{5}) + 32$
- **Fahrenheit to Celsius**: $C = (F - 32) \times \frac{5}{9}$
- **Celsius to Kelvin**: $K = C + 273.15$
- **Kelvin to Celsius**: $C = K - 273.15$
- **Fahrenheit to Kelvin**: $K = (F - 32) \times \frac{5}{9} + 273.15$
- **Kelvin to Fahrenheit**: $F = (K - 273.15) \times \frac{9}{5} + 32$
- *Validation Rule:* Values below absolute zero ($-273.15^\circ\text{C}$, $-459.67^\circ\text{F}$, $0\text{ K}$) display an alert Toast.

### 4. Volume (Base: Liter `L`)
- **Milliliter (`mL`)**: $\times 0.001$
- **Liter (`L`)**: $\times 1.0$
- **Cubic Meter (`m³`)**: $\times 1000.0$
- **Fluid Ounce US (`fl oz`)**: $\times 0.0295735$
- **Cup US (`cup`)**: $\times 0.236588$
- **Pint US (`pt`)**: $\times 0.473176$
- **Quart US (`qt`)**: $\times 0.946353$
- **Gallon US (`gal`)**: $\times 3.78541$

### 5. Speed (Base: Meter per second `m/s`)
- **Meter per second (`m/s`)**: $\times 1.0$
- **Kilometer per hour (`km/h`)**: $\times \frac{1}{3.6} \approx 0.27778$
- **Mile per hour (`mph`)**: $\times 0.44704$
- **Knot (`kn`)**: $\times 0.51444$
- **Foot per second (`ft/s`)**: $\times 0.3048$

---

## 🚀 How to Run in Android Studio

1. **Launch Android Studio**.
2. Select **Open** (or **File > Open...**).
3. Browse to this directory:
   `C:\Users\JANUDAYA\UnitConverterApp`
4. Wait for Gradle sync to complete automatically.
5. Select an Android Virtual Device (AVD Emulator) or a connected Android device.
6. Click the green **Run** button (or press `Shift + F10`).
