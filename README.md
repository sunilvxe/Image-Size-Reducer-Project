# Image Size Reduction using Pillow and ImageOps

This project demonstrates how to reduce the size of an image while maintaining its quality using the Pillow library in Python. The image is resized and compressed to meet a target file size in kilobytes (KB). The project provides an example of how to load, manipulate, and save images with reduced file sizes.

## Project Structure

- **image_processing.py**: Python script to load an image, resize it, and compress it to meet the target file size.
- **input_images**: Folder containing the input images for processing.
- **output_images**: Folder to save the processed, reduced images.

## Requirements

- Python 3.x
- Pillow library (for image processing)
- Matplotlib (for displaying images)

You can install the required libraries using pip:

```bash
pip install Pillow matplotlib
```

## Key Features

1. **Image Loading and Information Extraction**:
    - Load images from a specified file path using `PIL.Image.open()`.
    - Display the image using `matplotlib.pyplot.imshow()`.
    - Extract image dimensions (width x height) using `image.size`.
    - Calculate file size using `os.path.getsize()`.

2. **Image Size Reduction Function**:
    - **Resize Image**: The image is resized while maintaining the aspect ratio, ensuring the image fits within the specified dimensions (max size).
    - **Initial Compression**: The image is saved with an initial quality of 95% in JPEG format.
    - **Gradual Compression**: If the image file size exceeds the target size, the image quality is gradually reduced by 5% until the target size is met or the quality falls below 10%.
    - **Output**: The processed image is saved with the reduced size, and the file size is printed.

3. **Example Use Case**:
    - Input image: `1000092795.jpg` (from the Flickr30k dataset).
    - Target file size: 50 KB.
    - Final file size after processing: 47.79 KB (quality is maintained).

## Function Breakdown

### `reduce_image_size`

This function performs the image resizing and compression:

```python
def reduce_image_size(image_path, output_path, max_size=(800, 800), target_size_kb=100):
    """
    Reduces the size of an image by resizing and compressing it to a specific target file size.
    
    Args:
        image_path (str): Path to the input image.
        output_path (str): Path to save the reduced image.
        max_size (tuple): Maximum width and height for resizing.
        target_size_kb (int): Target size for the output image in KB.
    """
```

**Steps**:
1. The image is opened using `PIL.Image.open()`.
2. The image is resized to fit within the specified `max_size` while maintaining the aspect ratio.
3. The image is saved with an initial quality of 95%.
4. If the file size exceeds the target size (`target_size_kb`), the quality is reduced by 5% until the file size is under the target.
5. The final image is saved, and the final file size is displayed.

### Example Usage:

```python
if __name__ == "__main__":
    input_path = '/path/to/input/image.jpg'
    output_path = 'reduced_image.jpg'
    target_size_kb = 50  # Set your desired target size in KB
    
    reduce_image_size(image_path=input_path, output_path=output_path, max_size=(800, 800), target_size_kb=target_size_kb)
```

## Example Output:

```plaintext
Image saved at: reduced_image.jpg
Final file size: 47.79 KB
```

## Results

For an input image (`1000092795.jpg`) with an original size of **213.03 KB**, the image was successfully reduced to **47.79 KB** while maintaining its quality.

**Image Dimensions**:  
- Before reduction: `333 x 500` pixels  
- After reduction: `333 x 500` pixels  

## License

This project is licensed under the MIT License.

--
