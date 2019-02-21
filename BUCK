load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps_from_package')

realm_core = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/realm-core')

core_foundation = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/host-core-foundation')

security = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/host-security')

macos_srcs = glob([
  'src/impl/apple/**/*.cpp',
  'src/util/apple/**/*.cpp',
])

iphone_srcs = glob([
  'src/impl/apple/**/*.cpp',
  'src/util/apple/**/*.cpp',
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
    'src/impl/*.cpp',
    'src/util/*.cpp',
  ]),
  platform_srcs = [
    ('iphone.*', iphone_srcs),
    ('macos.*', macos_srcs),
    ('linux.*', linux_srcs),
    ('windows.*', windows_srcs),
  ],
  deps = buckaroo_deps_from_package('github.com/buckaroo-pm/realm-core'),
  platform_deps = [
    ('iphoneos.*', core_foundation + security),
    ('macos.*', core_foundation + security),
  ],
  visibility = [
    'PUBLIC',
  ],
)
