project('liftoff', 'cpp',
  default_options : 'cpp_std=c++11',
  subproject_dir : 'lo_libs')

subprojects = ['lo_test', 'lo_adder', 'lo_strings']

chosen_subproject = get_option('module')

foreach s : subprojects
  if chosen_subproject == 'all' or chosen_subproject == s
    subproject(s)
  endif
endforeach

string_dep = dependency('lo_strings', fallback : ['lo_strings', 'lo_strings_dep'])
adder_dep = dependency('lo_adder', fallback : ['lo_adder', 'lo_adder_dep'])
test_dep = dependency('lo_test', fallback : ['lo_test', 'lo_test_dep'])

shuttlelib = static_library('lo_shuttle', 'lo_shuttle.cpp',
  dependencies : [string_dep, adder_dep])

test('shuttle countdown', executable('countdown', 'shuttletest.cpp', link_with : shuttlelib,
    dependencies : [test_dep]))

executable('shuttle_launcher', 'main.cpp',
  link_with : shuttlelib)

