pkg_config = read_config('pkg_config', 'path', 'pkg-config')

genrule(
  name = 'preprocessor-flags',
  out = 'out.txt',
  cmd = pkg_config + ' openal --cflags > $OUT',
)

genrule(
  name = 'linker-flags',
  out = 'out.txt',
  cmd = pkg_config + ' openal --libs > $OUT',
)

prebuilt_cxx_library(
  name = 'openal',
  header_namespace = '',
  header_only = True,
  exported_preprocessor_flags = [
    '@$(location :preprocessor-flags)',
  ],
  exported_linker_flags = [
    '@$(location :linker-flags)',
  ],
  visibility = [
    'PUBLIC',
  ],
)
