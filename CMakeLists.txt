# Définir la version minimale de CMake
cmake_minimum_required(VERSION 3.10)

# Nom du projet
project(CryptoLibrary)

# Définir les répertoires des sources
set(SRCDIR .)  # Assurez-vous que les fichiers .cpp et .h se trouvent dans ce répertoire

# Définir le répertoire pour la bibliothèque cryptopp
set(CRYPTOPP_DIR "./../cryptopp")

# Ajouter le répertoire contenant les fichiers d'en-tête
include_directories(${CRYPTOPP_DIR})

# Lier la bibliothèque cryptopp
link_directories(${CRYPTOPP_DIR})

# Créer la bibliothèque statique
add_library(CryptoCIEL STATIC
    ${SRCDIR}/AesGestion.cpp
    ${SRCDIR}/RsaGestion.cpp
    ${SRCDIR}/HashGestion.cpp
)

# Spécifier les fichiers d'en-tête pour la bibliothèque
target_include_directories(CryptoCIEL PUBLIC
    ${SRCDIR}        # Inclure les fichiers d'en-tête de la bibliothèque
    ${CRYPTOPP_DIR}  # Inclure les fichiers d'en-tête de cryptopp
)

# Lier la bibliothèque cryptopp à la bibliothèque CryptoLib
target_link_libraries(CryptoCIEL PRIVATE cryptopp)

