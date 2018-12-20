# subdirs=[ "lanelet2", "lanelet2_core", "lanelet2_examples", "lanelet2_io", "lanelet2_maps", "lanelet2_projection", "lanelet2_python", "lanelet2_routing", "lanelet2_traffic_rules", "lanelet2_validation" ]

pkgs=["eigen3", "geographiclib"]

subdirs=[ "lanelet2_core", "lanelet2_examples",  "lanelet2_projection", "lanelet2_io", "lanelet2_traffic_rules", "lanelet2_routing", "lanelet2_validation", "lanelet2_maps", "deb" ]

env = Environment()

import os
from os.path import join

env.Append( CPPPATH=[join("#", subdir, "include") for subdir in subdirs] )
env.Append( LIBPATH=["#/scons_targets/lib/lanelet2/"] )

env.Append( LINKFLAGS="-Wl,--no-undefined -Wl,--no-allow-shlib-undefined -Wl,--copy-dt-needed-entries" )
env.Append( LINKFLAGS="-Wl,-rpath="+"'$$ORIGIN/../lib/lanelet2'")

for pkg in pkgs:
    env.ParseConfig( "pkg-config %s --cflags --libs" % pkg )

for subdir in subdirs:
    subdir_env = env.Clone()
    subdir_env.Append( CPPPATH=[join("#", subdir, "include", subdir)] )
    SConscript( join( subdir, "SConscript" ), exports=["subdir_env", "subdir"] )

