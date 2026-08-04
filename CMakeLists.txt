cmake_minimum_required(VERSION 3.1)
set(EXE_NAME spi-nand-prog)
project(${EXE_NAME} C)
find_package(PkgConfig)
pkg_check_modules(libusb-1.0 REQUIRED libusb-1.0)

set(CMAKE_C_FLAGS_RELWITHDEBINFO "-O3 -ggdb -Wall")

include_directories(include ${libusb-1.0_INCLUDEDIR})

set(SPI_MEM_SRCS
	spi-mem/spi-mem.c
	spi-mem/spi-mem-drvs.c
	spi-mem/spi-mem-fx2qspi.c
	spi-mem/spi-mem-serprog.c
	spi-mem/ch347/ch347.c
	spi-mem/ch347/spi-mem.c
)

set(SPI_NAND_SRCS
	spi-nand/alliancememory.c
	spi-nand/ato.c
	spi-nand/biwin.c
	spi-nand/chucun.c
	spi-nand/core.c
	spi-nand/dosilicon.c
	spi-nand/esmt.c
	spi-nand/etron.c
	spi-nand/fison.c
	spi-nand/fmsh.c
	spi-nand/foresee.c
	spi-nand/gigadevice.c
	spi-nand/gsto.c
	spi-nand/hiksemi.c
	spi-nand/hyf.c
	spi-nand/issi.c
	spi-nand/jsc.c
	spi-nand/kingston.c
	spi-nand/macronix.c
	spi-nand/micron.c
	spi-nand/mira.c
	spi-nand/mk.c
	spi-nand/paragon.c
	spi-nand/silicongo.c
	spi-nand/skyhigh.c
	spi-nand/titan.c
	spi-nand/toshiba.c
	spi-nand/tym.c
	spi-nand/unim.c
	spi-nand/winbond.c
	spi-nand/wodposit.c
	spi-nand/xincun.c
	spi-nand/xtx.c
	spi-nand/zbit.c
	spi-nand/zentel.c
)
add_executable(${EXE_NAME} ${SPI_MEM_SRCS} ${SPI_NAND_SRCS} main.c flashops.c)
target_link_libraries(${EXE_NAME} ${libusb-1.0_LIBRARIES})
