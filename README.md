# Force Tester Data Visualization

A Streamlit application for visualizing force tester data from Excel files. This tool helps users analyze mechanical test data by automatically grouping replicates, allowing detailed customization, and enabling configuration persistence.

## Features

- **Excel Data Import**: Supports Zwick Force Tester exports with paired x-y data columns ("Values Series") and result summaries ("Results Series").
- **Smart Grouping**: Automatically groups test replicates based on sample naming conventions (e.g., `sample-1`, `sample-2` are grouped as `sample`).
- **Interactive Visualization**: Zoom, pan, and hover over data points using Plotly interactive charts.
- **Customizable Styling**:
    - **Colors**: Assign specific colors to sample groups manually or use preset palettes.
    - **Line Styles**: Choose between solid, dashed, or dash-dot lines.
    - **Legend Names**: Rename groups directly in the UI for cleaner presentation.
- **Configuration Management**:
    - **Save/Load Settings**: Export your chart customization (colors, axes limits, titles) to a JSON file.
    - **Restore Work**: Re-upload your data and JSON config to instantly restore your exact chart view.
- **Data Export**: Download a filtered Excel file containing only the visible/selected data series.

## Installation

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Run the application:
```bash
streamlit run app.py
```

## Usage

1. **Prepare Data**:
   - Export data from TestExpert software.
   - Ensure the export includes "Results Series" and "Values Series" sheets.
   - Update export options to group by series.

2. **Upload File**:
   - Launch the app and upload your `.xlsx` file.

3. **Customize Chart**:
   - Use the **"Configure Test Groups"** section to toggle visibility, change colors, and rename legend items.
   - Use **"Chart Configuration"** to set titles, axis labels, font sizes, and specific axis ranges.

4. **Save Your Work**:
   - Expand the **"Import / Export Chart Settings"** section.
   - Click **"💾 Download Config"** to save your current styling.
   - Next time, upload this JSON file to restore your settings.

## Data Format Requirements

The application expects an Excel file with two specific sheets:

1.  **Values Series**: Contains the raw measurement data.
    *   Row 0: Sample Name
    *   Row 1: Measurement Type (e.g., "Standard travel", "Standard force")
    *   Row 2: Units
    *   Row 3+: Data points
    *   *Columns must be paired (Travel, Force) for each sample.*

2.  **Results Series**: Contains summary results and sample names used for validation.
