# Attendance System Using Artificial Intelligence

## Project Overview
This project implements an artificial intelligence-based attendance system using face recognition technology. It is designed to automate the process of attendance tracking in various settings, such as educational institutions, workplaces, or events. The system identifies individuals from images and records their attendance automatically, streamlining the traditional manual attendance recording process.

## Key Features
- **Face Recognition:** Utilizes advanced algorithms to accurately identify individuals from images.
- **Automatic Attendance Tracking:** Automates the process of marking attendance, saving time and reducing errors.
- **Customizable Output:** Provides options for customizing the output, such as bounding box color and text color.

## Directory Structure
- `training/` - Contains images or data used for training the face recognition model.
- `validation/` - Contains images or data used for validating the model's accuracy.
- `output/` - Stores output files, including face encodings and attendance records.
- `*.jpeg` - Sample images used for testing or demonstration purposes.

## Setup and Installation
1. **Clone the Repository:**
```shell
git clone [repository-url]
```
2. **Install Required Libraries:**
Ensure you have Python installed, and then run:
```shell
pip install face_recognition Pillow
```
3. **Prepare the Data:**
Place your training and validation images in the respective directories.

## Usage
To run the attendance system, execute the `detector.py` script:
```shell
python detector.py
```
The script will process the images in the specified directories, identify individuals, and record their attendance in the output directory.

# Code Explanation for `detector.py`

The `detector.py` script is a key component of the Attendance System Using Artificial Intelligence. This explanation breaks down the script into its core functionalities and describes what each part does.

## Import Statements
```python
from pathlib import Path
import face_recognition
import pickle
from collections import Counter
from PIL import Image, ImageDraw
```
**pathlib.Path:** Used for file and directory path operations.
**face_recognition:** Core library for facial recognition tasks.
**pickle:** For serializing and deserializing Python object structures (saving and loading data).
**collections.Counter:** Helps in counting objects (useful for tracking attendance).
**PIL (Python Imaging Library), Image, ImageDraw:** For image processing and drawing, such as adding bounding boxes around recognized faces.

```python
DEFAULT_ENCODINGS_PATH = Path("output/encodings.pkl")
BOUNDING_BOX_COLOR = "blue"
TEXT_COLOR = "white"
```
**DEFAULT_ENCODINGS_PATH:** Path to save face encodings. Encodings are used to recognize faces efficiently.
**BOUNDING_BOX_COLOR:** Color of the bounding boxes drawn around detected faces.
**TEXT_COLOR:** Color of the text for labeling detected faces.

## Class: `FaceEncoder`

```python
class FaceEncoder:
    def __init__(self, training_path):
        self.training_path = training_path

    def create_encodings(self):
        # Code to process images in the training_path.
        # Generate encodings for each face.
```

**Purpose:** Handles the creation and storage of face encodings based on the training dataset.
**Methods:**
__init__(self, training_path): Initializes the class with the path to the training data.
create_encodings(self): Processes the images in the training path, detects faces, and generates encodings for each detected face. These encodings are saved for future recognition tasks.

## Class: `FaceDetector`

```python
class FaceDetector:
    def __init__(self, encodings_path):
        self.encodings_path = encodings_path

    def detect_faces(self, image_path):
        # Code to load an image from image_path.
        # Detect faces using face_recognition.
```
**Purpose:** Responsible for detecting faces in given images.
**Methods:**
__init__(self, encodings_path): Initializes the class with the path to the saved face encodings.
detect_faces(self, image_path): Loads an image from the specified path and detects faces within it, using pre-generated encodings for recognition.

## Class: `AttendanceRecorder`

```python
class AttendanceRecorder:
    def __init__(self, output_path):
        self.output_path = output_path

    def record_attendance(self, recognized_faces):
        # Code to update attendance records based on recognized faces.
```
**Purpose:** Manages the recording of attendance based on recognized faces.
**Methods:**
__init__(self, output_path): Initializes the class with the path to the directory where attendance records are stored.
record_attendance(self, recognized_faces): Updates the attendance records based on the list of recognized faces. This could involve marking individuals as present in a database or a file.

## Integration and Workflow

The classes **FaceEncoder**, **FaceDetector**, and **AttendanceRecorder** work together within the detector.py script to facilitate the end-to-end process of automatic attendance tracking. Here's a simplified workflow:

**Encoding Creation:** FaceEncoder processes training images to create and store face encodings.
**Face Detection:** FaceDetector uses these encodings to detect and recognize faces in new images.
**Attendance Recording:** AttendanceRecorder takes the list of recognized faces and updates the attendance records accordingly.

## Customization
You can customize the system by modifying the following settings in `detector.py`:
- `DEFAULT_ENCODINGS_PATH` - Path to store face encodings.
- `BOUNDING_BOX_COLOR` - Color of the bounding box around recognized faces.
- `TEXT_COLOR` - Color of the text used to label recognized faces.

## Contributing
Contributions to this project are welcome! Please fork the repository, make your changes, and submit a pull request.

Make sure to replace [repository-url] with the actual URL of your GitHub repository.
