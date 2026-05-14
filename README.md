# 🚀 Data Pipelines → Hugging Face

Colección de pipelines en Python para cargar datasets desde múltiples fuentes hacia Hugging Face Hub. Cubre datos tabulares, NLP, visión por computadora, salud, series temporales y más.

---

## 📁 Estructura del Repositorio

```
.
├── pipelines/
│   ├── kaggle/
│   │   └── kaggle_to_hf.py
│   ├── huggingface/
│   │   └── hf_to_hf.py
│   ├── uci/
│   │   └── uci_to_hf.py
│   ├── google_dataset_search/
│   │   └── gds_to_hf.py
│   ├── llm_reasoning/
│   │   └── reasoning_datasets_to_hf.py
│   ├── papers_with_code/
│   │   └── pwc_to_hf.py
│   ├── imagenet/
│   │   └── imagenet_to_hf.py
│   ├── coco/
│   │   └── coco_to_hf.py
│   ├── physionet/
│   │   └── physionet_to_hf.py
│   ├── mimic/
│   │   └── mimic_to_hf.py
│   ├── ham10000/
│   │   └── ham10000_to_hf.py
│   ├── yahoo_finance/
│   │   └── yfinance_to_hf.py
│   └── fred/
│       └── fred_to_hf.py
├── utils/
│   ├── hf_uploader.py        # Utilidad común de subida a HF
│   ├── data_validator.py     # Validación de esquemas
│   └── logger.py             # Logging centralizado
├── configs/
│   └── sources.yaml          # Configuración de fuentes y destinos
├── requirements.txt
└── README.md
```

---

## ⚙️ Instalación

```bash
git clone https://github.com/tu-usuario/tu-repo.git
cd tu-repo
pip install -r requirements.txt
```

### Autenticación

```bash
# Hugging Face
huggingface-cli login

# Kaggle (requiere kaggle.json en ~/.kaggle/)
export KAGGLE_USERNAME=tu_usuario
export KAGGLE_KEY=tu_api_key

# FRED API
export FRED_API_KEY=tu_api_key
```

---

## 🗂️ Fuentes Soportadas

### 1. 🏆 Kaggle
**Ideal para:** datos tabulares, competiciones, proyectos reales, datasets limpios y sucios.

**Casos de uso:** predicción, clasificación, salud, finanzas, NLP básico.

🔗 [Kaggle Datasets](https://www.kaggle.com/datasets)

```bash
python pipelines/kaggle/kaggle_to_hf.py \
  --dataset "owner/dataset-name" \
  --hf-repo "tu-usuario/nombre-dataset"
```

---

### 2. 🤗 Hugging Face Datasets
**Ideal para:** LLMs, NLP, fine-tuning, reasoning datasets, chat datasets, multimodal.

**Casos de uso:** Unsloth, Qwen/Llama fine-tuning, datasets conversacionales y sintéticos.

🔗 [Hugging Face Datasets](https://huggingface.co/datasets)

```bash
python pipelines/huggingface/hf_to_hf.py \
  --source-dataset "org/dataset-name" \
  --hf-repo "tu-usuario/nombre-dataset" \
  --split "train"
```

---

### 3. 🎓 UCI Machine Learning Repository
**Ideal para:** clasificación, regresión, árboles de decisión, Random Forest, SVM.

**Datasets famosos:** Iris, Wine, Adult Income, Breast Cancer.

🔗 [UCI ML Repository](https://archive.ics.uci.edu/ml/index.php)

```bash
python pipelines/uci/uci_to_hf.py \
  --dataset-id 53 \
  --dataset-name "iris" \
  --hf-repo "tu-usuario/iris-uci"
```

---

### 4. 🔍 Google Dataset Search
**Ideal para:** datasets científicos, salud, economía, clima y datasets difíciles de encontrar.

🔗 [Google Dataset Search](https://datasetsearch.research.google.com)

```bash
python pipelines/google_dataset_search/gds_to_hf.py \
  --url "https://url-directa-del-dataset.csv" \
  --hf-repo "tu-usuario/nombre-dataset"
```

---

### 5. 🧠 LLMs & Reasoning Datasets (HF Hub)
**Ideal para:** fine-tuning de LLMs, razonamiento, datasets conversacionales.

**Datasets soportados:** OpenThoughts, UltraChat, ShareGPT, OpenHermes, GSM8K, MATH, DeepSeek-R1, Multilingual-Thinking.

🔗 [Multilingual Thinking Dataset](https://huggingface.co/datasets/HuggingFaceH4/Multilingual-Thinking)

```bash
python pipelines/llm_reasoning/reasoning_datasets_to_hf.py \
  --preset gsm8k \
  --hf-repo "tu-usuario/gsm8k-procesado"
```

**Presets disponibles:** `gsm8k`, `math`, `ultrachat`, `sharegpt`, `openhermes`, `openthoughts`, `multilingual-thinking`

---

### 6. 📄 Papers With Code
**Ideal para:** reproducir papers, benchmarks, datasets SOTA.

🔗 [Papers With Code Datasets](https://paperswithcode.com/datasets)

```bash
python pipelines/papers_with_code/pwc_to_hf.py \
  --dataset "nombre-del-dataset" \
  --hf-repo "tu-usuario/nombre-dataset"
```

---

### 7. 🖼️ ImageNet
**Ideal para:** visión computacional, clasificación de imágenes, benchmarks históricos.

🔗 [ImageNet](https://www.image-net.org)

```bash
python pipelines/imagenet/imagenet_to_hf.py \
  --data-dir /ruta/a/imagenet \
  --hf-repo "tu-usuario/imagenet-subset" \
  --subset "val"
```

> ⚠️ Requiere descarga previa manual de ImageNet con credenciales propias.

---

### 8. 🐄 COCO Dataset
**Ideal para:** detección de objetos, segmentación, visión multimodal.

🔗 [COCO Dataset](https://cocodataset.org)

```bash
python pipelines/coco/coco_to_hf.py \
  --year 2017 \
  --split "train" \
  --hf-repo "tu-usuario/coco-2017"
```

---

### 9. 💓 PhysioNet
**Ideal para:** ECG, ICU, señales biomédicas, predicción clínica.

🔗 [PhysioNet](https://physionet.org)

```bash
python pipelines/physionet/physionet_to_hf.py \
  --record "mitdb/100" \
  --hf-repo "tu-usuario/mitdb-physionet"
```

> ⚠️ Algunos datasets requieren credenciales y acuerdo de uso en PhysioNet.

---

### 10. 🏥 MIMIC-IV
**Ideal para:** clinical reasoning, NLP clínico, predicción hospitalaria.

🔗 [MIMIC-IV](https://physionet.org/content/mimiciv/2.2/)

```bash
python pipelines/mimic/mimic_to_hf.py \
  --mimic-dir /ruta/a/mimic-iv \
  --table "admissions" \
  --hf-repo "tu-usuario/mimic-iv-admissions"
```

> ⚠️ Requiere acceso aprobado a PhysioNet y credenciales MIMIC-IV.

---

### 11. 🔬 HAM10000 (Dermatología)
**Ideal para:** visión médica, clasificación de lesiones cutáneas.

🔗 [HAM10000 en Kaggle](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)

```bash
python pipelines/ham10000/ham10000_to_hf.py \
  --data-dir /ruta/a/ham10000 \
  --hf-repo "tu-usuario/ham10000-dermoscopy"
```

---

### 12. 📈 Yahoo Finance
**Ideal para:** datos financieros históricos, series temporales, forecasting.

🔗 [Yahoo Finance](https://finance.yahoo.com)

```bash
python pipelines/yahoo_finance/yfinance_to_hf.py \
  --tickers "AAPL,MSFT,GOOG" \
  --start "2010-01-01" \
  --end "2024-01-01" \
  --hf-repo "tu-usuario/stock-prices"
```

---

### 13. 🏦 FRED (Federal Reserve)
**Ideal para:** macroeconomía, series temporales, indicadores económicos.

🔗 [FRED Economic Data](https://fred.stlouisfed.org)

```bash
python pipelines/fred/fred_to_hf.py \
  --series "GDP,UNRATE,CPIAUCSL" \
  --start "2000-01-01" \
  --hf-repo "tu-usuario/fred-macro-indicators"
```

---

## 📦 Dependencias

```
# requirements.txt
datasets>=2.18.0
huggingface-hub>=0.22.0
pandas>=2.0.0
numpy>=1.26.0
kaggle>=1.6.0
ucimlrepo>=0.0.3
yfinance>=0.2.38
fredapi>=0.5.1
Pillow>=10.0.0
pycocotools>=2.0.7
wfdb>=4.1.0          # PhysioNet / MIMIC
requests>=2.31.0
tqdm>=4.66.0
pyyaml>=6.0
```

---

## 🔄 Pipeline Genérico

Todos los pipelines siguen la misma interfaz base:

```python
from utils.hf_uploader import upload_to_hf

# 1. Cargar datos desde la fuente
dataset = load_from_source(...)

# 2. Transformar al formato HF Dataset
hf_dataset = transform(dataset)

# 3. Subir a Hugging Face Hub
upload_to_hf(
    dataset=hf_dataset,
    repo_id="tu-usuario/nombre-dataset",
    private=False,
    commit_message="Initial upload via pipeline"
)
```

---

## 🗺️ Mapa de Fuentes

| # | Fuente | Tipo de Dato | Caso de Uso Principal |
|---|--------|-------------|----------------------|
| 1 | Kaggle | Tabular / Imágenes | ML general, competiciones |
| 2 | Hugging Face | Texto / Multimodal | LLMs, NLP, fine-tuning |
| 3 | UCI | Tabular | Clasificación, regresión |
| 4 | Google Dataset Search | Variado | Científico, clima, economía |
| 5 | LLM Reasoning (HF) | Texto | Reasoning, fine-tuning LLMs |
| 6 | Papers With Code | Variado | Benchmarks, SOTA |
| 7 | ImageNet | Imágenes | Visión computacional |
| 8 | COCO | Imágenes | Detección, segmentación |
| 9 | PhysioNet | Series / Señales | ECG, ICU, biomédico |
| 10 | MIMIC-IV | Clínico / Texto | NLP clínico, predicción |
| 11 | HAM10000 | Imágenes médicas | Dermatología, visión médica |
| 12 | Yahoo Finance | Series temporales | Forecasting financiero |
| 13 | FRED | Series temporales | Macroeconomía |

---

## ⚠️ Notas de Acceso

Algunos datasets requieren aprobación previa o credenciales específicas:

- **MIMIC-IV / PhysioNet** → Registro y acuerdo en [physionet.org](https://physionet.org)
- **ImageNet** → Registro en [image-net.org](https://www.image-net.org)
- **Kaggle** → API key en [kaggle.com/settings](https://www.kaggle.com/settings)
- **FRED** → API key gratuita en [fred.stlouisfed.org/docs/api](https://fred.stlouisfed.org/docs/api/api_key.html)

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si quieres agregar una nueva fuente o mejorar un pipeline existente, abre un PR con tu propuesta.

---

## 📄 Licencia

MIT License. Ver [`LICENSE`](./LICENSE) para más detalles.
