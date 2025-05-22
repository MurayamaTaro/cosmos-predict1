# .devcontainer/Dockerfile
FROM nvcr.io/nvidia/pytorch:24.10-py3

# 1) 基本ツールを追加
RUN apt-get update && apt-get install -y \
    git tree ffmpeg wget \
 && rm -rf /var/lib/apt/lists/*

# 2) リポジトリ内ファイルをコピー
COPY requirements.txt /workspace/requirements.txt
COPY . /workspace

WORKDIR /workspace

# 3) pip で依存インストール＋Transformer-Engine＋Apex
RUN pip install --upgrade pip \
 && pip install --no-cache-dir -r requirements.txt \
 && pip install transformer-engine[pytorch]==1.12.0 \
 && git clone https://github.com/NVIDIA/apex \
 && cd apex \
 && pip install -v --disable-pip-version-check --no-cache-dir \
      --no-build-isolation \
      --global-option="--cpp_ext" \
      --global-option="--cuda_ext" . \
 && cd .. && rm -rf apex

# 4) デフォルトシェル
CMD ["/bin/bash"]
