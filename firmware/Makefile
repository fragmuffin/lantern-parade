DOCKER_COMPOSE	= docker-compose
SERVICE			= microbit_upy

OUT				= MICROBIT.hex

CURRENT_UID 	:= $(shell id -u)

.PHONY: default mpy-cross build-$(OUT) clean

default: $(OUT)

mpy-cross:
	$(DOCKER_COMPOSE) run --rm -u $(CURRENT_UID) $(SERVICE) \
    	make -C lib/micropython/mpy-cross

build-$(OUT): mpy-cross
	$(DOCKER_COMPOSE) run --rm -u $(CURRENT_UID) $(SERVICE) \
	 	make -C src
	
$(OUT): build-$(OUT)
	cp -v micropython-microbit-v2/src/MICROBIT.hex $(OUT)

clean:
	rm -f $(OUT)
