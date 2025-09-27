# GPU対応TensorFlowの公式イメージを使用
FROM tensorflow/tensorflow:2.17.0-gpu 

WORKDIR /workspace

RUN python -m venv /opt/venv --system-site-packages \
 && /opt/venv/bin/pip install --upgrade pip setuptools wheel
ENV PATH="/opt/venv/bin:${PATH}"

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
CMD ["python", "-m", "flask", "run", "--host", "0.0.0.0", "--port", "5000"]