project('libusb', ['c', 'cpp'], default_options : ['c_std=c99'])

src = [
    'libusb/core.c',
    'libusb/descriptor.c',
    'libusb/hotplug.c',
    'libusb/io.c',
    'libusb/os/poll_windows.c',
    'libusb/strerror.c',
    'libusb/sync.c',
    'libusb/os/threads_windows.c',
    'libusb/os/windows_nt_common.c',
    'libusb/os/windows_usbdk.c',
    'libusb/os/windows_winusb.c',
]

inc = include_directories('.', 'msvc', 'libusb')

cc = meson.get_compiler('cpp')
args = ['-w']
enc_arg = '-Wno-error=invalid-source-encoding'
if cc.has_argument(enc_arg)
  args += enc_arg
endif

libusb_lib = static_library('libusb',
  sources : src,
  name_prefix: 'lib',
  include_directories : inc,
  cpp_args : args,
)

libusb_dep = declare_dependency(link_with: libusb_lib,
  include_directories: inc,
)
