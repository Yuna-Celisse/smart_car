# Handwritten Digit Recognition GUI

A Python Tkinter-based graphical user interface (GUI) for **real-time handwritten digit recognition**. This application lets users draw digits on a canvas, preprocess them into MNIST-style images, and classify them via UART using a Texas Instruments device.

---

## ✨ Features

- **Interactive Drawing Canvas:** Draw digits directly in the app. 
- **Automatic Preprocessing:** Converts drawings into 28×28 normalized grayscale images (MNIST-style). 
- **UART Communication:** Send preprocessed image data to a connected device (TI MCU/NPU) for classification. 
- **Two Classification Modes:**
- **CPU (host)** — classification performed on the MSPM0G5187 CPU.
- **NPU (device)** — classification performed on MSPM0G5187 TI NPU hardware.
- **Live Visualization:**
- Displays the downscaled (28×28) image.
- Shows predicted digit in real time.
- Plots classification probabilities as a histogram.
- Logs inference time and CPU/NPU timing.

---

## 🖥️ GUI Overview

| Section | Description |
|-----------------|-----------------------------------------------------------------------|
| **Header Labels** | Application title and "Texas Instruments" banner. |
| **Left Panel** | Drawing canvas for handwritten digits. |
| **Right Panel** | Downscaled image preview, UART config inputs, and action buttons. |
| **Bottom Section** | Predicted digit display, inference logs, and probability chart. |

------------------------------------------------------------------------

## ⚙️ How It Works

1.  **Draw a Digit:** Use the mouse to draw a digit (0--9) on the black
    canvas.
2.  **Preprocessing:**
    -   Captures the canvas
    -   Finds the bounding box of the digit
    -   Resizes to 28×28 grayscale and inverts colors to match MNIST
        format
3.  **Classification:**
    -   Flattens the preprocessed tensor
    -   Sends it over UART to a TI device 
    -   Receives probabilities for each digit
4.  **Visualization:**
    -   Displays predicted digit
    -   Plots probability histogram
    -   Shows inference time logs

------------------------------------------------------------------------

## 🔌 UART Settings

You can configure the UART COM port and baud rate directly from the GUI:

  --------------- -----------------------------------------------------
  **COM Port**    E.g. `COM11` on Windows or `/dev/ttyUSB0` on Linux.
  **Baud Rate**   Default: `115200` (editable).

> **Note:** Ensure your TI device firmware expects 32-bit floats
> (little-endian) for image data and returns probabilities in the same
> format.

------------------------------------------------------------------------

## 🚀 Running the Application

1.  Clone this repository

2.  Run the .exe file GUI:

3.  Select your COM port, baud rate, and classification mode (CPU or
    NPU).
4.  Draw a digit and click **Classify**.
5.  See the predicted digit, probabilities, and timing metrics in real
    time.

------------------------------------------------------------------------


## ⚠️ Important Notes

-   The NPU/CPU device must be running compatible firmware to receive
    image data and return classification probabilities.
-   The softmax normalization is done on the host after receiving raw
    scores.

------------------------------------------------------------------------

## 📜 License

This project is licensed under the TI License
