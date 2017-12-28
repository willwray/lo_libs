project('liftoff', 'cpp',
  default_options : 'cpp_std=c++11',
  subproject_dir : 'lo_libs')

subprojects = ['lo_test', 'lo_adder', 'lo_strings']

string_dep = subproject('lo_strings').get_variable('lo_strings_dep')
adder_dep = subproject('lo_adder').get_variable('lo_adder_dep')
test_dep = subproject('lo_test').get_variable('lo_test_dep')

shuttlelib = static_library('lo_shuttle', 'lo_shuttle.cpp',
  dependencies : [string_dep, adder_dep])

test('shuttle countdown', executable('countdown', 'shuttletest.cpp', link_with : shuttlelib,
    dependencies : [test_dep]))

executable('shuttle_launcher', 'main.cpp',
  link_with : shuttlelib)

