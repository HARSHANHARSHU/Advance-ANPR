# Advance-ANPR
_________________________________________________________________________________________
If my code is not opening download it as zip and extract it 
_________________________________________________________________________________________
This Python program is designed to process images with the goal of identifying license plates within them. It begins by improving the image quality by reducing noise and detecting edges. It then looks for contours, focusing on those with four sides as potential license plates. Once a suitable contour is identified, it extracts the license plate region from the image and saves it as a separate file. The code also uses the Tesseract OCR engine to recognize and display the text found on the license plate. In essence, this code automates the task of extracting and reading license plate information from images, making it useful for tasks such as vehicle identification and data extraction.
1. **Importing Libraries**:
   - `opencv-python` and `pytesseract` libraries are imported. These are used for image processing and OCR, respectively.

2. **Setting Up Environment**:
   - Various imports, such as `random`, `os`, `numpy`, and `matplotlib`, are used to manage and visualize the image processing steps.
   - The `images_dir` variable is set to the path where the images are stored.
   - `image_files` is a list of file names in the `images_dir`.
   - `image_path` is an incorrectly formatted path. It should specify a particular image file within the directory, but it combines the directory and an incorrect path.

3. **Loading and Preprocessing an Image**:
   - An image (`download.jpeg`) is loaded using OpenCV's `cv2.imread` method.
   - The image is then converted to grayscale using `cv2.cvtColor`.
   - The grayscale image is displayed using `matplotlib`.

4. **Plotting Utility**:
   - A function `plot_images` is defined to display two images side by side using `matplotlib`.

5. **Image Processing**:
   - Bilateral filtering is applied to the grayscale image to reduce noise.
   - The Canny edge detection algorithm is used to detect edges in the filtered image.
   - Images at different stages of processing are displayed using the `plot_images` function.

6. **Contour Detection**:
   - Contours are found in the edge-detected image using `cv2.findContours`.
   - A copy of the original image (`image_copy`) is created to draw the contours on.
   - The detected contours are drawn on the `image_copy` using `cv2.drawContours`.
   - The images before and after contour detection are displayed.

7. **Selecting License Plate Contour**:
   - The detected contours are sorted by area in descending order, and the top 30 contours are selected.
   - A loop iterates through these contours to find a contour with four edges (representing a potential license plate).
   - Once a suitable contour is found, the coordinates are used to extract the license plate region from the original image.

8. **Saving the License Plate Image**:
   - The extracted license plate region is saved as "harshu.jpg" using `cv2.imwrite`.
   - The same image is displayed twice using `plot_images`.

9. **Installing Tesseract OCR**:
   - Tesseract OCR is installed using `!sudo apt install tesseract-ocr`.

10. **Performing OCR**:
    - The `pytesseract.image_to_string` function is used to perform OCR on the extracted license plate image (`plate`).
    - The recognized text is stored in the `text` variable.

11. **Printing OCR Result**:
    - The recognized text is printed to the console.

Note: There are a few issues in the code that should be corrected:
- The `image_path` variable is incorrectly formatted.
- Some of the image paths are hard-coded, which may not work if the code is run in a different environment.
- The code assumes that a suitable license plate contour is found, but this may not always be the case in all images.
- There might be issues with the actual file paths and permissions when running this code in your environment.
