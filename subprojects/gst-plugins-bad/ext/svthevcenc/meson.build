svthevcenc_sources = [
  'gstsvthevcenc.c',
]

svthevcenc_headers = [
  'gstsvthevcenc.h',
]

doc_sources = []
foreach s: svthevcenc_sources + svthevcenc_headers
  doc_sources += meson.current_source_dir() / s
endforeach

plugin_sources += {
  'svthevcenc': pathsep.join(doc_sources)
}

svthevcenc_dep = dependency('SvtHevcEnc', version : '>= 1.4.1', required: get_option('svthevcenc'))

if svthevcenc_dep.found()
  gstsvthevcenc = library('gstsvthevcenc',
    svthevcenc_sources,
    c_args : gst_plugins_bad_args + ['-DGST_USE_UNSTABLE_API'],
    include_directories : [configinc],
    dependencies : [gstbase_dep, gstpbutils_dep, gstvideo_dep, gstcodecparsers_dep, svthevcenc_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
  plugins += [gstsvthevcenc]
endif
