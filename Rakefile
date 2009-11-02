require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "data_miner"
    gem.summary = %Q{Mine remote data into your ActiveRecord models.}
    gem.description = %Q{Mine remote data into your ActiveRecord models. You can also perform associations and convert units.}
    gem.email = "seamus@abshere.net"
    gem.homepage = "http://github.com/seamusabshere/data_miner"
    gem.authors = ["Seamus Abshere", "Andy Rossmeissl"]
    %w{ activerecord activesupport andand remote_table errata seamusabshere-conversions }.each { |name| gem.add_dependency name }
    gem.require_path = "lib"
    gem.files.include %w(lib/data_miner) unless gem.files.empty? # seems to fail once it's in the wild
    gem.rdoc_options << '--line-numbers' << '--inline-source'
    gem.rubyforge_project = "dataminer"
  end
  Jeweler::GemcutterTasks.new
  Jeweler::RubyforgeTasks.new do |rubyforge|
    rubyforge.doc_task = "rdoc"
  end
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/*_test.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/*_test.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end




task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION')
    version = File.read('VERSION')
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "data_miner #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
