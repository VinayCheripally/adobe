Shape Detection and Contour Analysis

This project provides a Python script for reading and processing CSV files containing polylines, generating an image with those polylines, detecting shapes in the image using contours, and saving the detected shapes back into a CSV file.
Features

    CSV Reading: The script reads CSV files containing coordinates of polylines and processes them into a structured format.
    Polyline Drawing: The polylines are drawn on a blank image using OpenCV.
    Shape Detection: The script detects different shapes (lines, triangles, quadrilaterals, pentagons, hexagons, circles) in the image based on contours.
    Contour Analysis: It calculates and displays the shapes' circularity and other properties, labeling the shapes on the output image.
    CSV Writing: The detected contours are written into a new CSV file, with each shape separated by an empty line.
    Visualization: The script uses Matplotlib to display the processed image with detected shapes labeled.

Requirements

    Python 3.x
    OpenCV
    NumPy
    Matplotlib

You can install the required libraries using pip:

bash

pip install opencv-python numpy matplotlib

Usage

    Input CSV File: Prepare a CSV file (isolated.csv) containing polylines' coordinates. Each polyline should be identified by a unique ID in the first column.

    Run the Script:
        Place your CSV file in the project directory.
        Execute the script:

    bash

    python shape_detection.py

    Output:
        The script will generate an image displaying the detected shapes and label them accordingly.
        The detected contours will be written to a new CSV file named output_polylines.csv.
        The image will be displayed using Matplotlib.

Functions
read_csv_(csv_path)

    Description: Reads a CSV file and organizes the data into a list of polylines.
    Parameters:
        csv_path: The path to the CSV file.
    Returns: A list of paths where each path is a list of polylines.

polylines_to_image(paths_XYs, width=500, height=500, thickness=1)

    Description: Draws the polylines on a blank image.
    Parameters:
        paths_XYs: The list of polylines.
        width: Width of the image.
        height: Height of the image.
        thickness: Thickness of the polylines.
    Returns: A grayscale image with the drawn polylines.

write_polylines_to_csv(contours, filename)

    Description: Writes the detected contours into a CSV file.
    Parameters:
        contours: The contours to write.
        filename: The name of the output CSV file.

Example

python

gray_image = polylines_to_image(read_csv_("content/isolated.csv"))

_, thresh_image = cv2.threshold(gray_image, 220, 255, cv2.THRESH_BINARY)
contours, hierarchy = cv2.findContours(thresh_image, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)

# Process and visualize contours

License

This project is licensed under the MIT License - see the LICENSE file for details.
