# Variabelen
IMAGE_NAME := slanggen-backend
PORT := 80
WHEEL_FILE := $(shell ls dist/*.whl 2>/dev/null)
#MODEL_FILE := artefacts/model.pt # Pas aan naar de echte modelnaam
MODEL_FILE := artefacts/slanggen_model.pt

.PHONY: all build_all train build_wheel docker_build run clean

# Default actie: alles bouwen en runnen
all: build_all docker_build run

# Check of alles aanwezig is
build_all: build_wheel train

# Bouw de wheel als deze niet bestaat
build_wheel:
	@if [ -z "$(WHEEL_FILE)" ]; then \
		echo "Wheel niet gevonden. Bouwen met uv..."; \
		uv build --clean; \
	else \
		echo "Wheel is al aanwezig."; \
	fi

# Train het model als het artefact niet bestaat
train:
	@if [ ! -f "$(MODEL_FILE)" ]; then \
		echo "Model niet gevonden. Training starten..."; \
		python src/slanggen/main.py; \
	else \
		echo "Getraind model is al aanwezig."; \
	fi

# Bouw de Docker image
docker_build: build_wheel train
	@echo "Bouwen van Docker image..."
	docker build -t $(IMAGE_NAME) .

# Run de container op poort 80
run:
	@echo "Container starten op poort $(PORT)..."
	docker run -d -p $(PORT):80 --name $(IMAGE_NAME) $(IMAGE_NAME)
	@echo "Applicatie bereikbaar op http://localhost:$(PORT)"

clean:
	docker stop $(IMAGE_NAME) || true
	docker rm $(IMAGE_NAME) || true
	rm -rf dist/ build/