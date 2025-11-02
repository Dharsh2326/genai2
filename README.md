# AI-Based Image to Sketch Converter

## 📘 Overview

This project uses Generative AI with Stable Diffusion and ControlNet (Canny Edge) to transform a normal image into a realistic pencil sketch.  
It combines the power of diffusion models and edge detection to generate detailed black-and-white sketches from input images.

The project runs directly in Google Colab, so no complex setup is required.

## 🚀 Features

- Converts any uploaded image into a hand-drawn style sketch.
- Uses ControlNet (Canny) to detect edges and guide the generation.
- Leverages Stable Diffusion (v1.5) for high-quality, AI-generated results.
- Simple and clean side-by-side comparison of original and generated sketch.
- Automatically downloads the output image.

## 🧠 Technologies Used

| Component               | Purpose                       |
|-------------------------|-------------------------------|
| Python                  | Programming language          |
| Hugging Face Diffusers  | Generative AI model pipeline  |
| ControlNet (Canny)      | Edge detection guidance       |
| PyTorch                 | Model inference and computation |
| Pillow (PIL)            | Image handling                |
| Matplotlib              | Image visualization           |
| Google Colab            | Easy cloud-based execution    |

## ⚙️ Setup Instructions

1. Open [Google Colab](https://colab.research.google.com/).
2. Copy and paste the entire project code into a new notebook.
3. Run each cell step-by-step.
4. When prompted, upload an image from your device.
5. The model will generate and display the sketch.
6. A file named `sketch.png` will automatically download after generation.

## 🧩 Code Explanation

### 1. Install and Import Dependencies

```python
!pip install -q diffusers transformers accelerate torch pillow controlnet_aux
```
Installs all required AI and image processing libraries.

### 2. Load ControlNet and Stable Diffusion

```python
controlnet = ControlNetModel.from_pretrained("lllyasviel/control_v11p_sd15_canny")
pipe = StableDiffusionControlNetPipeline.from_pretrained("runwayml/stable-diffusion-v1-5")
```
Loads the pre-trained generative AI models from Hugging Face.

### 3. Edge Detection with Canny

```python
edge_image = canny(image)
```
Detects edges in the uploaded image — acts as the input guide for the sketch.

### 4. Sketch Generation

```python
sketch = pipe(prompt="pencil sketch, detailed drawing, black and white", image=edge_image)
```
The Stable Diffusion model generates a black-and-white sketch guided by the edges.

### 5. Visualization and Download

The output is displayed beside the original and saved as `sketch.png`.

## 💡 Future Enhancements

- Add a web interface using Flask or Gradio.
- Allow users to adjust sketch intensity or style.
- Extend model support to color sketches or artistic filters.
- Add batch processing for multiple images.
- Integrate with Hugging Face Spaces for permanent hosting.
