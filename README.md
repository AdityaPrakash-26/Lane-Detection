# Lane-Detection

This is a Python command line project made with [Python](https://www.python.org), [OpenCV](https://opencv.org), and [Numpy](https://numpy.org/).

## Getting started

1. Install [python 3](https://www.python.org)
2. Clone the repo
3. Install [dependencies](./requirements.txt)

- `pip3 install -r requirements.txt`

3. Run project

- `python3 main.py`

## How to use

1. The program will automatically detect all lanes/edges in the lower half of the video.
2. You can use your own video by replace the `input.mp4` file.
3. Press `q` to exit the program.

## How it works?

First, a frame is captured from the MP4 video. Then we define a `region_of_interest` with vertices as `(100, height), (width/2, height/2), (width, height)`, which is essentially a triangle starting at the bottom corners, and peaking at the mid point of the image. All further calculations happen in this region.

Next, we plan to use the [Canny Algorithm](https://en.wikipedia.org/wiki/Canny_edge_detector) to detect the edges in the frame, but we first convert the image to grayscale for best results. After this, we crop the image to remove everything but our region of interest triangle, and call the OpenCV's in-built `HoughLinesP` function on it. This coupled with the draw function will create the lines(shown with green) and then superimpose them on our original frame, which is finally returned. This process is repeated for every frame in the video.

## Output

https://user-images.githubusercontent.com/55011564/126891188-5b2cd095-0518-4702-8eb3-561bada60047.mp4

## Resources
- [Hough Transform](https://en.wikipedia.org/wiki/Hough_transform)
- [OpenCV Docs](https://docs.opencv.org/)
- [OpenCV Tutorial](https://docs.opencv.org/master/d9/df8/tutorial_root.html)
- [NumPy](https://numpy.org/doc/stable/user/quickstart.html)
