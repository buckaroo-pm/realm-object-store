load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps')

macos_srcs = glob([
  'src/impl/apple/**/*.cpp',
])

iphone_srcs = glob([
  'src/impl/apple/**/*.cpp',
])

linux_srcs = glob([
  'src/impl/epoll/**/*.cpp',
])

windows_srcs = glob([
  'src/impl/windows/**/*.cpp',
])

cxx_library(
  name = 'object-store',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('src', '**/*.hpp'),
  ]),
  srcs = glob([
    'src/*.cpp',
  ]),
  platform_srcs = [
    ('iphone.*', iphone_srcs),
    ('macos.*', macos_srcs),
    ('linux.*', linux_srcs),
    ('windows.*', windows_srcs),
  ],
  deps = buckaroo_deps(),
  visibility = [
    'PUBLIC',
  ],
)
