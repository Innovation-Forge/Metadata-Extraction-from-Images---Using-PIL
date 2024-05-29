# GPS Metadata Extractor Script

## Introduction

The GPS Metadata Extractor script processes JPEG images in a specified directory to extract GPS metadata. It uses the `PIL` library to read image EXIF data, identifies GPS information, converts it to latitude and longitude, and saves the results in a CSV file. Additionally, it generates a report using `PrettyTable` to display the extracted GPS coordinates in a readable table format.

## Features

- **Extract GPS Metadata**: Extracts GPS information from JPEG images.
- **Convert GPS Data**: Converts GPS coordinates to latitude and longitude.
- **Save Results to CSV**: Saves the extracted GPS data to a CSV file.
- **Display Results**: Generates a report using `PrettyTable` to display the GPS coordinates.

## Prerequisites

- Python 3.6 or higher.
- Required Python libraries: `PIL` (Pillow), `prettytable`.

## Modules

- **os**: Provides functions for interacting with the operating system.
- **PIL (Pillow)**: Provides functions to read image data and extract EXIF metadata.
- **binascii**: Converts binary data to hexadecimal.
- **csv**: Provides functions to handle CSV files.
- **prettytable**: Generates readable table formats for displaying data.

```python
import os
from PIL import Image
from PIL.ExifTags import TAGS, GPSTAGS
import csv
from prettytable import PrettyTable
```

## Functions

### `extract_gps_dictionary(file_name)`

Extracts the GPS dictionary from an image file.

- **Parameters:**
  - `file_name` (str): The path to the image file.
- **Returns:**
  - `dict`: A dictionary containing GPS metadata.
  - `dict`: A dictionary containing all EXIF data.

### `extract_lat_lon(gps)`

Converts GPS data to latitude and longitude.

- **Parameters:**
  - `gps` (dict): The GPS metadata dictionary.
- **Returns:**
  - `tuple`: A tuple containing latitude and longitude.

### `convert_to_degrees(value, ref)`

Converts GPS coordinates to degrees.

- **Parameters:**
  - `value` (tuple): The GPS coordinate value.
  - `ref` (str): The GPS coordinate reference (N/S/E/W).
- **Returns:**
  - `float`: The GPS coordinate in degrees.

### `process_images(directory)`

Processes all JPEG images in the specified directory to extract GPS data.

- **Parameters:**
  - `directory` (str): The path to the directory containing JPEG images.
- **Returns:**
  - `None`

## Usage

1. **Set the Directory Path**: Enter the directory path containing JPEG images when prompted.

    ```python
    directory_path = input("Enter the path to the directory containing JPEG files: ")
    ```

2. **Run the Script**: Execute the script in your Python environment.

    ```bash
    python script_name.py
    ```

3. **Output**: The script will save the extracted GPS data to `gps_coordinates.csv` and display the results in a table format.

## Example Output

```plaintext
+-----------+----------+-----------+
| File Name | Latitude | Longitude |
+-----------+----------+-----------+
|  image1.jpg  | 12.34567 | 89.12345  |
|  image2.jpg  | 23.45678 | 78.23456  |
+-----------+----------+-----------+
```

## Error Handling

- **Non-Image Files**: If a file is not a valid image or does not contain EXIF data, an error message is displayed.
- **Invalid GPS Data**: If the GPS data cannot be converted, an error message is displayed.

## Security Considerations

- **Input Validation**: Ensure the directory path provided does not contain sensitive or unauthorized information.
- **Permission Handling**: Make sure the script has appropriate permissions to read files in the specified directory.

## FAQs

**Q: What happens if the directory is empty?**
A: The script will simply prompt for another directory or to quit.

**Q: Can the script process large directories?**
A: Yes, the script uses `os.walk` to iterate through directories and files, making it efficient for large directories.

**Q: How does the script handle different file types?**
A: The script processes only JPEG files with `.jpg` extensions.

## Troubleshooting

- **Invalid Directory Path**: Ensure that the directory path is correct and accessible.
- **Module Not Found Errors**: Make sure Python is installed correctly and all necessary modules are available.

For further assistance or to report bugs, please reach out to the repository maintainers or open an issue on the project's issue tracker.
