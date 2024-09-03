# Sign Language Recognition Using MediaPipe

## Overview
The **Sign Language Recognition** project is a real-time system that interprets basic hand signs using the MediaPipe framework and OpenCV. The project can detect and recognize five hand signs—"Stop," "Forward," "Backward," "Left," and "Right"—from a live webcam feed, displaying the corresponding command on the screen.

This project demonstrates how computer vision can be applied to facilitate non-verbal communication, offering potential applications in accessibility, robotics, and more.

## Features
- **Real-Time Detection:** Processes live video feed from a webcam to recognize hand signs.
- **Sign Recognition:** Identifies five distinct hand gestures and displays the corresponding command.
- **Visualization:** Draws hand landmarks and connections, providing visual feedback on detected gestures.

## Dependencies
To run this project, you need the following Python libraries:
- OpenCV
- MediaPipe

You can install these dependencies using pip:
```bash
pip install opencv-python mediapipe
```

## How It Works
### Hand Landmark Detection
The project uses MediaPipe’s Hand solution to detect hand landmarks from the video stream. These landmarks are key to recognizing specific gestures.

### Gesture Recognition
Each sign is recognized based on the relative positions of finger tips and the thumb. Here’s a breakdown of how the signs are detected:

- **Stop:** All fingers are extended straight.
- **Forward:** Thumb points right, and all other fingers are extended.
- **Backward:** Thumb points left, with the middle, ring, and pinky fingers extended.
- **Left:** Thumb points down, and fingers point left.
- **Right:** Thumb points down, and fingers point right.

### Code Explanation
1. **Setup MediaPipe and OpenCV:**
   Initialize the MediaPipe Hands model and OpenCV for video capture.
   ```python
   mp_hand = mp.solutions.hands
   hands = mp_hand.Hands(min_detection_confidence=0.5, min_tracking_confidence=0.5)
   draw_utils = mp.solutions.drawing_utils
   ```

2. **Process Video Frames:**
   Capture frames from the webcam and convert them to RGB for MediaPipe processing.
   ```python
   image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
   result = hands.process(image_rgb)
   ```

3. **Landmark Detection:**
   Extract hand landmarks and check their relative positions to identify gestures.
   ```python
   if lm_hands[2].y > lm_hands[4].y and lm_hands[8].y < lm_hands[6].y ...
   ```

4. **Draw Landmarks:**
   The detected landmarks and connections are drawn on the image for visualization.
   ```python
   draw_utils.draw_landmarks(image, hand_landmrak, mp_hand.HAND_CONNECTIONS, ...)
   ```

5. **Display Output:**
   The recognized sign is displayed on the screen, and the video feed is shown in a window.
   ```python
   cv2.imshow("Hand Sign Detection", image)
   ```

## Future Enhancements
- **Expand Sign Vocabulary:** Extend the system to recognize a broader range of signs.
- **Improve Accuracy:** Fine-tune the model to improve detection accuracy.
- **Real-World Applications:** Integrate with other systems such as robotic controls or accessibility tools.

## Conclusion
This project highlights the potential of computer vision in enhancing communication, especially for individuals with hearing or speech impairments. It’s a starting point for developing more comprehensive sign language recognition systems that can be used in various practical applications.
