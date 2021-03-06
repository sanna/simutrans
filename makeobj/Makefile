
#OSTYPE = beos
#OSTYPE = cygwin
#OSTYPE = freebsd
#OSTYPE = linux
OSTYPE = mingw

LN= $(CC)

ifeq ($(OSTYPE),mingw)
  LDLIBS=-lmingw32 -lpng -lz -lstdc++
  CFLAGS= -O -g
  CXXFLAGS= -O -g
endif

ifeq ($(OSTYPE),linux)
  LDLIBS=-lpng -lz -lstdc++ -lm
  CFLAGS   = -O
  CXXFLAGS = -O
endif

ifeq ($(OSTYPE),beos)
  LDLIBS=-lpng -lz -lstdc++
  CFLAGS=-O
  CXXFLAGS=-O
endif

ifeq ($(OSTYPE),mac)
  LDLIBS=-lpng -lz -lstdc++ -lm
  CFLAGS=-O
  CXXFLAGS=-O
endif

ifdef FLAGS
  CFLAGS   += $(FLAGS)
  CXXFLAGS += $(FLAGS)
endif

CXXFLAGS += -DMAKEOBJ

SOURCES=makeobj.cc

OBJECTS=makeobj.o ../besch/writer/obj_node.o \
 ../simmem.o \
 ../dataobj/freelist.o \
 ../dataobj/tabfile.o ../utils/cstring_t.o ../utils/simstring.o ../utils/searchfolder.o \
 ../tpl/debug_helper.o \
 ../utils/dr_rdpng.o \
 ../besch/writer/building_writer.o ../besch/writer/good_writer.o \
 ../besch/writer/skin_writer.o ../besch/writer/image_writer.o \
 ../besch/writer/imagelist2d_writer.o ../besch/writer/imagelist_writer.o \
 ../besch/writer/obj_writer.o ../besch/writer/root_writer.o \
 ../besch/writer/xref_writer.o ../besch/writer/text_writer.o \
 ../besch/writer/tree_writer.o ../besch/writer/factory_writer.o \
 ../besch/writer/bridge_writer.o ../besch/writer/vehicle_writer.o \
 ../besch/writer/way_writer.o ../besch/writer/way_obj_writer.o\
 ../besch/writer/ground_writer.o  ../besch/writer/sound_writer.o \
 ../besch/writer/crossing_writer.o  ../besch/writer/tunnel_writer.o \
 ../besch/writer/citycar_writer.o  ../besch/writer/pedestrian_writer.o \
 ../besch/writer/sim_writer.o ../besch/writer/roadsign_writer.o \
 ../besch/writer/groundobj_writer.o \
 ../besch/writer/get_waytype.o ../besch/writer/get_climate.o \
 ../simdebug.o ../utils/log.o ../simtools.o

all: makeobj

makeobj: $(OBJECTS)
	$(LN) $(CXXFLAGS) $(LDFLAGS) -o makeobj $(OBJECTS) $(LDLIBS)

clean:
	rm -f $(OBJECTS)

depend:
	makedepend $(SOURCES)

dep: depdep


depdep: $(SOURCES)
	$(CC) -M $^ > .depend


ifeq (.depend,$(wildcard .depend))
    # include .depend only if it exists
include .depend
endif
