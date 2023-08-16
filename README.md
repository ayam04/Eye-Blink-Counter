# Blink Detection using FaceMesh and Live Plot

This code uses the `cv2`, `cvzone.FaceMeshModule`, and `cvzone.PlotModule` libraries to detect blinks using facial landmarks obtained from the FaceMesh model. It also displays a live plot of the blink ratio over time.

## Requirements

- OpenCV (`cv2`)
- cvzone library (with FaceMesh and PlotModule)

## Usage

1. Install the required libraries using pip:

```bash
pip install opencv-python
pip install cvzone
```

2. Import the necessary modules:

```python
import cv2
import cvzone
from cvzone.FaceMeshModule import FaceMeshDetector
from cvzone.PlotModule import LivePlot
```

3. Initialize the video capture from the camera:

```python
cap = cv2.VideoCapture(0)
```

4. Create a FaceMesh detector:

```python
detector = FaceMeshDetector(maxFaces=1)
```

5. Initialize a live plot for blink ratio visualization:

```python
plotY = LivePlot(640, 360, [20, 50], invert=True)
```

6. Define face landmarks to be highlighted and set up other necessary variables:

```python
idList = [22, 23, 24, 26, 110, 157, 158, 159, 160, 161, 130, 243]
ratioList = []
blinkCounter = 0
counter = 0
color = (255, 0, 255)
```

7. Start the main loop for processing frames:

```python
while True:
    # ... (read and process frames, compute blink ratio)
    cv2.imshow("Video", imgStack)
    cv2.waitKey(25)
```

8. When done, release the video capture and close the OpenCV windows:

```python
cap.release()
cv2.destroyAllWindows()
```

## Functionality

The code processes video frames captured from a camera and uses the FaceMesh model to detect facial landmarks. It calculates the ratio between vertical and horizontal distances of certain facial landmarks. If the blink ratio falls below a threshold, it's considered a blink. The blink count is displayed on the screen along with a live plot of the blink ratio over time.

Please make sure to replace `VIDEO_FILE.mp4` with the actual video file name if you want to use a video file instead of the camera feed.

Keep in mind that this code assumes you have the required libraries (`cv2`, `cvzone.FaceMeshModule`, and `cvzone.PlotModule`) installed and properly set up.