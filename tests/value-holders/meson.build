
value_holders_common_sources = files([
	'common.h',
	'common.c'
	])

tchkhdl = executable('check_holder',
	['check_holder.c']+value_holders_common_sources+common_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DROOT_DIR="'+meson.source_root()+'"',
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep,
		inc_testsh_dep
		],
	install: false
	)
test('ValueHolder', tchkhdl,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tchkset = executable('check_set',
	['check_set.c']+value_holders_common_sources+common_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DROOT_DIR="'+meson.source_root()+'"',
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep,
		inc_testsh_dep
		],
	install: false
	)
test('ValueHolderSet', tchkset,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tchkstm = executable('check_statement',
	['check_statement.c']+value_holders_common_sources+common_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DROOT_DIR="'+meson.source_root()+'"',
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep,
		inc_testsh_dep
		],
	install: false
	)
test('ValueHolderStatement', tchkstm,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)
