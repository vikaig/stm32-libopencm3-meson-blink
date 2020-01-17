project(
    'stm32-libopencm3-meson-blink',
    'c',
    default_options: [ 'buildtype=plain' ]
)

common_flags = [
    '-mcpu=cortex-m3',
    '-mthumb',
]

cflags = [
    '-Os',
    '-DSTM32F1'
]

ldflags = [
    '-Tstm32f103xb.ld',
    '--specs=nosys.specs',
    '-nostartfiles',
    '-Wl,--gc-sections'
]

sources = [
    'src/main.c'
]

cflags += common_flags
ldflags += common_flags

cc = meson.get_compiler('c')
libopencm3 = cc.find_library('opencm3_stm32f1')

exe = executable(meson.project_name() + '.elf', sources, c_args: cflags, link_args: ldflags, dependencies: libopencm3)

bin = custom_target('bin',
    input: exe,
    output: exe.full_path().split('/')[-1].split('.elf')[0] + '.bin',
    command: [find_program('objcopy'), '-O', 'binary', '@INPUT@', '@OUTPUT@'],
    build_by_default: true,
    depends: exe
)

stm32flash = find_program('stm32flash', required: false)
if stm32flash.found()
    run_target('flash', command: [ stm32flash, '-w', bin.full_path(), '-b', '115200', '-g', '0', '/dev/ttyUSB0' ], depends: bin)
endif
