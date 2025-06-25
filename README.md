# YOLOv8 Drawing Classification

A YOLOv8-based image classification model for analyzing children's drawings and predicting emotional states or drawing categories.

## 🎯 Features

- **Image Classification**: Classify drawings into predefined categories using fine-tuned YOLOv8
- **Visual Analysis**: Generate importance heatmaps to understand model decision-making
- **Automated Preprocessing**: Automatic image resizing to 224x224 for optimal model performance
- **Detailed Insights**: Comprehensive prediction analysis with confidence scores and region importance

## 📊 Model Output

The model provides:

1. **Primary Prediction**: Most likely class with confidence score
2. **Top-3 Probabilities**: Ranked list of possible classifications
3. **Visual Analysis**: 
   - Original image display
   - Resized model input (224x224)
   - Importance heatmap showing decision regions
   - Overlay visualization combining image and heatmap

## 🔍 Analysis Features

### Importance Mapping
- Analyzes which regions of the drawing influence the model's decision
- Uses occlusion-based method to determine feature importance
- Generates color-coded heatmaps (yellow = high importance, dark = low importance)

### Prediction Insights
- **High Confidence** (>0.8): Reliable prediction
- **Medium Confidence** (0.6-0.8): Standard prediction
- **Low Confidence** (<0.6): Uncertain prediction, may need review

### Region Analysis
- Identifies key areas: Top/Bottom/Center and Left/Right/Center
- Determines if model focuses on specific regions or considers entire image
- Provides interpretable feedback on model behavior

## 📁 Project Structure
```
├── code/                        # Model training and prediction code
│   ├── img_prediction_Dino.ipynb           # DINO model prediction notebook
│   ├── img_prediction_YOLOv8n-cls.ipynb    # YOLOv8n classification notebook
│   ├── img_prediction_YOLOv8x-cls.ipynb    # YOLOv8x classification notebook
│   ├── img_prediction_resnet18.ipynb       # ResNet18 prediction notebook
│   └── ModelTest(Yolov8x_cls).ipynb        # YOLOv8x classification model test
├── models/                      # Trained model files
│   ├── drawing_finetuned_yolo.pt           # Fine-tuned YOLO model for drawings
│   └── photo_pretrained_yolo.pt            # Pre-trained YOLO model for photos
```

## 🎨 Example Results

```
==================================================
Classification Results
==================================================
Predicted Class: angry
Confidence: 0.6055
Original Image Size: (480, 640)
Model Input Size: 224x224

Top 3 Class Probabilities:
1. angry: 0.6055
2. happy: 0.2341
3. sad: 0.1604

Prediction Insights:
- Model considered the entire image comprehensively.
- Medium confidence prediction.
```

## 🔧 Model Training

The model was fine-tuned using YOLOv8 classification on a custom dataset of children's drawings. 

### Training Details
- **Base Model**: YOLOv8 Classification
- **Input Size**: 224x224 pixels
- **Training Data**: Custom drawing dataset
- **Output**: Fine-tuned model saved as `drawing_finetuned_yolo.pt`

## 🚨 Known Issues

### Importance Mapping Limitations
- Current occlusion-based analysis may not perfectly reflect actual model decision process
- Some models may show unexpected importance patterns (e.g., background over facial features)
- Consider this as supplementary analysis rather than definitive explanation

### Recommendations
- Review model training data for potential biases
- Consider additional validation with diverse test images
- Monitor confidence scores for prediction reliability

## 📈 Performance Notes

- **Processing Time**: ~2-5 seconds per image (including visualization)
- **Memory Usage**: Moderate (depends on image size and batch processing)
- **Accuracy**: Varies by drawing quality and training data similarity

## 🙏 Acknowledgments

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics) for the base model
- OpenCV and Matplotlib for image processing and visualization
- Contributors and testers who helped improve the model
