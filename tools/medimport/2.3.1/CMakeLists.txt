SET(medimport231_SOURCES
  MED231datasetNumEcrire.c
  MED231champLireEtUnlink.c
  MAJ_231_232_maillagesbuilt.cxx
  MAJ_231_232_chaine.c
  MED231datasetNumEcrirebuilt.cxx
  MED231champNormaliserbuilt.cxx
  MAJ_231_232_chainebuilt.cxx
  MED231champLireEtUnlinkbuilt.cxx
  MAJ_231_232_champs.c
  MAJ_231_232_champsbuilt.cxx
  MED231datasetNumLire.c
  MAJ_231_232_maillages.c
  MED231champRefInfoEtRenMaa.c
  MED231champInfoEtRen.c
  MED231champInfoEtRenbuilt.cxx
  MED231datasetNumLirebuilt.cxx
  MED231champNormaliser.c
  MED231champRefInfoEtRenMaabuilt.cxx
)

# Include are specific for the 2.3.6 version - make sure they get incl first:
INCLUDE_DIRECTORIES(BEFORE 
    "${PROJECT_BINARY_DIR}/include/2.3.6"
    "${PROJECT_SOURCE_DIR}/include/2.3.6")

ADD_DEFINITIONS(-DMED_API_23)

# On Win platform, we need to make sure symbols are properly exported in
# the intermediary OBJECT targets
# The definition "-D<target>_EXPORTS" is normally added automatically by CMake
# when building Win DLL,
# but this doesn't work when using intermediary targets (ADD_LIBRARY(... OBJECT ...)
IF(WIN32)
  ADD_DEFINITIONS(-Dmedimport_EXPORTS)
ENDIF()

ADD_LIBRARY(_medimport231 OBJECT ${medimport231_SOURCES})

ADD_LIBRARY(_medimport231_static OBJECT ${medimport231_SOURCES})
MED_SET_DEFINITIONS(_medimport231_static MED3_USESTATIC)
