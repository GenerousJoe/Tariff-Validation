Process Document 
for 
Tariff Cleaning and Consolidation System
1. Overview
This solution provides a streamlined approach to clean, standardise, and consolidate tariff data from CSV files. It includes a Python-based processing script and a user-friendly Flask web interface for ease of use.
2. Features
A. Python Processing Script
Data Cleaning:
Standardises service names using uppercase formatting and custom replacements (e.g., 'VIT C' → 'VITAMIN C').
Removes special characters and applies consistent formatting.
Fuzzy Matching & Consolidation:
  - Uses `rapidfuzz` to identify and merge similar names (threshold: 75% similarity).
  - Ensures prices are merged using the maximum value found across duplicates.
- Category Normalization:
  - Strips and capitalizes category fields.
  - Handles missing or malformed categories gracefully.
- Output Generation:
  - Saves the cleaned and consolidated CSV to the user-specified location.
  - Supports UTF-8 and fallback to Latin1 encodings for broader compatibility.
B. Flask Web Interface (app.py)
- Homepage: Simple landing page for user navigation.
- Tariff Upload Interface:
  - Users can upload raw tariff CSV files through a web form.
  - Backend processes the file using the `process_tariff` function.
  - Flash messages provide real-time feedback on success or errors.
- File Download:
  - A download link is provided for the cleaned file.
  - Users can download the result directly from the browser.
3. How to Use
Option A: Command-Line (Script Only)
1. Run `main()` from the script.
2. A file dialog prompts you to select an input CSV file.
3. Choose a destination for the cleaned file.
4. Processed file is saved, and a confirmation message is shown in the terminal.
Option B: Web Interface
1. Start the server:
   python app.py
2. Visit http://127.0.0.1:5000/ in your browser.
3. Navigate to 'Upload Tariff'.
4. Select a tariff CSV file and submit.
5. Download the cleaned file via the provided link.
4. File Structure
project/
├── app.py                  # Flask web interface
├── validate_tariff.py      # Main tariff processing script
├── medication.py           # Additional processing logic (e.g., inventory)
├── templates/
│   ├── index.html          # Homepage template
│   └── upload_tariff.html  # Upload & result interface
├── uploads/                # Temporary file storage
5. Dependencies
Install required libraries using:
pip install pandas numpy rapidfuzz flask
6. Notes
- Ensure all CSV files have the columns: name, category, and price.
- Handle missing files or incorrect formats through validation built into the script.
- This system is modular and can be extended to support more processing types (e.g., inventory).
