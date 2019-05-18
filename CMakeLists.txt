cmake_minimum_required(VERSION 3.9)
project(fido VERSION 1)

include(GNUInstallDirs)

add_library(fido SHARED
	src/Adadelta.cpp
	src/Backpropagation.cpp
	src/FidoControlSystem.cpp
	src/GeneticAlgo.cpp
	src/Interpolator.cpp
	src/Layer.cpp
	src/LSInterpolator.cpp
	src/main.cpp
	src/NeuralNet.cpp
	src/Neuron.cpp
	src/Pruner.cpp
	src/QLearn.cpp
	src/SGDTrainer.cpp
	src/WireFitQLearn.cpp
)

set_target_properties(fido PROPERTIES
	VERSION ${PROJECT_VERSION}
	SOVERSION 1
	PUBLIC_HEADER 
		include/ActivationFunctions.h
		include/Adadelta.h
		include/Backpropagation.h
		include/FidoControlSystem.h
		include/Fido.h
		include/GeneticAlgo.h
		include/Interpolator.h
		include/Layer.h
		include/Learner.h
		include/LSInterpolator.h
		include/NeuralNet.h
		include/Neuron.h
		include/Pruner.h
		include/QLearn.h
		include/SGDTrainer.h
		include/Trainer.h
		include/WireFitQLearn.h
)

configure_file(fido.pc.in fido.pc @ONLY)

target_include_directories(fido PRIVATE .)

install(TARGETS fido
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
	PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

install(FILES ${CMAKE_BINARY_DIR}/fido.pc
	    DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
