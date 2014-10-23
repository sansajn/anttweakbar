# anttweakbar build script
# 
# $ scons
# $ sudo scons install
# $ sudo ldconfig
#

AddOption('--debug-build',	action='store_true',	dest='debug_build',
	help='debug build', default=False)

env = Environment()
env.ParseConfig('pkg-config --cflags --libs gl glu x11 sdl libglfw')

if GetOption('debug_build'):
	env.Append(CCFLAGS=['-g', '-O0'])
else:
	env.Append(CCFLAGS=['-Os'])

# linux only
atb_src = Split('''
	TwColors.cpp 
	TwFonts.cpp 
	TwOpenGL.cpp 
	TwOpenGLCore.cpp 
	TwBar.cpp 
	TwMgr.cpp 
	TwPrecomp.cpp 
	LoadOGL.cpp 
	LoadOGLCore.cpp 
	TwEventGLFW.c 
	TwEventGLUT.c 
	TwEventSDL.c 
	TwEventSDL12.c 
	TwEventSDL13.c 
	TwEventSFML.cpp 
	TwEventX11.c''')

env.Append(
	CPPPATH = ['include'],
	CPPFLAGS = ['-fPIC', '-fno-strict-aliasing', '-D_UNIX',
		'-D__PLACEMENT_NEW_LINE'],
	LIBPATH = '.',
)

atb_lib = env.SharedLibrary('anttweakbar', ['src/'+s for s in atb_src])

atb_target = '/usr/local/lib'
env.Install(atb_target, atb_lib)
env.Alias('install', atb_target)

# examples
env.Append(LIBS=['m', 'glut'])
env.Program(['examples/TwSimpleGLUT.c', atb_lib])
env.Program(['examples/TwDualGLUT.c', atb_lib])
env.Program(['examples/TwSimpleSDL.c', atb_lib])
env.Program(['examples/TwSimpleGLFW.c', atb_lib])
env.Program(['examples/TwAdvanced1.cpp', atb_lib])
env.Program(['examples/TwString.cpp', atb_lib])
#env.Program(['examples/TwSimpleSFML.cpp', atb_objs])  # nejede
#env.Program(['examples/TwGLCoreSDL.c', atb_objs])  # nejede

