# anttweakbar build script
# dependencies: libsdl1.2-dev libglfw3-dev freeglut3-dev
# glfw not available in Ubuntu 22.04

AddOption('--debug-build', action='store_true', dest='debug_build',
	help='debug build', default=False)

tbar_env = Environment()
#tbar_env.ParseConfig('pkg-config --cflags --libs gl glu x11 sdl libglfw')
tbar_env.ParseConfig('pkg-config --cflags --libs gl glu x11 sdl')


tbar_env.Append(LIBS=['stdc++'])

if GetOption('debug_build'):
	tbar_env.Append(CCFLAGS=['-g', '-O0', '-std=c++98'])
else:
	tbar_env.Append(CCFLAGS=['-O2', '-std=c++98'])

# linux only
#tbar_src = Split('''
#	TwColors.cpp
#	TwFonts.cpp
#	TwOpenGL.cpp
#	TwOpenGLCore.cpp
#	TwBar.cpp
#	TwMgr.cpp
#	TwPrecomp.cpp
#	LoadOGL.cpp
#	LoadOGLCore.cpp
#	TwEventGLFW.c
#	TwEventGLUT.c
#	TwEventSDL.c
#	TwEventSDL12.c
#	TwEventSDL13.c
#	TwEventSFML.cpp
#	TwEventX11.c''')

# linux only files
tbar_src = Split('''
	TwColors.cpp
	TwFonts.cpp
	TwOpenGL.cpp
	TwOpenGLCore.cpp
	TwBar.cpp
	TwMgr.cpp
	TwPrecomp.cpp
	LoadOGL.cpp
	LoadOGLCore.cpp
	TwEventGLUT.c
	TwEventSDL.c
	TwEventSDL12.c
	TwEventSDL13.c
	TwEventSFML.cpp
	TwEventX11.c''')

tbar_env.Append(
	CPPPATH = ['include'],
	CPPFLAGS = ['-fPIC', '-fno-strict-aliasing', ],
	CPPDEFINES=['_UNIX', '__PLACEMENT_NEW_LINE'],
	LIBPATH = '.',
)

tbar_full_src = ['src/'+s for s in tbar_src]

static_tbar = tbar_env.StaticLibrary('anttweakbar', tbar_full_src)
shared_tbar = tbar_env.SharedLibrary('anttweakbar', tbar_full_src)

tbar_target = '/usr/local/lib'
tbar_env.Install(tbar_target, shared_tbar)
tbar_env.Alias('install', tbar_target)

# examples
tbar_env.Append(LIBS=['m', 'glut'])
tbar_env.Program(['examples/TwSimpleGLUT.c', static_tbar])
tbar_env.Program(['examples/TwDualGLUT.c', static_tbar])
tbar_env.Program(['examples/TwSimpleSDL.c', static_tbar])
#tbar_env.Program(['examples/TwSimpleGLFW.c', static_tbar])
#tbar_env.Program(['examples/TwAdvanced1.cpp', static_tbar])
tbar_env.Program(['examples/TwString.cpp', static_tbar])
#tbar_env.Program(['examples/TwSimpleSFML.cpp', static_tbar])  # nejede
#tbar_env.Program(['examples/TwGLCoreSDL.c', static_tbar])  # nejede

