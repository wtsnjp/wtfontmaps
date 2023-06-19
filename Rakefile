# Rakefile for wtsnjp/wtfontmaps
require 'rake/clean'
require 'pathname'

# basics
PKG_NAME = "wtfontmaps"

# directories
REPO_ROOT = Pathname.pwd
BUILD_DIR = REPO_ROOT + "build"
SAMPLE_DIR = REPO_ROOT + "sample"

TEXMFLOCAL = Pathname(`kpsewhich --var-value TEXMFLOCAL`.chomp)
WTFONTMAMPS_DIR = TEXMFLOCAL + "fonts/map/dvipdfmx" + PKG_NAME

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
task :install do
  # cleanup old stuff and recreate the empty dir
  rm_rf WTFONTMAMPS_DIR
  mkdir_p WTFONTMAMPS_DIR

  # copy all map files
  Dir.glob(REPO_ROOT + "*.map").each {|m| cp m, WTFONTMAMPS_DIR}

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
    "reimin-shingo-pr6"
  ]
  llmk_config_template = <<~TOML
    %% +++
    %% latex = "%s"
    %%
    %% [programs.dvipdf]
    %% opts = ["-f %s"]
    %% +++
  TOML
  sample_tex = File.read(SAMPLE_DIR + "sample.tex")

  # preparation
  rm_rf BUILD_DIR
  mkdir_p BUILD_DIR

  # build the samples
  cd BUILD_DIR
  families.each do |f|
    sample_fn = "sample-#{f}.tex"
    fontmap_fn = REPO_ROOT + "uptex-#{f}.map"
    content = llmk_config_template % ["uplatex", fontmap_fn] + sample_tex

    puts "Writing #{sample_fn}"
    File.write(sample_fn, content)

    sh "llmk #{sample_fn}"
  end

  # finale
  cp Dir.glob("*.pdf"), SAMPLE_DIR
end
