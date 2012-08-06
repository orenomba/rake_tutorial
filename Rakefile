require 'rake/clean'

SOURCE_PATH = "./src"
OUTPUT_PATH = "./output"
directory OUTPUT_PATH

SOURCES = FileList[File.join SOURCE_PATH, "*.c"]
OBJECTS = SOURCES.ext(".o")

CLEAN.include(FileList[File.join SOURCE_PATH, "*.o"])
CLEAN.include(FileList[File.join OUTPUT_PATH, "*"])
CLOBBER.include(OUTPUT_PATH)


rule '.o' => '.c' do |t|
  sh "gcc -c #{t.source} -o #{t.name}"
end

task default: [OUTPUT_PATH, :main]

file main: OBJECTS do |t|
  sh "gcc -o #{File.join(OUTPUT_PATH, t.name)} #{t.prerequisites.join(" ")}"
end