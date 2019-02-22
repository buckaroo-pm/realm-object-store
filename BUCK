load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps_from_package')

realm_core = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/realm-core')

zlib = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/madler-zlib')

realm_sync_cocoa = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/realm-sync-cocoa')

core_foundation = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/host-core-foundation')

security = \
  buckaroo_deps_from_package('github.com/buckaroo-pm/host-security')

macos_srcs = glob([
  'src/impl/apple/**/*.cpp',
  'src/util/apple/**/*.cpp',
  'src/sync/impl/apple/**/*.cpp',
])

iphone_srcs = glob([
  'src/impl/apple/**/*.cpp',
  'src/util/apple/**/*.cpp',
  'src/sync/impl/apple/**/*.cpp',
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
    'src/sync/*.cpp',
    'src/sync/impl/*.cpp',
  ]),
  platform_srcs = [
    ('iphone.*', iphone_srcs),
    ('macos.*', macos_srcs),
    ('linux.*', linux_srcs),
    ('windows.*', windows_srcs),
  ],
  preprocessor_flags = [
    '-DREALM_ENABLE_SYNC=1',
  ],
  deps = realm_core + zlib,
  platform_deps = [
    ('iphoneos.*', core_foundation + security + realm_sync_cocoa),
    ('macos.*', core_foundation + security + realm_sync_cocoa),
  ],
  visibility = [
    'PUBLIC',
  ],
)
