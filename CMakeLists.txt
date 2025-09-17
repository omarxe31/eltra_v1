cmake_minimum_required(VERSION 3.15)

project(EltraV1 VERSION 1.0 LANGUAGES CXX)

# JUCE موجود كـ submodule أو هنسحبه في GitHub Actions
set(JUCE_DIR "${CMAKE_SOURCE_DIR}/JUCE")

# نضيف JUCE
add_subdirectory(${JUCE_DIR})

juce_add_plugin(EltraV1
    PLUGIN_MANUFACTURER_CODE Al8i
    PLUGIN_CODE ElV1
    FORMATS VST3
    PRODUCT_NAME "Eltra V1"
)

target_sources(EltraV1 PRIVATE
    PluginProcessor.cpp
    PluginProcessor.h
    PluginEditor.cpp
    PluginEditor.h
)

target_link_libraries(EltraV1 PRIVATE
    juce::juce_audio_utils
    juce::juce_dsp
    juce::juce_gui_extra
    juce::juce_gui_basics
)
