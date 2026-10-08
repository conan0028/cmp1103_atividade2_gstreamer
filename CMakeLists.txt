cmake_minimum_required(VERSION 4.3)
project(CMP1103)

set(CMAKE_CXX_STANDARD 26)

# Inicializa a busca por pacotes (utilitário nativo)
find_package(PkgConfig REQUIRED)

# ==========================================
# 1. Busca e importa o GStreamer
# ==========================================
pkg_check_modules(GST REQUIRED IMPORTED_TARGET gstreamer-1.0)

# ==========================================
# 2. Busca e importa os módulos do FFmpeg
# ==========================================
pkg_check_modules(FFMPEG REQUIRED IMPORTED_TARGET libavcodec libavformat libavutil libswscale)

# ==========================================
# Executáveis da Disciplina (Adicione as novas aulas aqui)
# ==========================================

# Programa Principal
add_executable(CMP1103_main main.cpp)
target_link_libraries(CMP1103_main PkgConfig::GST PkgConfig::FFMPEG)

# Exercícios

add_executable(flashback_pipeline flashback_pipeline.c)
target_link_libraries(flashback_pipeline PkgConfig::GST)

add_executable(pipeline_atividade2_a pipeline_atividade2_a.c)
target_link_libraries(pipeline_atividade2_a PkgConfig::GST PkgConfig::FFMPEG)

add_executable(pipeline_atividade2_b pipeline_atividade2_b.c)
target_link_libraries(pipeline_atividade2_b PkgConfig::GST PkgConfig::FFMPEG)