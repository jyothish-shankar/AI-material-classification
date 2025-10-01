# AI Material Classification
This repository contains a project for classifying scrap materials (metal, plastic, paper, glass,trash,card board) using deep learning.
It also includes a conveyor belt simulation for real-time image classification and logging.

# Repository Structure
AI-material-classification/
├── src/
│ ├── train_model.py # Training script
│ ├── export_onnx.py # Export trained model to ONNX
│ ├── inference_onnx.py # Single image inference script
│ ├── conveyor_simulation.py # Simulated conveyor belt frame processing
├── dataset-resized/ # Dataset with folders for each class
├── my_results/ # Outputs: ONNX model, class names, logs
├── README.md # Project documentation

# Model Architecture

- Backbone: ResNet18 (Transfer Learning)  
- Input size: 224×224 pixels  
- Data Augmentation: Resize, random horizontal flips, random rotation, normalization  
- Optimizer: Adam  
- Loss: CrossEntropyLoss  
- Training: 5 epochs (can be increased for better accuracy)  
- Export: PyTorch model exported to ONNX for inference  

---

# Features

- ONNX Runtime for fast inference  
- Single image prediction with confidence score  
- Low-confidence flag when prediction < 60%  
- Top-2 predictions recorded for each frame  
- Conveyor simulation:  
  - Processes all images in a folder  
  - Logs predictions and confidence to CSV (`my_results/conveyor_log.csv`)  

# How to Run

# Train the model
```bash
python src/train_model.py
python src/export_onnx.py
python src/inference_onnx.py --image path/to/test.jpg
python src/conveyor_simulation.py --folder frames/ --fps 1
