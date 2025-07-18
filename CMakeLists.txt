cmake_minimum_required(VERSION 3.14.0)
project(Emu68-tools VERSION 0.1.0)

set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

include(CPM)
include(utils)
include(verstring)

set_emu68_tools_policies()

set(CPM_SOURCE_CACHE "${PROJECT_SOURCE_DIR}/external")
CPMUsePackageLock(package-lock.cmake)

CPMGetPackage(CPMLicenses.cmake)

cpm_licenses_create_disclaimer_target(
	write-licenses "${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/third_party.txt" "${CPM_PACKAGES}"
)

get_verstring(VERSTRING)

add_subdirectory(common)
add_subdirectory(devicetree.resource)
add_subdirectory(sdcard.device)
add_subdirectory(VideoCore.card)
add_subdirectory(unicam.resource)
add_subdirectory(68040.library)
add_subdirectory(EmuControl)
add_subdirectory(SmallPT)
add_subdirectory(Buddhabrot)
add_subdirectory(VC4Tweak)
add_subdirectory(emmc.device)
add_subdirectory(i2c.library)
add_subdirectory(lattice_i2c_prog)
add_subdirectory(SetClockI2C)
add_subdirectory(network)
add_subdirectory(Emu68rom)

# Contribs
# add_subdirectory(Emu68Contribs/Emu68Info) <-- Disabled until original gets an update
CPMGetPackage(Emu68Contribs)
CPMGetPackage(GenetDriver)
add_subdirectory(BinaryContribs)
