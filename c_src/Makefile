compile: ../priv/bcrypt


ERTS_INCLUDE_DIR ?= $(shell erl -noshell -s init stop -eval "io:format(\"~s/erts-~s/include/\", [code:root_dir(), erlang:system_info(version)]).")
ERL_INTERFACE_INCLUDE_DIR ?= $(shell erl -noshell -s init stop -eval "io:format(\"~s\", [code:lib_dir(erl_interface, include)]).")
ERL_INTERFACE_LIB_DIR ?= $(shell erl -noshell -s init stop -eval "io:format(\"~s\", [code:lib_dir(erl_interface, lib)]).")
ERL_CFLAGS ?= -I$(ERL_INTERFACE_INCLUDE_DIR)

ifeq ($(shell uname),SunOS)
  ERL_LDFLAGS ?= -L$(ERL_INTERFACE_LIB_DIR) -lerl_interface -lei -lnsl
else
  ERL_LDFLAGS ?= -L$(ERL_INTERFACE_LIB_DIR) -lerl_interface -lei
endif

../priv/bcrypt:
	$(CC) $(CFLAGS) $(ERL_CFLAGS) $(EXE_LDFLAGS) bcrypt_port.c bcrypt.o blowfish.o $(LDFLAGS) $(ERL_LDFLAGS) -lpthread -o ../priv/bcrypt

clean:
	@rm -f ../priv/bcrypt

.PHONY: clean compile
