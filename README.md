# WV-Team
사진 기반 위스키 검색/분류 실험 (Colab + Google Drive 데이터)

## 환경:
python 3.11(만약 macos에서 특별히 requirements_macos.txt를 이용하여 설치할 거라면)
tensorflow 2.16.2
jupyter 1.1.1

```python
python3 -m venv .venv
source .venv/bin/activate   # (윈도우는 .\.venv\Scripts\activate)
pip install -r requirements.txt
```

## 로컬 주피터 실행
로컬에서 
```bash
git clone
```
으로 클론하여 실행하는 경우, WV-Team/data 디렉토리가 기본 DATA_DIR가 됩니다.
여기에 prepacked.zip을 압축해제하면 됩니다.(photos 서브 디렉토리를 넣는 것이 중요합니다.)
```
.
├── LICENSE
├── README.md
├── data #로컬에서 실행시 DATA_DIR
│   ├── kfold_result.csv
│   ├── kfold_result_class.csv
│   ├── kfold_result_input.csv
│   ├── metadata.csv
│   ├── model_v2.keras
│   ├── model_v_final.keras
│   ├── model_v_final_checkpoint.keras
│   ├── photos # 여기안에 사진 데이터가 들어갑니다.
│   ├── whiskies.csv
│   ├── whiskies_filtered.csv
│   ├── whiskies_recategorized.csv
│   ├── whiskies_relabel.csv
│   └── whisky_full.csv
├── notebooks
│   ├── 00_colab_bootstrap.ipynb
│   ├── 01_data_bootstrap.ipynb
│   ├── 02_data_analysis.ipynb
│   ├── 03-1_model_analysis.ipynb
│   ├── 03_model_build.ipynb
│   ├── 04_pretrained_comparison.ipynb
│   ├── 05-1_new_model_analysis.ipynb
│   ├── 05-2_data_argumentation.ipynb
│   ├── 05-3_input_layer_test.ipynb
│   ├── 05_class_balance.ipynb
│   └── 06_final_model.ipynb
├── requirements.txt
└── requirements_macos.txt
```

가상 환경을 세팅하셨다면,
```bash
jupyter lab
```

## 빠른 시작(Colab)
1) 이 리포지토리를 Colab에서 열기(보통은 각 ipynb의 최상단에 버튼이 있습니다.)
2) 자신의 구글 드라이브 안에 colab_drive 라는 이름의 디렉토리 생성
3) prepacked.zip을 업로드
* colab에서는 자신 드라이브의 colab_drive/prepacked.zip의 내용을 copy해서 사용하는 방식입니다.

```python
import os
import shutil
from pathlib import Path

try:
    import google.colab
    IN_COLAB = True
except ImportError:
    IN_COLAB = False

if IN_COLAB:
    from google.colab import drive
    drive.mount('/content/drive')
    DATA_DIR = Path('/content/unpacked/')
    PACK_DIR = Path('/content/drive/My Drive/colab_drive/prepacked.zip')
    shutil.copy(PACK_DIR, '/content/')
    !unzip -o -q /content/prepacked.zip -d {DATA_DIR}
else:
    DATA_DIR= Path(os.path.join(os.getcwd(), "../data/")).resolve()
DATA_DIR
```

## prepacked.zip
* 본 WV-Team의 모든 기여자는, 해당 zip파일안의 산물중, "photos" 디렉토리 안의 내용물에 대해서 그 어떠한 권리도 주장하지 않을 것이며, 또한 저작자가 아님을 밝힙니다.
[prepacked.zip](https://drive.google.com/file/d/1V_YlfIoNxEMF1rx5RZZ_tSKtri4n5UzS/view?usp=sharing)

### Final result
Confusion Matrix\
<img width="753" height="679" alt="Image" src="https://github.com/user-attachments/assets/4f434e86-8e07-443d-9ab5-c16f1cb90b59" />