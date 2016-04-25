.PHONY: main

DEBUG =

INVENTORY 				:=
UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Linux)
    INVENTORY += inventory-docker
endif
ifeq ($(UNAME_S),Darwin)
    INVENTORY += inventory-docker-machine
endif

all: executable

debug: DEBUG = -vvvv
debug: executable

executable:
	ansible-playbook -i $(INVENTORY) main.yml $(DEBUG)
