[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ysaismartinez/AdversarialPatch/blob/main/ysais_adversarial_patch_full.ipynb)

# Adversarial Patch Project

This repository contains my implementation for the **Adversarial Patches** assignment for Duke’s Explainable AI course. The notebook demonstrates how small, intentionally designed visual patches can reduce a model’s confidence or alter its predictions.

---

## How to Run

Everything is designed to run automatically on **Google Colab** or locally with minimal setup.

1. **Open the notebook**  
   - Open the notebook from the Colab URL CLEARLY visible at the top of this README file.  
   - Or open it locally in JupyterLab or VS Code.

2. **Run all cells in order --or if you want to save time, you can see the output already from all cells**  
   The notebook will:
   - Install dependencies (`torch`, `torchvision`, `timm`, `matplotlib`, `opencv-python-headless`)
   - Clone this GitHub repository automatically
   - Load `imagenet_classes.txt`
   - Detect and use images in the `data/` folder
   - Generate and train an adversarial patch
   - Produce visual comparisons between **original** and **patched** images

   No manual configuration is required.

3. **Check the outputs**  
   - Saved results are stored in the `results/` folder (for example, `example_1.png`)
   - You’ll see side-by-side comparisons with model confidence scores before and after patching

---

## Folder Structure

```
AdversarialPatch/
│
├── data/                     # Contains ≥5 test images (jpg/png)
│   ├── banana.jpg
│   ├── bottle.jpeg
│   ├── car.jpeg
│   ├── chair.jpeg
│   ├── bottle.jpeg
│   ├── phone.jpeg
│   ├── dog.jpeg
│   └── backpack.jpg
│
├── imagenet_classes.txt      # ImageNet label names (required)
├── ysais_adversarial_patch_full.ipynb   # Main notebook
├── results/                  # Automatically created for outputs
└── README.md
```

---

## Expected Output

After training, you’ll see:
- Confidence values before and after the patch is applied  
- Example images showing the patch overlayed on everyday objects (e.g., backpack, banana)  
- Printed logs such as:

```
Found 8 images in data/ (for patch optimization)
Epoch 25/30  avg_loss: 10.9372
```

---

## Notes

- If `imagenet_classes.txt` is missing, the notebook will automatically continue and display class indices instead of labels.  
- You can adjust the patch size and learning rate near the top of the notebook.  
- The project is fully reproducible — rerunning all cells from scratch should yield comparable results.  

---

## Reflection Summary

This project explores the vulnerability of CNN-based vision models to localized adversarial noise. The generated patch consistently reduced model confidence across several images, even when the overall classification remained the same. This shows that small, localized perturbations can distract or confuse a model without being visually meaningful to humans.  

The results highlight the importance of explainability and robustness in computer vision systems, especially in high-stakes applications like autonomous vehicles or medical imaging. Overall, this exercise demonstrates both the power and the fragility of deep learning models when exposed to subtle adversarial manipulations.

---

## Optional Local Installation

If you prefer to run this notebook locally instead of Colab:

```
git clone https://github.com/ysaismartinez/AdversarialPatch.git
cd AdversarialPatch
pip install -r requirements.txt
```

Then open `ysais_adversarial_patch_full.ipynb` in Jupyter and run all cells.

---

## requirements.txt

```
torch
torchvision
timm
matplotlib
opencv-python-headless
numpy
pillow
```

