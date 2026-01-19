project('emscripten_hello', 'cpp',
  version: '0.1.0',
  default_options: ['cpp_std=c++17']
)

cpp = meson.get_compiler('cpp')
incs = include_directories('include')
srcs = files('src/main.cpp')
target = 'hello'

if host_machine.system() == 'emscripten'
  args = meson.get_external_property('emcc_args', []) + meson.get_external_property('emcc_link_args', [])
  if get_option('buildtype') == 'release'
    args += ['-O3', '-sASSERTIONS=0', '-sSAFE_HEAP=0']
  endif
  custom_target(target,
    input: srcs,
    output: [target + '.html', target + '.js', target + '.wasm'],
    command: cpp.cmd_array() + [
      '@INPUT@', '-o', '@OUTPUT0@', '-I', meson.project_source_root() / 'include'
    ] + args,
    build_by_default: true,
  )
else
  executable(target,
    sources: srcs,
    include_directories: incs,
    build_by_default: true,
    install: false,
  )
endif
