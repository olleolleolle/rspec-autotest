source "https://rubygems.org"

gemspec

%w[rspec rspec-core rspec-expectations rspec-mocks rspec-support].each do |lib|
  branch = ENV.fetch('RSPEC_BRANCH', 'master')
  next if branch == '2-99-maintenance' && lib == 'rspec-support'

  library_path = File.expand_path("../../#{lib}", __FILE__)
  if File.exist?(library_path) && !ENV['USE_GIT_REPOS']
    gem lib, :path => library_path
  else
    gem lib, :git => "https://github.com/rspec/#{lib}.git", :branch => branch
  end
end

### deps for rdoc.info
platforms :ruby do
  gem 'yard',          '0.8.6.1', :require => false
  gem 'redcarpet',     '2.1.1'
  gem 'github-markup', '0.7.2'
end

if RUBY_VERSION.to_s < '1.9.3'
  gem 'i18n', '~> 0.6.0'
end

eval File.read('Gemfile-custom') if File.exist?('Gemfile-custom')
