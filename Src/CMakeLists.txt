set(Boost_USE_MULTITHREADED ON)
set(Boost_USE_STATIC_LIBS ON)

find_package (Threads)
find_package(Boost 1.56 REQUIRED COMPONENTS
   serialization thread system chrono
   )

add_executable(
  rapsearch
  main.cpp
  HashSearch.cpp
  BlastStat.cpp
  Seg.cpp
  mergeUnit.cpp
)

target_link_libraries(rapsearch
  ${CMAKE_THREAD_LIBS_INIT}
  Boost::serialization
  Boost::thread Boost::system Boost::chrono)

add_executable(
  prerapsearch
  BuildHash.cpp
  HashSearch.cpp
  BlastStat.cpp
  Seg.cpp
  mergeUnit.cpp
)

target_link_libraries(prerapsearch
  ${CMAKE_THREAD_LIBS_INIT}
  Boost::serialization
  Boost::thread Boost::system Boost::chrono)

set(CMAKE_BUILD_TYPE RELEASE)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-write-strings")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -pg")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")

install(TARGETS rapsearch prerapsearch RUNTIME DESTINATION bin)
