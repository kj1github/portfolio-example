# Gebruik de gespecificeerde kleine image met torch en uv
FROM raoulgrouls/torch-python-slim:py3.12-torch2.8.0-amd64-uv0.9.8

WORKDIR /app

# Kopieer de wheel file uit de dist folder naar de container
# We gebruiken een wildcard zodat het versienummer niet uitmaakt
COPY dist/*.whl /tmp/

# Installeer de wheel met uv voor maximale snelheid
RUN uv pip install --system fastapi uvicorn beautifulsoup4

#RUN uv pip install /tmp/*.whl


RUN uv pip install --system /tmp/*.whl

# Kopieer de backend code en het getrainde model
# Let op: zorg dat de paden overeenkomen met wat backend/app.py verwacht
COPY backend/ .
COPY artefacts/ ./artefacts/

# Expose poort 80 voor directe toegang via SURF
EXPOSE 80

# Start de backend applicatie
# We gaan ervan uit dat app.py een server start op poort 80
CMD ["python", "app.py"]