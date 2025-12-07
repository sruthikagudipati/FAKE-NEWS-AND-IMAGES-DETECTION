#  Fake News Image Detection (Binary: Fake vs Real)

This project detects whether a news-related image belongs to a **FAKE** or **REAL** class
using a **CNN model** trained with Keras/TensorFlow and deployed using **Streamlit**.

## Project Structure

```text
fake_news_detection_project/
├── src/
│   └── train.py                # Training script for CNN model
├── streamlit_app/
│   └── app.py                  # Streamlit web app for prediction
├── data/
│   └── fake_and_real/          # Place your dataset here (fake/ and real/ subfolders)
├── models/
│   ├── fake_real_model.h5      # Trained model (generated after training)
│   └── label_map.json          # Class index to label map (generated after training)
├── requirements.txt
├── .gitignore
└── README.md
```

##  Dataset Setup

Expected folder structure for dataset:

```text
data/fake_and_real/
    ├── fake/
    │   ├── img1.jpg
    │   ├── img2.jpg
    │   └── ...
    └── real/
        ├── img1.jpg
        ├── img2.jpg
        └── ...
```

Each image should correspond to either a fraud/fake news example or a real/genuine news example.

> You can adapt this to your own fake/real image dataset.

##  Model

- Model type: Custom CNN (Conv2D + MaxPooling + Dense + Dropout)
- Input size: 224 × 224 × 3
- Output: Single neuron with sigmoid → probability of class 1
- Loss: Binary crossentropy
- Optimizer: Adam
- Metrics: Accuracy

##  Training

Run the following from the project root:

```bash
python src/train.py
```

This will:
- Load images from `data/fake_and_real/`
- Train a CNN for Fake vs Real classification
- Save:
  - `models/fake_real_model.h5`
  - `models/label_map.json`

##  Running the Streamlit App

After training and generating the model files, run:

```bash
cd streamlit_app
streamlit run app.py
```

Then open the provided URL in your browser, upload an image, and the app will classify it as **FAKE** or **REAL** with confidence.

##  Notes

- This repo is structured for academic/demo use.
- You can modify `train.py` to add callbacks, data augmentation, or transfer learning.
- Be sure to place your dataset correctly before training.
