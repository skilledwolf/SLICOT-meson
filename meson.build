# Meson build file for the SLICOT library

project('slicot', 'fortran',
        version : '5.8',
        license : 'BSD-3-Clause',
        default_options : ['default_library=static'])

# Compiler options
add_project_arguments('-fPIC', language : 'fortran')

# Find all Fortran source files in the 'src' directory
slicot_sources = []
src_dir = 'src'
src_files = run_command('find', src_dir, '-name', '*.f').stdout().strip().split('\n')
foreach f : src_files
  slicot_sources += f
endforeach

# Define the SLICOT library
slicot_lib = library('slicot',
                     slicot_sources,
                     install : true)

# Make the library discoverable with pkg-config
import('pkgconfig').generate(slicot_lib,
                             description : 'SLICOT: Subroutine Library in Systems and Control Theory')

# Create a dependency object for other Meson projects
slicot_dep = declare_dependency(link_with : slicot_lib)

