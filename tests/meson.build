test_headers = files([
	'gda-ddl-creator.h'
	])

inc_testsh = include_directories ('.')
inc_testsh_dep = declare_dependency (include_directories : inc_testsh)

tests_sources = files([
	'gda-ddl-creator.c',
	'test-cnc-utils.h',
	'test-cnc-utils.c',
	'data-model-errors.h',
	'data-model-errors.c'
	])

common_sources = files([
	'test-errors.h',
	'test-errors.c'
	])

tests_sources += test_headers
tests_sources += common_sources

tddlc = executable('test-ddl-creator test',
	['test-ddl-creator.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('DDLCreator', tddlc,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)


tbc = executable('test-bin-converter',
	['test-bin-converter.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('BinConverter', tbc,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tsqli = executable('test-sql-identifier',
	['test-sql-identifier.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('SqlIdentifier', tsqli,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tiq = executable('test-identifiers-quotes',
	['test-identifiers-quotes.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('IdentifiersQuotes', tiq,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tsqlb = executable('test-sql-builder',
	['test-sql-builder.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('SqlBuilder', tsqlb,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tcstrs = executable('test-connection-string-split',
	['test-connection-string-split.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('ConnectionStringSplit', tcstrs,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tipar = executable('test-input-parsers',
	['test-input-parsers.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('InputParsers', tipar,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tqkl = executable('test-quark-list',
	['test-quark-list.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('QuarkList', tqkl,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

tsqlr = executable('test-sql-renderer',
	['test-sql-renderer.c'] + tests_sources,
	c_args: [
		'-include',
		meson.build_root() + '/config.h',
		'-DCHECK_FILES="'+meson.source_root()+'"',
		'-DTOP_BUILD_DIR="'+meson.build_root()+'"'
		],
	link_with: libgda,
	dependencies: [
		libgda_dep,
		inc_rooth_dep,
		inc_sqliteh_dep
		],
	install: false
	)
test('SqlRenderer', tsqlr,
	env: [
		'GDA_TOP_SRC_DIR='+meson.source_root(),
		'GDA_TOP_BUILD_DIR='+meson.build_root()
		]
	)

subdir('data-models')
subdir('meta-store')
subdir('multi-threading')
subdir('parser')
subdir('providers')
subdir('value-holders')
if enable_ui
subdir('ui')
endif