project('lo_libs', 'cpp',
  default_options : 'cpp_std=c++11')

subprojects = ['lo_test', 'lo_adder', 'lo_strings']

chosen_subproject = get_option('module')

foreach s : subprojects
  if chosen_subproject == 'all' or chosen_subproject == s
    dep = s + '_dep'
    set_variable(dep, subproject(s).get_variable(dep))
  endif
endforeach
