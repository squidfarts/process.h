###################################################################################
#                                                                                 #
# NAME: meson.build                                                               #
#                                                                                 #
# AUTHOR: Neil Henning.                                                           #
# WRITTEN BY: Michael Brockus.                                                    #
#                                                                                 #
# License: Unlicense                                                              #
#                                                                                 #
###################################################################################



project('process.h', 'c',
    license         : ['MIT'],
    meson_version   : '>=0.50.0',
    default_options : 
    [ 
        'werror=true',
        'optimization=3', 
        'warning_level=3', 
        'b_sanitize=address,undefined', 
        'b_lto=true', 
        'b_lundef=true'
    ])
cc = meson.get_compiler('c')
args_for_langs = 'c'



##
#
# Meson: Add compiler flags
#
##
if cc.get_id() == 'clang'
    add_project_arguments(
        cc.get_supported_arguments(
            [
            '-Wweak-vtables', 
            '-Wexit-time-destructors',
            '-Wglobal-constructors', 
            '-Wmissing-noreturn' 
            ]
        ), language: args_for_langs)
endif

if cc.get_argument_syntax() == 'gcc'
    add_project_arguments(
        cc.get_supported_arguments(
            [
            '-Wunreachable-code', 
            '-Wmissing-declarations',
            '-Wmissing-prototypes',
            '-Wredundant-decls',
            '-Wundef',
            '-Wwrite-strings',
            '-Wformat',
            '-Wformat-nonliteral',
            '-Wformat-security',
            '-Wold-style-definition',
            '-Winit-self',
            '-Wmissing-include-dirs',
            '-Waddress',
            '-Waggregate-return',
            '-Wno-multichar',
            '-Wno-parentheses',
            '-Wno-unused-parameter',
            '-Wno-type-limits',
            '-Wdeclaration-after-statement',
            '-Wvla',
            '-Wpointer-arith'
            ]
        ), language: args_for_langs)
endif

if cc.get_id() == 'msvc'
    add_project_arguments(
        cc.get_supported_arguments(
            [
            '/w44265', 
            '/w44061', 
            '/w44062', 
            '/wd4018', # implicit signed/unsigned conversion
            '/wd4146', # unary minus on unsigned (beware INT_MIN)
            '/wd4244', # lossy type conversion (e.g. double -> int)
            '/wd4305', # truncating type conversion (e.g. double -> float)
            ]
        ), language: args_for_langs)
endif



process_h_dir = include_directories('.')

process_h_dep = declare_dependency(
    include_directories: process_h_dir)
