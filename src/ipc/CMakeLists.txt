
facelift_add_library(FaceliftIPCLibCommon
    SOURCES ipc-common/ipc-common.cpp
    HEADERS ipc-common/ipc-common.h
    LINK_LIBRARIES FaceliftModelLib FaceliftPropertyLib FaceliftCommonLib FaceliftQMLModelLib
)

facelift_add_library(FaceliftIPCLib
    SOURCES facelift-ipc.cpp #dummy.cpp
    HEADERS facelift-ipc.h
    LINK_LIBRARIES FaceliftModelLib FaceliftPropertyLib FaceliftCommonLib FaceliftQMLModelLib
)

if(FACELIFT_DBUS_IPC_ENABLED)
    add_subdirectory(dbus)
    message("DBus IPC backend enabled")
    target_link_libraries(FaceliftIPCLib FaceliftIPCLibDBus)
endif()

