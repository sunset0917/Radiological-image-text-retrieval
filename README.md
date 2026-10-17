# Fine-Tuned BiomedCLIP for Radiology Image–Text Retrieval

Fine-tuned **BiomedCLIP** on the **ROCO (Radiology Objects in Context)** dataset for multimodal image–text retrieval in the radiology domain.

## Overview

This project fine-tunes **BiomedCLIP**, a biomedical vision-language foundation model, using image-caption pairs from the ROCO radiology dataset.

The goal is to improve the semantic alignment between radiological images and their corresponding medical descriptions, enabling:

- **Text-to-image retrieval:** Retrieve relevant radiological images using a natural language query.
- **Image-to-text retrieval:** Retrieve relevant medical descriptions given a radiological image.

The project also includes a Gradio application for interactive exploration of the fine-tuned model.

## Demo

Try the model directly on Hugging Face Spaces:

**[Launch the interactive demo](https://huggingface.co/spaces/lulu12lemon/biomedclip)**

## Base Model

The project uses the following architecture:

- **Model:** BiomedCLIP
- **Image encoder:** ViT-B/16
- **Text encoder:** PubMedBERT
- **Framework:** OpenCLIP

Learn more about the base model:

[Microsoft BiomedCLIP on Hugging Face](https://huggingface.co/microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224)

## Dataset

### ROCO — Radiology Objects in Context

ROCO is a medical computer vision dataset containing radiological images extracted from biomedical publications and their associated captions.

The dataset was obtained from Kaggle:

**[Access the ROCO dataset](https://www.kaggle.com/datasets/virajbagal/roco-dataset)**

Due to licensing and storage considerations, the original images are not included in this repository. The repository includes a cleaned CSV file containing radiology training data:

- `radiologytraindata_clean.csv`

The test dataset used by the demo is also represented in the project structure.

## Project Structure

```text
├── notebooks/
│   └── TA_Final.ipynb
├── scripts/
│   ├── script.py
│   ├── script2.py
│   └── script3.py
├── data/
│   ├── Trainingdataset.py
│   └── radiologytestdata_clean.csv
├── demo/
│   └── app.py
├── requirements.txt
└── README.md
```

### Main Files

| File | Description |
|---|---|
| `TA_Final.ipynb` | Notebook for experimentation and model evaluation. |
| `scripts/` | Scripts used for training and supporting workflows. |
| `Trainingdataset.py` | Dataset preparation and loading utilities. |
| `radiologytestdata_clean.csv` | Cleaned test dataset metadata. |
| `demo/app.py` | Gradio interface for image–text retrieval. |
| `requirements.txt` | Project dependencies. |

## Fine-Tuned Model

The trained model checkpoint is available on Hugging Face Spaces:

**[Download `model.pt`](https://huggingface.co/spaces/lulu12lemon/biomedclip/blob/main/model.pt)**

Download the checkpoint before running the application locally.

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/sunset0917/biomedclip-roco-finetuning.git
cd biomedclip-roco-finetuning
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Linux or macOS:

```bash
source venv/bin/activate
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the model checkpoint

Download [`model.pt` from Hugging Face](https://huggingface.co/spaces/lulu12lemon/biomedclip/blob/main/model.pt) and place it in the location expected by the application.

Check the model path configured in `demo/app.py` before launching the demo.

## Running the Gradio Application

From the repository root, run:

```bash
python demo/app.py
```

The interface supports:

- Entering a text description to retrieve relevant radiological images.
- Using a radiological image to retrieve relevant medical descriptions.
- Exploring retrieval results ranked by similarity.

**Note:** The demo uses images from the ROCO test set for retrieval and visualization.

## Results

The fine-tuned model was evaluated on image–text retrieval tasks and compared against the original BiomedCLIP model.

### Image-to-Text Retrieval

| Metric | Fine-Tuned BiomedCLIP | Original BiomedCLIP |
|---|---:|---:|
| Recall@1 | 33.55% | 33.21% |
| Recall@5 | 66.27% | 66.02% |
| Recall@10 | 79.40% | 79.26% |

### Text-to-Image Retrieval

| Metric | Fine-Tuned BiomedCLIP | Original BiomedCLIP |
|---|---:|---:|
| Recall@1 | 35.60% | 35.49% |
| Recall@5 | 66.96% | 67.09% |
| Recall@10 | 80.31% | 80.14% |

The fine-tuned model achieved higher Recall@1 and Recall@10 in both retrieval directions. Recall@5 also improved for image-to-text retrieval, while the original model performed slightly better on text-to-image Recall@5.

Overall, the results show comparable retrieval performance between the fine-tuned and original models, with modest improvements on most evaluated metrics.

## Demo Interface

![BiomedCLIP Retrieval Demo](image/demo.png)

<!---
# Recuperación Multimodal Imagen - Texto en Imágenes Radiológicas

Modelo BiomedCLIP ajustado (fine-tuning) sobre el conjunto de datos **ROCO (Radiology Objects in Context)** para tareas de recuperación multimodal imagen-texto en el dominio radiológico.

## Descripción

Este proyecto realiza el ajuste fino de **BiomedCLIP**, un modelo fundacional multimodal para imágenes biomédicas y texto científico, utilizando pares imagen-caption del subconjunto de radiología de ROCO.

El modelo resultante mejora la alineación entre imágenes médicas y descripciones clínicas, permitiendo:

- Búsqueda de imágenes a partir de texto.
- Recuperación de descripciones médicas a partir de imágenes.
---

## Demo

Prueba el modelo directamente desde Hugging Face Spaces:

**[Acceder a la demo](https://huggingface.co/spaces/lulu12lemon/biomedclip)**


## Modelo Base
Se utilizó:

- **BiomedCLIP**
- Encoder de imágenes: ViT-B/16
- Encoder de texto: PubMedBERT
- Framework: OpenCLIP

Más información sobre BiomedCLIP:

https://huggingface.co/microsoft/BiomedCLIP-PubMedBERT_256-vit_base_patch16_224

---

## Dataset

### ROCO (Radiology Objects in Context)

ROCO es un conjunto de datos de visión por computadora médica compuesto por imágenes extraídas de publicaciones biomédicas junto con sus respectivas descripciones. Por motivos de licencia y tamaño, las imágenes originales no se incluyen en este repositorio. Se usó la data a partir de Kaggle  **[Acceder al dataset]([https://huggingface.co/spaces/lulu12lemon/biomedclip](https://www.kaggle.com/datasets/virajbagal/roco-dataset))**
Sin embargo, se proporciona el archivo:

```text
radiologytraindata_clean.csv
```
---

## Estructura del Proyecto

```text

├── notebooks/
├───── TA_Final.ipynb
├── scripts/
├───── script.py
├───── script2.py
├───── script3.py
├── data/
├───── Trainingdataset.py
├───── radiologytestdata_clean.csv
├── demo/
├───── app.py
├── requirements.txt
└── README.md
```

Donde:

| Archivo | Descripción |
|----------|------------|
| `script_final.py` | Entrenamiento del modelo con parámetros optimizados |
| `app.py` | Aplicación Gradio |
| `requirements.txt` | Dependencias del proyecto |

Además, el modelo final puede ser encontrado **[aquí]( https://huggingface.co/spaces/lulu12lemon/biomedclip/blob/main/model.pt)**

---

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/sunset0917/biomedclip-roco-finetuning.git
```

### 2. Crear entorno virtual

```bash
python -m venv venv
```

Linux/Mac:

```bash
source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

---

## Aplicación Gradio

Primero descargar el modelo **[aquí]( https://huggingface.co/spaces/lulu12lemon/biomedclip/blob/main/model.pt)**
Nota: Para la demo, como parte de las imágenes para recuperar y mostrar se usó el test set del dataset ROCO. 
Ejecutar localmente:

```bash
python app.py
```

La interfaz permite:

- Describir una imagen radiológica.
- Buscar imágenes radiológicas a partir de texto.
- Visualizar resultados ordenados por relevancia.


---

## Resultados

Se muestran los resultados obtenidos para el modelo propio.

| Tarea | Métrica | Modelo Propio | BioMedCLIP |
|----------|---------|---------|---------|
| Recuperación Imagen a Texto | Recall@1 | 33.55% | 33.21% |
| Recuperación Imagen a Texto| Recall@5 | 66.27% | 66.02% |
| Recuperación Imagen a Texto | Recall@10 | 79.40% | 79.26% |
| Recuperación Texto a Imagen | Recall@1 | 35.60% | 35.49% |
| Recuperación Texto a Imagen | Recall@5 | 66.96% | 67.09%
| Recuperación Texto a Imagen | Recall@10 | 80.31% | 80.14%


---


### Interfaz de la Demo

![Demo](image/demo.png)

---

## Limitaciones

Este proyecto tiene fines exclusivamente académicos y de investigación. Además, se ha enfocado en el desarrollo de tarea de recuperación de texto e imágenes del modelo de BiomedCLIP, no se han implementado las tareas de clasificación de imágenes o respuesta de preguntas. 

-->
