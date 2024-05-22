# Readme

### Python Version : 3.10.12

Using Python versions other than the specified is likely fail.

Using Library versions other than the specified in the requirements.txt is likely fail.

---

### Install Required Libraries

```
pip install -r requirements.txt
```

### Predict Classes

1. Open and Run cells in the ***model_predictor.ipynb*** File
2. You can explore the ***model_trainer.ipynb*** to retrain the model yourself
    
    **NOTE:** It will be better to use a GPU or TPU or rather train from GOOGLE COLABS and while you do this, ensure you have the correct library version within COLABS.
    

---

---

## Docker

```bash
docker build -t malaria_image .
```

```bash
docker run --rm -d -t --name=my_container --port=8080:8080 malaria_image
```

```bash
docker exec -ti my_container bash
```

```bash
jupyter notebook --ip='0.0.0.0' --port=8080 --no-browser --allow-root
```

---

---

### Model Architecture

```
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓
┃ Layer (type)┃ Output Shape┃       Param #┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩
│ conv2d (Conv2D)                 │ (None, 200, 200, 16)   │           448 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ conv2d_1 (Conv2D)               │ (None, 200, 200, 16)   │         2,320 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ max_pooling2d (MaxPooling2D)    │ (None, 100, 100, 16)   │             0 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential (Sequential)         │ (None, 50, 50, 32)     │         2,160 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential_1 (Sequential)       │ (None, 25, 25, 64)     │         7,392 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential_2 (Sequential)       │ (None, 12, 12, 128)    │        27,072 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dropout (Dropout)               │ (None, 12, 12, 128)    │             0 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential_3 (Sequential)       │ (None, 6, 6, 256)      │       103,296 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dropout_1 (Dropout)             │ (None, 6, 6, 256)      │             0 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ flatten (Flatten)               │ (None, 9216)           │             0 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential_4 (Sequential)       │ (None, 512)            │     4,721,152 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential_5 (Sequential)       │ (None, 128)            │        66,176 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ sequential_6 (Sequential)       │ (None, 64)             │         8,512 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense_3 (Dense)                 │ (None, 1)              │            65 │
└─────────────────────────────────┴────────────────────────┴───────────────┘

```

### Sample Results

![https://github.com/AllanMogley/11-Malaria-Cells-Analysis/blob/master/04%20-%20Image_Results/output.png](https://github.com/AllanMogley/11-Malaria-Cells-Analysis/blob/master/04%20-%20Image_Results/output.png)