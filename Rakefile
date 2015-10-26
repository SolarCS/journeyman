require 'rspec/core/rake_task'

$LOAD_PATH.unshift File.expand_path('../lib', __FILE__)
require 'journeyman/version'

name = 'journeyman'
version = Journeyman::VERSION

task :gem => :build
task :build do
  system "gem build #{name}.gemspec"
end

task :install => :build do
  system "sudo gem install #{name}-#{version}.gem"
end

task :release => :build do
  system "git tag -a v#{version} -m 'Tagging #{version}'"
  system 'git push --tags'
  system "gem push #{name}-#{version}.gem"
  system "rm #{name}-#{version}.gem"
end

RSpec::Core::RakeTask.new(:spec)
task :default => :spec
