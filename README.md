# WV-Team
사진 기반 위스키 검색/분류 실험 (Colab + Google Drive 데이터)

## 환경:
python 3.11, 중요합니다!! 3.13같이 최신버전은 pip install 안될 수도 있어요!!!
```python
python3 -m venv .venv
source .venv/bin/activate   # (윈도우는 .\.venv\Scripts\activate)
pip install -r requirements.txt
```

## 로컬 주피터 실행
```
# 가상 환경 진입 후
jupyter lab
```

## 빠른 시작(Colab)
1) 이 리포지토리를 Colab에서 열기
2) `notebooks/00_colab_bootstrap.ipynb` 실행
3) Google Drive에 `MyDrive/WV-Team/data/`에 CSV/이미지 배치