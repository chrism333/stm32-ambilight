
# path to the xpcc root directory
rootpath = '../../xpcc'

env = Environment(tools = ['xpcc'], toolpath = [rootpath + '/scons/site_tools'])

# find all source files
files = env.FindFiles('.')

# build the program
program = env.Program(target = env['XPCC_CONFIG']['general']['name'], source = files.sources)

# build the xpcc library
env.XpccLibrary()

# create a file called 'defines.hpp' with all preprocessor defines if necessary
env.Defines()

env.Alias('size', env.Size(program))
env.Alias('symbols', env.Symbols(program))
env.Alias('defines', env.ShowDefines())

hexfile = env.Hex(program)

env.Alias('program', env.OpenOcd(program))
env.Alias('remote', env.OpenOcdRemote(hexfile))
env.Alias('build', [hexfile, env.Listing(program)])
env.Alias('all', ['build', 'size'])

env.Default('all')
