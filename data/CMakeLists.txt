install(DIRECTORY config phroms resources state
  TYPE DATA)

install(DIRECTORY media/discs media/scsi media/tapes
  DESTINATION ${CMAKE_INSTALL_DATADIR}/media)

install(DIRECTORY roms/bbc roms/bbcint roms/bplus roms/m128 roms/other
  DESTINATION ${CMAKE_INSTALL_DATADIR}/roms)
