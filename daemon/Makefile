PKG_CONFIG ?= pkg-config

# Copyright (c) 2018, AT&T Intellectual Property.  All rights reserved.
#
# SPDX-License-Identifier: GPL-2.0-only

# binary name
NAME = brokerd

CFLAGS += -g
CFLAGS += -I../broker
CFLAGS += $(shell $(PKG_CONFIG) --cflags libczmq)
CFLAGS += $(shell $(PKG_CONFIG) --cflags libmnl)

LIBS += ../broker/libvyatta-route-broker.a
LIBS += $(shell $(PKG_CONFIG) --libs libczmq)
LIBS += $(shell $(PKG_CONFIG) --libs libmnl)
LIBS += -linih -pthread

OBJS = broker_main.o broker_process.o

all: $(NAME)

$(NAME): $(OBJS)
	$(CC) $(CFLAGS) $(CPPFLAGS) $(LDFLAGS) -o $(NAME) $(OBJS) $(LIBS)

clean:
	rm -f $(OBJS) $(NAME)

install: $(NAME)
	install -D $(NAME) $(DESTDIR)/usr/sbin/$(NAME)
