FROM python:3.9-slim
WORKDIR /app
COPY server.py .
COPY index.html .
RUN pip install flask
EXPOSE 5000
CMD ["python", "server.py"]

