# Shape Detector

This project is a web-based application that detects and classifies geometric shapes in images. It uses TypeScript and OpenCV.js to identify circles, triangles, rectangles, pentagons, and stars.

## About the Project

The Shape Detector is a tool that allows users to upload an image and see the geometric shapes within it identified and classified. The application provides information about each detected shape, including its type, confidence level, bounding box, center point, and area.

This project was initially designed as a technical interview challenge to assess a candidate's ability to implement shape detection algorithms. However, it has since evolved into a more general-purpose shape detection tool.

### Technologies Used

-   **TypeScript:** For type-safe JavaScript development.
-   **Vite:** As the build tool and development server.

## Features

-   **Shape Detection:** Detects circles, triangles, rectangles, pentagons, and stars in images.
-   **Image Upload:** Users can upload their own images for shape detection.
-   **Test Images:** A set of test images is provided to demonstrate the application's capabilities.
-   **Evaluation:** The application can evaluate the performance of the shape detection algorithm against a ground truth dataset.
-   **Detailed Results:** Provides detailed information about each detected shape.

## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

-   Node.js (version 16 or higher)
-   npm or yarn package manager

### Installation

1.  Clone the repo:
    ```sh
    git clone https://github.com/your_username_/shape-detector.git
    ```
2.  Install NPM packages:
    ```sh
    npm install
    ```
3.  Start the development server:
    ```sh
    npm run dev
    ```

## How it Works

The shape detection process is handled by the `ShapeDetector` class in `src/main.ts`. The algorithm uses OpenCV.js to perform the following steps:

1.  **Image Loading:** The application loads an image from a file or a data URL into an HTML canvas.
2.  **Grayscale Conversion:** The image is converted to grayscale to simplify the subsequent processing steps.
3.  **Noise Reduction:** A bilateral filter is applied to the grayscale image to reduce noise while preserving edges.
4.  **Edge Detection:** The Canny edge detector is used to find the edges in the image.
5.  **Contour Detection:** The application finds the contours of the shapes in the edged image.
6.  **Shape Classification:** Each contour is analyzed to determine its shape:
    -   The number of vertices in the contour's polygonal approximation is used to identify triangles, rectangles, and pentagons.
    -   Circles are identified by analyzing the ratio of the contour's area to the area of its minimum enclosing circle.
    -   Stars are identified based on the number of vertices, the convexity of the contour, and the angles between the vertices.
7.  **Result Display:** The detected shapes, along with their properties, are displayed to the user.

## Evaluation

The application includes an evaluation feature that measures the accuracy of the shape detection algorithm. The `EvaluationManager` class in `src/evaluation-manager.ts` compares the detected shapes with a ground truth dataset defined in `ground_truth.json`.

To run the evaluation, select the test images you want to evaluate and click the "Run Selected Evaluation" button. The evaluation results will be displayed, showing the precision, recall, and F1-score for each shape type.

