# Face Recognition Attendance System

## Overview

This project implements an automated attendance system using face recognition technology. It utilizes Python, OpenCV, dlib's ResNet face recognition model, and MongoDB to create a robust solution for tracking attendance in real-time.

## Features

-  Advanced Face Recognition: Uses dlib's state-of-the-art ResNet model for accurate face detection and recognition.
-  Real-time Processing: Captures and processes video streams in real-time for immediate attendance marking.
-  Database Integration: Leverages MongoDB for efficient storage and retrieval of attendance records.
-  Daily Attendance Tracking: Automatically creates a new collection for each day's attendance, preventing duplicate entries.
-  User-friendly Image Capture: Includes a separate script for easy capture of student images for the dataset.
-  Automatic Model Download: Implements automatic downloading and decompression of required dlib models.

## Prerequisites

- Python 3.7+
- OpenCV
- dlib
- NumPy
- scikit-image
- MongoDB
- pymongo

## Installation

- Clone this repository:
git clone https://github.com/kumarchy/Face-recognition-using-dlib.git

  cd face-recognition-attendance

- Install required packages:
  
  pip install opencv-python dlib numpy scikit-image pymongo

- Ensure MongoDB is installed and running on your system.

## Usage

- Capturing Student Images
  
  Run the image capture script to build your dataset:

  python datagen.py

  Follow the prompts to enter the student's name and roll number. Press SPACE to capture images and ESC to finish.

- Generating Face Encodings
  
  Process the captured images to create face encodings:

  python trainer.py

This script will:

i. Download necessary dlib models if not present

ii. Process all images in the Dataset directory

iii. Generate and save face encodings to

face_encodings.pkl

- Running the Attendance System
  
  Start the main attendance system:

  python inference.py

The system will:
- Check if attendance has already been taken for the day
- Start the webcam for face recognition
- Mark attendance in real-time
- Save attendance records to the MongoDB database

Press 'q' to quit and save the attendance.

## Code Structure

- datagen.py: Script for capturing student images.
- trainer.py: Processes images and generates face encodings.
- inference.py: Main script for running the attendance system.

## Key Functions

- capture_images(): Captures and saves images for the dataset.
- download_model(): Downloads and decompresses dlib models.
- process_images(): Generates face encodings from images.
- find_match(): Finds the best match for a face encoding.
- mark_attendance(): Records attendance in the MongoDB database.
- run_attendance_system(): Main function to run the attendance system.

## Database Structure

- Database Name: Attendances
- Collections: Dynamic daily collections (e.g., attendance_2023-05-01)
- Document Structure:
  
  {
  
    "student_name": "John Doe",
    "roll_no": "R001",
    "status": "P",
    "timestamp": ISODate("2023-05-01T09:00:00Z")

  }

## Future Enhancements

- Web interface for attendance management
- Integration with existing school
- Liveness detection for improved security
- Fine-tuning of the ResNet model for specific environments

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to check issues page if you want to contribute.

## Acknowledgments

- dlib developers for their excellent face recognition model
- OpenCV community for computer vision tools
- MongoDB team for the robust database solution
