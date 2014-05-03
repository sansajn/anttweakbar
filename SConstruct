# anttweakbar build script
env = Environment()

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
)

atb_lib = env.SharedLibrary('anttweakbar', ['src/'+s for s in atb_src])

atb_target = '/usr/local/lib'
env.Install(atb_targer, atb_lib)
env.Alias('install', atb_targer)

# examples

