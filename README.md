# EXP1-Image-Handling-and-Pixel-Transformations-Using-OpenCV
AIM:

Write a Python program using OpenCV that performs the following tasks:

Software Required:

.Anaconda - Python 3.7
.Jupyter Notebook (for interactive development and execution)

Algorithm:

Step 1:
Load an image from your local directory and display it.

Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

Step 5:
Split the image (Dolphin.jpg) into B, G, R components and display the channels

Program Developed By:
Name: Litya M

Register Number: 212225230152

program:

Ex. No. 01
1. Read the image ('Dolphin.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import matplotlib.pyplot as plt
img = cv2.imread('dolphin image 1.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)###
3. Print the image width, height & Channel.
h, w = img_rgb.shape[:2]
print(h, w)
```
4. Display the image using matplotlib imshow().
```
plt.imshow(img_rgb, cmap='viridis')
plt.title("Original Image")
plt.axis('off') 
plt.show()
```
5. Save the image as a PNG file using OpenCV imwrite().
```
img = cv2.imread('dolphin image 1.jpg', cv2.IMREAD_GRAYSCALE)
```
7. Read the saved image above as a color image using cv2.cvtColor().
```
image = cv2.imread('dolphin image 1.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
9. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
img = cv2.imread('dolphin image 1.png')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
print("Width =", img_rgb.shape[1])
print("Height =", img_rgb.shape[0])
print("Channel =", img_rgb.shape[2])
plt.imshow(img_rgb)
plt.title("Color Image")
plt.axis('off')
plt.show()
```
11. Crop the image to extract any specific (Dolphin alone) object from the image.
```
image = cv2.imread('dolphin image 1.jpg')
image.shape
roi = image[50:350, 50:350]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```
12. Resize the image up by a factor of 2x.
```
image = cv2.imread('dolphin image 1.jpg')
image.shape
resized_image = cv2.resize(image, (768 // 2, 600 // 2))
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```
13. Flip the cropped/resized image horizontally.
```
image = cv2.imread('dolphin image 1.jpg')
flipped_horizontally = cv2.flip(image, 1)
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
```
14. Horizontal flip
```
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
flipped_vertically = cv2.flip(image, 0)
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```
15. Read in the image ('Dolphin.jpg').
```
img = cv2.imread('dolphin image 1.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
16. Add the following text to the dark area at the bottom of the image (centered on the image):
```
image = cv2.imread('dolphin image 1.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
_ = cv2.putText(img_rgb, "SAADHANA", (10,30),
                cv2.FONT_HERSHEY_SIMPLEX,
                1,
                (255,255,255),  
                2)
```
17. Draw a magenta rectangle that encompasses the Dolphin.
```
rect_color = magenta
image = cv2.imread('dolphin image 1.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
h, w = img_rgb.shape[:2]
plt.imshow(rect_img)
plt.title("Rectangle")
plt.axis('off')
plt.show()
```
18. Display the final annotated image.
```
img = cv2.imread('dolphin image 1.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
h, w = img_rgb.shape[:2]
print(h, w)
plt.imshow(img_rgb, cmap='viridis')
plt.title("Annotated Image")
plt.axis('off')
plt.show()
```
19. Read the image ('Dolphin.jpg').
```
img = cv2.imread('dolphin image 1.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
20. Adjust the brightness of the image.
```
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```
21. Create brighter and darker images.
```
img_brighter = cv2.add(img, matrix) img_darker = cv2.subtract(img, matrix)
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)
```
22. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```
23. Modify the image contrast.
    
```
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```
24. Display the images (Original, Lower Contrast, Higher Contrast).
    
 ```
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```
25. Split the image (Dolphin.jpg) into the B,G,R components & Display the channels.
    
```
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```
26. Merged the R, G, B , displays along with the original image

```
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```
27. Split the image into the H, S, V components & Display the channels.
    
```
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
28. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```
Output:
i) Read and Display an Image.

<img width="477" height="495" alt="image" src="https://github.com/user-attachments/assets/1afbbd93-30a9-4f1c-a8ba-65f5109b877e" />

<img width="462" height="492" alt="image" src="https://github.com/user-attachments/assets/9a866f76-4fd6-4933-a521-159f15a00c84" />

<img width="457" height="495" alt="image" src="https://github.com/user-attachments/assets/325fe4ee-3250-46a1-8dfa-b523464aa0e2" />

<img width="475" height="500" alt="image" src="https://github.com/user-attachments/assets/4ba42b3b-a074-4b48-a4ab-b140c6623a05" />

<img width="462" height="492" alt="image" src="https://github.com/user-attachments/assets/493d05a5-4e97-4e03-bc37-9d18a917e5b5" />

ii) Adjust Image Brightness.

<img width="461" height="492" alt="image" src="https://github.com/user-attachments/assets/9dff2ad0-e257-4189-95e3-2c034b7f3c99" />

<img width="461" height="487" alt="image" src="https://github.com/user-attachments/assets/6cb0d3b3-38e0-41c3-8484-f7ef442f248b" />


<img width="470" height="492" alt="image" src="https://github.com/user-attachments/assets/3df95d57-f4b6-45b1-ab06-622d7ac19538" />

<img width="462" height="487" alt="image" src="https://github.com/user-attachments/assets/944536b4-9fcf-46f1-9952-58a61e69ff71" />


iii) Modify Image Contrast.

<img width="462" height="487" alt="image" src="https://github.com/user-attachments/assets/0bc4d167-1308-4848-9f9d-156f57d2d298" />

iv) Generate Third Image Using Bitwise Operations.

<img width="452" height="496" alt="image" src="https://github.com/user-attachments/assets/3f9b55ae-0957-4bbf-b0af-0275dc6eeeef" />

<img width="546" height="492" alt="image" src="https://github.com/user-attachments/assets/b81b01e9-a711-462f-a311-58f55544a5c1" />

<img width="462" height="491" alt="image" src="https://github.com/user-attachments/assets/bd9e1754-d58f-4e37-ba6d-7d7fc38cfde3" />

<img width="467" height="490" alt="image" src="https://github.com/user-attachments/assets/caf49d9d-64a0-49bb-9359-b5df2b142d1f" />



Result:

Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
