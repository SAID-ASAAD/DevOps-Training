FROM python:3.11-slim-bullseye

# Define o diretório de trabalho no contêiner
WORKDIR /app

# Copia o arquivo de dependências primeiro para aproveitar o cache do Docker
COPY requirements.txt .

# Instala as dependências
# --no-cache-dir reduz o tamanho da imagem
# --upgrade pip garante que estamos usando a versão mais recente do pip
RUN pip install --no-cache-dir --upgrade pip && pip install --no-cache-dir -r requirements.txt

# Copia o restante do código da aplicação para o diretório de trabalho
COPY . .

# Expõe a porta que a aplicação irá rodar
EXPOSE 8000

# Comando para iniciar a aplicação com Uvicorn
# Usamos 0.0.0.0 para que a aplicação seja acessível de fora do contêiner
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
