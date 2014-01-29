source "https://rubygems.org"

def location_for(place, fake_version = nil)
  mdata = /^(git:[^#]*)#(.*)/.match(place)
  if mdata
    [fake_version, { :git => mdata[1], :branch => mdata[2], :require => false }].compact
  elsif mdata = /^file:\/\/(.*)/.match(place)
    ['>= 0', { :path => File.expand_path(mdata[1]), :require => false }]
  else
    [place, { :require => false }]
  end
end

group :development do
  gem 'watchr'
end

group :development, :test do
  gem 'rake'
  gem 'puppetmodule-stdlib', ">= 1.0.0", :path => File.expand_path("..", __FILE__)
  gem 'rspec', "~> 2.11.0", :require => false
  gem 'mocha', "~> 0.10.5", :require => false
  gem 'puppetlabs_spec_helper', :require => false
  gem 'rspec-puppet'
end

facterversion = ENV['GEM_FACTER_VERSION']
if facterversion
  gem 'facter', *location_for(facterversion)
else
  gem 'facter', :require => false
end

gem 'puppet', '~> 3.4.0'
gem 'puppet-lint'

# vim:ft=ruby
