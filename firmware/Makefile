DOCKER_COMPOSE	= docker-compose
SERVICE			= compile

OUT				= MICROBIT.hex

CURRENT_UID 	:= $(shell id -u)

.PHONY: default mpy-cross build-$(OUT) clean

default: $(OUT)

mpy-cross:
	$(DOCKER_COMPOSE) run --rm -u $(CURRENT_UID) $(SERVICE) \
    	make -C lib/micropython/mpy-cross

build-$(OUT): mpy-cross
	$(DOCKER_COMPOSE) run --rm -u $(CURRENT_UID) $(SERVICE) \
	 	bash -c 'git config --global --add safe.directory /code/lib/codal && make -C src'
	
$(OUT): build-$(OUT)
	ln -s micropython-microbit-v2/src/MICROBIT.hex $(OUT)

clean:
	rm -f $(OUT)
