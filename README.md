# 機械学習プロジェクト用 テンプレート構成

このリポジトリは，機械学習プロジェクトの構成テンプレートです．

## ディレクトリ構成

```
my-ml-project/
├── README.md # プロジェクトの概要・使い方（このファイル）
├── requirements.txt # 必要なPythonライブラリ（pip用）
├── environment.yml # Conda環境用（任意）
├── .gitignore # Gitで無視するファイル一覧
│
├── config/
│ └── config.yaml
│
├── data/
│ ├── raw/
│ └── processed/
│
├── dataset/
│ ├── data_utils.py
│ └── preprocess.py
│
├── models/
│ └── my_model.py
│
├── losses
│ └── my_loss.py
│
├── trainers/
│ └── trainer.py
│
├── utils/
│ ├── logger.py
│ ├── metrics.py
│ └── visualization.py 
│
├── scripts/
│ ├── train.py
│ ├── eval.py
│ └── predict.py
│
├── experiments/
│ ├── logs/
│ ├── checkpoints/
│ └── results/
│
├── notebooks/
├── logs/
├── checkpoints/
└── results/
```

## 各ディレクトリの説明

- `config/`：モデルや訓練パラメータの設定ファイル（YAML/JSONなど）
- `data/`：ローディング対象の生データや加工済データを格納
- `dataset/`：PyTorchなどの `Dataset` 定義やデータ前処理
- `models/`：ニューラルネットワークモデルの定義
- `losses/`：損失関数のカスタム実装
- `trainers/`：学習ループやオプティマイザ処理
- `utils/`：ログ記録，可視化，評価関数などの補助処理
- `scripts/`：CLIから使うスクリプト（例：`train.py`で学習）
- `experiments/`：実験ごとのログ・結果・重みなどを保存
- `notebooks/` : Jupyterで試したコードなどを保存

## 使用方法

```bash
# 環境構築（例: conda）
conda env create -f environment.yml
conda activate my-ml-project
```

# 学習実行
```bash
python scripts/train.py --config config/config.yaml
```
# 注意点
data/ 以下は .gitignore でGitに含まれません．必要に応じて .gitkeep を使ってフォルダ構造のみ維持してください．

実験の再現性を保つために，config.yaml を整理して管理してください．

# .gitignore の例
```
# Pythonキャッシュ・中間ファイル
__pycache__/
*.py[cod]
*.so
*.pyd

# Jupyter Notebookのチェックポイント
.ipynb_checkpoints/

# 環境ファイル・依存管理
.env
.venv/
venv/
env/
Pipfile.lock
poetry.lock

# Condaの環境（保存しない場合）
*.conda
*.env
*.yml

# データ関連
data/
datasets/
*.csv
*.tsv
*.zip
*.tar.gz
*.npz
*.npy
*.pt
*.pth
*.ckpt
*.h5
*.wav
*.mp3

# モデルの出力・チェックポイント
checkpoints/
experiments/
logs/
runs/         # TensorBoard

# キャッシュ・ビルド
*.log
*.bak
*.tmp
*.swp
.cache/
build/
dist/

# VSCode固有
.vscode/
*.code-workspace

# Mac固有
.DS_Store

# Jupyter Notebookの出力画像など
*.png
*.jpg
*.jpeg
*.gif

# テスト出力・一時ファイル
*.out
*.err
*.tmp
```
