project('spiel-it',
  license: 'GPL-3',
  version: run_command(
    'python3', '-c',
    'from spiel_it.version import __version__; print(__version__, end="")',
    check: true
  ).stdout(),
)

# Dependencies
python_module = import('python')
py = python_module.find_installation('python3', required: true, modules: [
  'gi',
])

dependency('spiel-1.0', fallback: ['libspiel', 'spiel_lib_dep'])

application_id = 'org.project_spiel.SpielIt'
app_data_dir = get_option('prefix') / get_option('datadir') / 'spiel-it'
iconsdir = get_option('prefix') / get_option('datadir') / 'icons'
desktop_file_dir = get_option('prefix') / get_option('datadir') / 'applications'
# Configuration used in template files
config = configuration_data()
config.set('app_data_dir', app_data_dir)
config.set('python_path', py.full_path())

configure_file(
  input: 'spiel-it.py.in',
  output: 'spiel-it',
  configuration: config,
  install_mode: 'rwxr-xr-x',
  install_dir: get_option('bindir'),
)

# Python module
install_subdir(
  'spiel_it',
  install_dir: py.get_install_dir(),
)

# ui file
install_data(
  'data/spiel-it.ui',
  install_dir: app_data_dir,
)

#icon
install_data(
  'spiel-it.svg',
  install_dir: iconsdir / 'hicolor' / 'symbolic' / 'apps',
  rename: '@0@.svg'.format(application_id)
)

# Desktop file
desktop_conf = configuration_data()
desktop_conf.set('icon', application_id)
configure_file(
  input: 'data/org.project_spiel.SpielIt.desktop.in',
  output: 'org.project_spiel.SpielIt.desktop',
  configuration: desktop_conf,
  install_dir: desktop_file_dir
)
