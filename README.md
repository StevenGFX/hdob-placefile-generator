
# HDOB Placefile Generator

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Node Version](https://img.shields.io/badge/node-%3E%3D14.0.0-brightgreen.svg)](https://nodejs.org/)

HDOB Placefile Generator is a utility for generating placefiles from High-Density Observations (HDOB) data collected from hurricane reconnaissance aircraft. This tool is useful for meteorologists and weather enthusiasts to visualize hurricane data in GRLevelX and similar applications.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Placefile Format](#placefile-format)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- Fetches and parses HDOB data from the National Hurricane Center (NHC) Reconnaissance Archives.
- Generates placefiles compatible with GRLevelX weather radar software.
- Supports unit conversion between metric and imperial.
- Allows configuration of observation parameters, refresh intervals, and output paths.
- Easy-to-customize configuration for user-specific needs.

## Installation

To get started, you need to have [Node.js](https://nodejs.org/) installed. We recommend using Node.js version 14 or higher.

1. Clone the repository:

   ```bash
   git clone https://github.com/stevengfx/hdob-placefile-generator.git
   ```

2. Navigate to the project directory:

   ```bash
   cd hdob-placefile-generator
   ```

3. Install the dependencies:

   ```bash
   npm install
   ```

## Usage

Once you have installed the dependencies, you can generate a placefile by running the following command:

```bash
npm start
```

This will execute the `hdob-placefile-generator.mjs` script, which fetches HDOB data from the NHC archive and generates a placefile in the current directory.

### Command Line Arguments

- By default, the script looks back 1 hour into the HDOB archive. You can adjust the `hoursBack` configuration within the script.
  
### Output

- The output placefile will be saved as `hdob_placefile.txt` in the project root by default. You can customize this path in the configuration section.

## Configuration

You can adjust various settings in the script by modifying the `config` object. Here are the key configuration options:

```javascript
const config = {
  baseUrl: 'https://www.nhc.noaa.gov/archive/recon/2024/', // Base URL for the NHC recon archive
  hoursBack: 1,  // Number of hours to go back in the archive
  windbarbIcons: './assets/Basic_WindBarb_096.png', // Wind barb icons // TODO: Need to fix windbarb icons
  airplaneIcon: './assets/airplane.png', // Airplane icon
  units: 'imperial',  // Choose between 'imperial' or 'metric' units
  outputFilePath: './hdob_placefile.txt',  // Path to save the generated placefile
  refreshInterval: 10,  // Refresh interval for placefile updates (in seconds)
  titlePrefix: 'Hurricane Hunter',  // Prefix for the placefile title
  color: [200, 200, 255],  // RGB color for the placefile header
  timeFormat: '24h',  // Time format: '12h' or '24h'
  pressureUnit: 'mb',  // Pressure unit: 'mb' or 'inHg'
  rainRateUnit: 'mm/hr',  // Rain rate unit: 'mm/hr' or 'in/hr'
  temperaturePrecision: 1,  // Decimal precision for temperature
  windSpeedPrecision: 2  // Decimal precision for wind speed
};
```

## Placefile Format

The generated placefile is designed for GRLevelX and follows the standard format for weather radar placefiles. Here’s an example snippet:

```
Refresh: 10
Title: Hurricane Hunter - 2024-09-26 19:25:00 UTC
Color: 200 200 255
Font: 1, 11, 1, "Courier New"
Threshold: 999

IconFile: 1, 18, 44, 3, 40, "./assets/Basic_WindBarb_096.png"
IconFile: 9, 15, 15, 7, 7, "./assets/airplane.png"

Object: 27.2667,-84.6
  Icon: 0,0,000,9,1,"Date: 17:16:30 UTC\nAircraft Pres: 696.6 mb\nTemp: 55.0°F (30sec avg)\nDew: 48.0°F (30sec avg)\nWind: 37° @ 81.64 knots (30sec avg)\nRain Rate: 1 mm/hr"
  Icon: 0,0,37,1,16
  Text: -17,13,1,"Wind: 81.64 knots"
  Text: -17,-13,1,"Temp: 55.0°F"
End:
```

## Contributing

Contributions are welcome! If you have suggestions, bug reports, or improvements, feel free to open an issue or submit a pull request.

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes.
4. Push your changes (`git push origin feature/your-feature`).
5. Create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Enjoy using HDOB Placefile Generator! If you find this tool helpful, feel free to give a ⭐️ on [GitHub](https://github.com/stevengfx/hdob-placefile-generator)!

---

### Badges and Links:
- [GitHub Repository](https://github.com/stevengfx/hdob-placefile-generator)
- [Issues](https://github.com/stevengfx/hdob-placefile-generator/issues)
