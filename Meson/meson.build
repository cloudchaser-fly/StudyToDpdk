project('main', 'c')

my_add_lib = shared_library(
	'myadd',
	['math/add.c', 'math/add.h']
)
executable('main', 'main.c', link_with: my_add_lib)

