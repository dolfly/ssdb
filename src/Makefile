include ../build_config.mk

OBJS = proc_kv.o proc_hash.o proc_zset.o proc_queue.o proc_set.o \
	backend_dump.o backend_sync2.o slave.o \
	serv.o proc_cluster.o cluster.o cluster_store.o cluster_migrate.o range_migrate.o \
	rpl_info_handler.o rpl_mi.o
LIBS = ./ssdb/libssdb.a ./net/libnet.a ./util/libutil.a
EXES = ../ssdb-server


all: ${OBJS} ssdb-server.o
	${CXX} -o ../ssdb-server ssdb-server.o ${OBJS} ${LIBS} ${CLIBS} client/SSDB_impl.o
cluster_migrate.o: cluster_migrate.h cluster_migrate.cpp
	${CXX} ${CFLAGS} -I./client -c cluster_migrate.cpp
proc_cluster.o: serv.h proc_cluster.cpp
	${CXX} ${CFLAGS} -c proc_cluster.cpp
cluster.o: cluster.h cluster.cpp
	${CXX} ${CFLAGS} -c cluster.cpp
cluster_store.o: cluster_store.h cluster_store.cpp
	${CXX} ${CFLAGS} -c cluster_store.cpp
range_migrate.o: range_migrate.h range_migrate.cpp
	${CXX} ${CFLAGS} -c range_migrate.cpp

rpl_info_handler.o: rpl_info_handler.h rpl_info_handler.cpp
	${CXX} ${CFLAGS} -c rpl_info_handler.cpp
rpl_mi.o: rpl_mi.h rpl_mi.cpp
	${CXX} ${CFLAGS} -c rpl_mi.cpp

ssdb-server.o: ssdb-server.cpp
	${CXX} ${CFLAGS} -c ssdb-server.cpp
slave.o: slave.h slave.cpp
	${CXX} ${CFLAGS} -c slave.cpp
backend_dump.o: backend_dump.h backend_dump.cpp
	${CXX} ${CFLAGS} -c backend_dump.cpp
backend_sync2.o: backend_sync2.h backend_sync2.cpp
	${CXX} ${CFLAGS} -c backend_sync2.cpp

proc.o: serv.h proc.cpp
	${CXX} ${CFLAGS} -c proc.cpp
proc_kv.o: serv.h proc_kv.cpp
	${CXX} ${CFLAGS} -c proc_kv.cpp
proc_hash.o: serv.h proc_hash.cpp
	${CXX} ${CFLAGS} -c proc_hash.cpp
proc_zset.o: serv.h proc_zset.cpp
	${CXX} ${CFLAGS} -c proc_zset.cpp
proc_queue.o: serv.h proc_queue.cpp
	${CXX} ${CFLAGS} -c proc_queue.cpp
proc_set.o: serv.h proc_set.cpp
	${CXX} ${CFLAGS} -c proc_set.cpp

serv.o: serv.h serv.cpp 
	${CXX} ${CFLAGS} -c serv.cpp

clean:
	rm -f ${EXES} *.o *.exe *.a

