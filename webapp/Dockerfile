# Stage 1: build dependencies
FROM python:3.11 AS builder

WORKDIR /install

COPY requirements.txt .
RUN pip install --no-cache-dir --prefix=/install/packages -r requirements.txt


# Stage 2: runtime (lekki obraz)
FROM python:3.11-slim AS runtime

WORKDIR /app

# kopiujemy tylko gotowe paczki z buildera
COPY --from=builder /install/packages /usr/local

# kopiujemy aplikację
COPY app.py .

EXPOSE 5000

CMD ["python", "app.py"]
