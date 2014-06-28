source 'https://rubygems.org'

gemspec

gem 'mocha', '~> 0.13.0', require: false
gem 'rack-cache', '~> 1.2'
gem 'jquery-rails', '~> 2.2.0'
gem 'turbolinks'

# require: false so bcrypt is loaded only when has_secure_password is used.
# This is to avoid ActiveModel (and by extension the entire framework)
# being dependent on a binary library.
gem 'bcrypt', '~> 3.1.7', require: false

# This needs to be with require false to avoid
# it being automatically loaded by sprockets
gem 'uglifier', '>= 1.3.0', require: false

group :doc do
  gem 'sdoc'
  gem 'redcarpet', '~> 2.2.2', platforms: :ruby
  gem 'w3c_validators'
  gem 'kindlerb'
end

# AS
gem 'dalli', '>= 2.2.1'

# Add your own local bundler stuff
local_gemfile = File.dirname(__FILE__) + "/.Gemfile"
instance_eval File.read local_gemfile if File.exist? local_gemfile

group :test do
  platforms :mri_19 do
    gem 'ruby-prof', '~> 0.11.2'
  end

  platforms :mri_19, :mri_20 do
    gem 'debugger'
  end

  gem 'benchmark-ips'
end

platforms :ruby do
  gem 'yajl-ruby'
  gem 'nokogiri', '>= 1.4.5'

  # Needed for compiling the ActionDispatch::Journey parser
  gem 'racc', '>=1.4.6', require: false

  # AR
  gem 'sqlite3', '~> 1.3.6'

  group :db do
    gem 'pg', '>= 0.11.0'
    gem 'mysql', '>= 2.9.0'
    gem 'mysql2', '>= 0.3.10'
  end
end

platforms :jruby do
  gem 'json'
  gem 'activerecord-jdbcsqlite3-adapter', '>= 1.3.0'

  group :db do
    gem 'activerecord-jdbcmysql-adapter', '>= 1.3.0'
    gem 'activerecord-jdbcpostgresql-adapter', '>= 1.3.0'
  end
end

# gems that are necessary for ActiveRecord tests with Oracle database
if ENV['ORACLE_ENHANCED']
  platforms :ruby do
    gem 'ruby-oci8', '>= 2.0.4'
  end
  gem 'activerecord-oracle_enhanced-adapter', github: 'rsim/oracle-enhanced', branch: 'master'
end

# A gem necessary for ActiveRecord tests with IBM DB
gem 'ibm_db' if ENV['IBM_DB']

gem 'goldiloader', path: '../goldiloader'
