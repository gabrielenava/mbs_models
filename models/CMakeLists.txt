# Install subdirectories
macro(SUBDIRLIST result curdir)
  file(GLOB children RELATIVE ${curdir} ${curdir}/*)
  set(dirlist "")
  foreach(child ${children})
    if(IS_DIRECTORY ${curdir}/${child})
      list(APPEND dirlist ${child})
    endif()
  endforeach()
  set(${result} ${dirlist})
endmacro()

# Get list of subdirectories
subdirlist(subdirs ${CMAKE_CURRENT_SOURCE_DIR})

# Install each subdirectories 
foreach (dir ${subdirs})
  install (DIRECTORY ${dir} DESTINATION ${CMAKE_INSTALL_PREFIX}/models)
endforeach ()
