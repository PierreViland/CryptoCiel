# Définir la version minimale de CMake
cmake_minimum_required(VERSION 3.10)

# Nom du projet
project(CryptoCIEL)

# Définir les répertoires de source, objets, et bibliothèque
set(SRCDIR .)
set(CRYPTOPP_DIR "/home/kali/Desktop/crypto/cryptopp/")
#set(CRYPTOPP_DIR "./../../cryptopp/")
# Créer la liste des fichiers sources
file(GLOB SOURCES "${SRCDIR}/*.cpp")

# Créer l'exécutable
add_executable(testCryptoCiel ${SOURCES})

# Ajouter le répertoire contenant les fichiers d'en-tête (si besoin)
target_include_directories(testCryptoCiel  PRIVATE ./../cryptopp/)

# Lier la bibliothèque statique 'malib' qui se trouve dans ./Cryp
target_link_directories(testCryptoCiel PRIVATE ${LIBDIR})
target_link_libraries(testCryptoCiel PRIVATE ${CRYPTOPP_DIR}/libcryptopp.a)
