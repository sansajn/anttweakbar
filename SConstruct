# anttweakbar build script

env = Environment()

src_list = Split('''
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


anttweakbar_objs = env.Object(['src/' + s for s in src_list])

env.Library('libanttweakbar.a', anttweakbar_objs)

