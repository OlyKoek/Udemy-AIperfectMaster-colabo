# GPU対応TensorFlowの公式イメージを使用
FROM tensorflow/tensorflow:latest-gpu

WORKDIR /workspace

RUN apt-get update && apt-get install -y \
    curl \
    && rm -rf /var/lib/apt/lists/*

RUN curl -LsSf https://astral.sh/uv/install.sh | sh
ENV PATH="/root/.local/bin:${PATH}"

COPY pyproject.toml uv.lock* ./
RUN uv sync --frozen

COPY . .

EXPOSE 5000

CMD ["uv", "run", "python", "classifier.py"]