#
# CMake build system file for EVEmu.
#
# Author: Bloody.Rabbit
#

################
# Dependencies #
################
ADD_SUBDIRECTORY( "${PROJECT_SOURCE_DIR}/dep/utils"
                  "${PROJECT_BINARY_DIR}/dep/utils" )

FIND_PACKAGE( "UTF8CPP" QUIET )

IF( NOT UTF8CPP_FOUND )
  ADD_SUBDIRECTORY( "${PROJECT_SOURCE_DIR}/dep/utf8cpp"
                    "${PROJECT_BINARY_DIR}/dep/utf8cpp" )

  SET( UTF8CPP_FOUND        TRUE )
  SET( UTF8CPP_INCLUDE_DIRS ${utf8cpp_INCLUDE_DIRS} )
  SET( UTF8CPP_LIBRARIES    "utf8cpp" )
ENDIF( NOT UTF8CPP_FOUND )

##############
# Initialize #
##############
SET( TARGET_NAME        "eve-common" )
SET( TARGET_INCLUDE_DIR "${PROJECT_SOURCE_DIR}/include/${TARGET_NAME}" )
SET( TARGET_SOURCE_DIR  "${PROJECT_SOURCE_DIR}/src/${TARGET_NAME}" )
SET( TARGET_PACKETS_DIR "${PROJECT_BINARY_DIR}/src/${TARGET_NAME}" )

SET( TARGET_INCLUDE_DIRS
     ${UTF8CPP_INCLUDE_DIRS}
     ${utils_INCLUDE_DIRS}
     ${common_INCLUDE_DIRS}
     "${TARGET_INCLUDE_DIR}"
     "${TARGET_PACKETS_DIR}" )

# Export directories
SET( ${TARGET_NAME}_INCLUDE_DIRS
     ${TARGET_INCLUDE_DIRS}
     PARENT_SCOPE )

#########
# Files #
#########
SET( INCLUDE
     "${TARGET_INCLUDE_DIR}/EVECommonPCH.h"
     "${TARGET_INCLUDE_DIR}/EVEVersion.h" )
SET( SOURCE
     "" )

SET( cache_INCLUDE
     "${TARGET_INCLUDE_DIR}/cache/CachedObjectMgr.h" )
SET( cache_SOURCE
     "${TARGET_SOURCE_DIR}/cache/CachedObjectMgr.cpp" )

SET( database_INCLUDE
     "${TARGET_INCLUDE_DIR}/database/EVEDBUtils.h"
     "${TARGET_INCLUDE_DIR}/database/RowsetReader.h"
     "${TARGET_INCLUDE_DIR}/database/RowsetToSQL.h" )
SET( database_SOURCE
     "${TARGET_SOURCE_DIR}/database/EVEDBUtils.cpp"
     "${TARGET_SOURCE_DIR}/database/RowsetReader.cpp"
     "${TARGET_SOURCE_DIR}/database/RowsetToSQL.cpp" )

SET( destiny_INCLUDE
     "${TARGET_INCLUDE_DIR}/destiny/DestinyBinDump.h"
     "${TARGET_INCLUDE_DIR}/destiny/DestinyStructs.h" )
SET( destiny_SOURCE
     "${TARGET_SOURCE_DIR}/destiny/DestinyBinDump.cpp" )

SET( marshal_INCLUDE
     "${TARGET_INCLUDE_DIR}/marshal/EVEMarshal.h"
     "${TARGET_INCLUDE_DIR}/marshal/EVEMarshalOpcodes.h"
     "${TARGET_INCLUDE_DIR}/marshal/EVEMarshalStringTable.h"
     "${TARGET_INCLUDE_DIR}/marshal/EVEUnmarshal.h" )
SET( marshal_SOURCE
     "${TARGET_SOURCE_DIR}/marshal/EVEMarshal.cpp"
     "${TARGET_SOURCE_DIR}/marshal/EVEMarshalStringTable.cpp"
     "${TARGET_SOURCE_DIR}/marshal/EVEUnmarshal.cpp" )

SET( network_INCLUDE
     "${TARGET_INCLUDE_DIR}/network/EVEPktDispatch.h"
     "${TARGET_INCLUDE_DIR}/network/EVESession.h"
     "${TARGET_INCLUDE_DIR}/network/EVETCPConnection.h"
     "${TARGET_INCLUDE_DIR}/network/EVETCPServer.h"
     "${TARGET_INCLUDE_DIR}/network/packet_types.h" )
SET( network_SOURCE
     "${TARGET_SOURCE_DIR}/network/EVEPktDispatch.cpp"
     "${TARGET_SOURCE_DIR}/network/EVESession.cpp"
     "${TARGET_SOURCE_DIR}/network/EVETCPConnection.cpp" )

SET( packets_INCLUDE
     "${TARGET_PACKETS_DIR}/packets/AccountPkts.h"
     "${TARGET_PACKETS_DIR}/packets/CorporationPkts.h"
     "${TARGET_PACKETS_DIR}/packets/Crypto.h"
     "${TARGET_PACKETS_DIR}/packets/Destiny.h"
     "${TARGET_PACKETS_DIR}/packets/DogmaIM.h"
     "${TARGET_PACKETS_DIR}/packets/General.h"
     "${TARGET_PACKETS_DIR}/packets/Character.h"
     "${TARGET_PACKETS_DIR}/packets/Inventory.h"
     "${TARGET_PACKETS_DIR}/packets/Language.h"
     "${TARGET_PACKETS_DIR}/packets/LSCPkts.h"
     "${TARGET_PACKETS_DIR}/packets/Manufacturing.h"
     "${TARGET_PACKETS_DIR}/packets/Market.h"
     "${TARGET_PACKETS_DIR}/packets/Missions.h"
     "${TARGET_PACKETS_DIR}/packets/ObjectCaching.h"
     "${TARGET_PACKETS_DIR}/packets/Sovereignty.h"
     "${TARGET_PACKETS_DIR}/packets/Standing2.h"
     "${TARGET_PACKETS_DIR}/packets/Trade.h"
     "${TARGET_PACKETS_DIR}/packets/Tutorial.h"
     "${TARGET_PACKETS_DIR}/packets/Wallet.h"
     "${TARGET_PACKETS_DIR}/packets/Mail.h" )
SET( packets_SOURCE
     "${TARGET_PACKETS_DIR}/packets/AccountPkts.cpp"
     "${TARGET_PACKETS_DIR}/packets/CorporationPkts.cpp"
     "${TARGET_PACKETS_DIR}/packets/Crypto.cpp"
     "${TARGET_PACKETS_DIR}/packets/Destiny.cpp"
     "${TARGET_PACKETS_DIR}/packets/DogmaIM.cpp"
     "${TARGET_PACKETS_DIR}/packets/General.cpp"
     "${TARGET_PACKETS_DIR}/packets/Character.cpp"
     "${TARGET_PACKETS_DIR}/packets/Inventory.cpp"
     "${TARGET_PACKETS_DIR}/packets/Language.cpp"
     "${TARGET_PACKETS_DIR}/packets/LSCPkts.cpp"
     "${TARGET_PACKETS_DIR}/packets/Manufacturing.cpp"
     "${TARGET_PACKETS_DIR}/packets/Market.cpp"
     "${TARGET_PACKETS_DIR}/packets/Missions.cpp"
     "${TARGET_PACKETS_DIR}/packets/ObjectCaching.cpp"
     "${TARGET_PACKETS_DIR}/packets/Sovereignty.cpp"
     "${TARGET_PACKETS_DIR}/packets/Standing2.cpp"
     "${TARGET_PACKETS_DIR}/packets/Trade.cpp"
     "${TARGET_PACKETS_DIR}/packets/Tutorial.cpp"
     "${TARGET_PACKETS_DIR}/packets/Wallet.cpp"
     "${TARGET_PACKETS_DIR}/packets/Mail.cpp" )
SET( packets_XMLP
     "${TARGET_SOURCE_DIR}/packets/AccountPkts.xmlp"
     "${TARGET_SOURCE_DIR}/packets/CorporationPkts.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Crypto.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Destiny.xmlp"
     "${TARGET_SOURCE_DIR}/packets/DogmaIM.xmlp"
     "${TARGET_SOURCE_DIR}/packets/General.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Character.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Inventory.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Language.xmlp"
     "${TARGET_SOURCE_DIR}/packets/LSCPkts.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Manufacturing.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Market.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Missions.xmlp"
     "${TARGET_SOURCE_DIR}/packets/ObjectCaching.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Sovereignty.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Standing2.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Trade.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Tutorial.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Wallet.xmlp"
     "${TARGET_SOURCE_DIR}/packets/Mail.xmlp" )

SET( python_INCLUDE
     "${TARGET_INCLUDE_DIR}/python/PyDumpVisitor.h"
     "${TARGET_INCLUDE_DIR}/python/PyLookupDump.h"
     "${TARGET_INCLUDE_DIR}/python/PyPacket.h"
     "${TARGET_INCLUDE_DIR}/python/PyRep.h"
     "${TARGET_INCLUDE_DIR}/python/PyTraceLog.h"
     "${TARGET_INCLUDE_DIR}/python/PyVisitor.h"
     "${TARGET_INCLUDE_DIR}/python/PyXMLGenerator.h" )
SET( python_SOURCE
     "${TARGET_SOURCE_DIR}/python/PyDumpVisitor.cpp"
     "${TARGET_SOURCE_DIR}/python/PyLookupDump.cpp"
     "${TARGET_SOURCE_DIR}/python/PyPacket.cpp"
     "${TARGET_SOURCE_DIR}/python/PyRep.cpp"
     "${TARGET_SOURCE_DIR}/python/PyVisitor.cpp"
     "${TARGET_SOURCE_DIR}/python/PyXMLGenerator.cpp" )

SET( python_classes_INCLUDE
     "${TARGET_INCLUDE_DIR}/python/classes/PyDatabase.h"
     "${TARGET_INCLUDE_DIR}/python/classes/PyExceptions.h"
     "${TARGET_INCLUDE_DIR}/python/classes/PyUtils.h" )
SET( python_classes_SOURCE
     "${TARGET_SOURCE_DIR}/python/classes/PyDatabase.cpp"
     "${TARGET_SOURCE_DIR}/python/classes/PyExceptions.cpp"
     "${TARGET_SOURCE_DIR}/python/classes/PyUtils.cpp" )

SET( tables_INCLUDE
     "${TARGET_INCLUDE_DIR}/tables/invCategories.h"
     "${TARGET_INCLUDE_DIR}/tables/invGroups.h" )
SET( tables_SOURCE
     "" )

SET( utils_INCLUDE
     "${TARGET_INCLUDE_DIR}/utils/EVEUtils.h"
     "${TARGET_INCLUDE_DIR}/utils/EvilNumber.h"
     "${TARGET_INCLUDE_DIR}/utils/Util.h" )
SET( utils_SOURCE
     "${TARGET_SOURCE_DIR}/utils/EVEUtils.cpp"
     "${TARGET_SOURCE_DIR}/utils/EvilNumber.cpp"
     "${TARGET_SOURCE_DIR}/utils/util.cpp" )

#####################
# Setup the library #
#####################
INCLUDE_DIRECTORIES( ${TARGET_INCLUDE_DIRS} )

SOURCE_GROUP( "include"                  FILES ${INCLUDE} )
SOURCE_GROUP( "include\\cache"           FILES ${cache_INCLUDE} )
SOURCE_GROUP( "include\\database"        FILES ${database_INCLUDE} )
SOURCE_GROUP( "include\\destiny"         FILES ${destiny_INCLUDE} )
SOURCE_GROUP( "include\\marshal"         FILES ${marshal_INCLUDE} )
SOURCE_GROUP( "include\\network"         FILES ${network_INCLUDE} )
SOURCE_GROUP( "include\\packets"         FILES ${packets_INCLUDE} )
SOURCE_GROUP( "include\\python"          FILES ${python_INCLUDE} )
SOURCE_GROUP( "include\\python\\classes" FILES ${python_classes_INCLUDE} )
SOURCE_GROUP( "include\\tables"          FILES ${tables_INCLUDE} )
SOURCE_GROUP( "include\\utils"           FILES ${utils_INCLUDE} )

SOURCE_GROUP( "src"                  FILES ${SOURCE} )
SOURCE_GROUP( "src\\cache"           FILES ${cache_SOURCE} )
SOURCE_GROUP( "src\\database"        FILES ${database_SOURCE} )
SOURCE_GROUP( "src\\destiny"         FILES ${destiny_SOURCE} )
SOURCE_GROUP( "src\\marshal"         FILES ${marshal_SOURCE} )
SOURCE_GROUP( "src\\network"         FILES ${network_SOURCE} )
SOURCE_GROUP( "src\\packets"         FILES ${packets_SOURCE} )
SOURCE_GROUP( "src\\packets\\xmlp"   FILES ${packets_XMLP} )
SOURCE_GROUP( "src\\python"          FILES ${python_SOURCE} )
SOURCE_GROUP( "src\\python\\classes" FILES ${python_classes_SOURCE} )
SOURCE_GROUP( "src\\tables"          FILES ${tables_SOURCE} )
SOURCE_GROUP( "src\\utils"           FILES ${utils_SOURCE} )

FILE( MAKE_DIRECTORY "${TARGET_PACKETS_DIR}/packets" )
ADD_CUSTOM_COMMAND( OUTPUT ${packets_INCLUDE} ${packets_SOURCE}
                    COMMAND "xmlpktgen"
                    ARGS -I "${TARGET_PACKETS_DIR}/packets"
                         -S "${TARGET_PACKETS_DIR}/packets"
                         ${packets_XMLP}
                    DEPENDS "xmlpktgen"
                    COMMENT "Generating packet files..." )

ADD_LIBRARY( "${TARGET_NAME}"
             ${INCLUDE}                ${SOURCE}
             ${cache_INCLUDE}          ${cache_SOURCE}
             ${database_INCLUDE}       ${database_SOURCE}
             ${destiny_INCLUDE}        ${destiny_SOURCE}
             ${marshal_INCLUDE}        ${marshal_SOURCE}
             ${network_INCLUDE}        ${network_SOURCE}
             ${packets_INCLUDE}        ${packets_SOURCE}        ${packets_XMLP}
             ${python_INCLUDE}         ${python_SOURCE}
             ${python_classes_INCLUDE} ${python_classes_SOURCE}
             ${tables_INCLUDE}         ${tables_SOURCE}
             ${utils_INCLUDE}          ${utils_SOURCE} )

TARGET_BUILD_PCH( "${TARGET_NAME}"
                  "${TARGET_INCLUDE_DIR}/EVECommonPCH.h"
                  "${TARGET_SOURCE_DIR}/utils/EVEUtils.cpp" )
TARGET_LINK_LIBRARIES( "${TARGET_NAME}"
                       "common" "utils" )
