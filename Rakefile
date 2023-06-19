# Rakefile for wtsnjp/wtfontmaps
require 'rake/clean'
require 'pathname'

# basics
PKG_NAME = "wtfontmaps"

# directories
BASE_DIR = Pathname.pwd
MAPS_DIR = BASE_DIR / "maps"
BUILD_DIR = BASE_DIR / "build"
SAMPLE_DIR = BASE_DIR / "sample"

TEXMFLOCAL = Pathname(`kpsewhich --var-value TEXMFLOCAL`.chomp)
WTFONTMAMPS_DIR = TEXMFLOCAL / "fonts/map/dvipdfmx" / PKG_NAME

# cleaning
CLEAN.include(["build"])
CLOBBER.include(["sample/*.pdf"])

desc "Uninstall the fontmaps from TEXMFLOCAL"
task :uninstall do
  # remove the direcotry
  rm_rf WTFONTMAMPS_DIR

  # update the ls-R database
  sh "mktexlsr"
end

desc "Install the fontmaps to TEXMFLOCAL"
task :install => :uninstall do
  # copy map files
  cp_r MAPS_DIR, WTFONTMAMPS_DIR

  # update the ls-R database
  sh "mktexlsr"
end

desc "Typeset all sample documents"
task :sample do
  # variables
  families = [
    "morisawa-pr6",
    "ryumin-shingo-pr6",
    "udreimin-udshingo-pr6",
    "reimin-shingo-pr6",
    "morisawa-pr6n",
    "ryumin-shingo-pr6n",
    "udreimin-udshingo-pr6n",
    "reimin-shingo-pr6n"
  ]
  tex_header = <<~HEAD
    %%#!texfot uplatex
    \\def\\fontMapName{%s}
    \\def\\jisOption{%s}
  HEAD
  sample_tex = File.read(SAMPLE_DIR / "sample.tex")

  # preparation
  rm_rf BUILD_DIR
  mkdir_p BUILD_DIR

  # build the samples
  cd BUILD_DIR
  families.each do |f|
    sample_fn = "sample-#{f}.tex"
    jis2004 = (f[-1] == "n") ? "true" : "false"
    content = tex_header % [f, jis2004] + sample_tex

    puts "Writing #{sample_fn}"
    File.write(sample_fn, content)

    sh "llmk -v #{sample_fn}"
  end

  # finale
  cp Dir.glob("*.pdf"), SAMPLE_DIR
end
