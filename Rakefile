# Rakefile for wtsnjp/wtfontmaps
require 'rake/clean'
require 'pathname'

# basics
PKG_NAME = "wtfontmaps"

# directories
REPO_ROOT = Pathname.pwd
TMP_DIR = REPO_ROOT + "tmp"
BUILD_DIR = TMP_DIR + "build"

TEXMFLOCAL = Pathname(`kpsewhich --var-value TEXMFLOCAL`.chomp)
WTFONTMAMPS_DIR = TEXMFLOCAL + "fonts/map/dvipdfmx" + PKG_NAME

# cleaning
CLEAN.include([])
CLOBBER.include([])

def ensure_root
  if `whoami`.chomp != 'root'
    fail "This task have to be executed as root."
  end
end

desc "Uninstall the fontmaps from TEXMFLOCAL"
task :uninstall do
  ensure_root

  # remove the direcotry
  rm_rf WTFONTMAMPS_DIR

  # update the ls-R database
  sh "mktexlsr"
end

desc "Install the fontmaps to TEXMFLOCAL"
task :install do
  ensure_root

  # cleanup old stuff and recreate the empty dir
  rm_rf WTFONTMAMPS_DIR
  mkdir_p WTFONTMAMPS_DIR

  # copy all map files
  Dir.glob(REPO_ROOT + "*.map").each {|m| cp m, WTFONTMAMPS_DIR}

  # update the ls-R database
  sh "mktexlsr"
end
