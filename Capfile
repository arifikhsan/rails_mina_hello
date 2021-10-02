# Load DSL and set up stages
require "capistrano/setup"

# Include default deployment tasks
require "capistrano/deploy"

# Load the SCM plugin appropriate to your project:
#
# require "capistrano/scm/hg"
# install_plugin Capistrano::SCM::Hg
# or
# require "capistrano/scm/svn"
# install_plugin Capistrano::SCM::Svn
# or
require "capistrano/scm/git"
install_plugin Capistrano::SCM::Git

# Include tasks from other gems included in your Gemfile
#
# For documentation on these, see for example:
#
#   https://github.com/capistrano/rvm
#   https://github.com/capistrano/rbenv
#   https://github.com/capistrano/chruby
#   https://github.com/capistrano/bundler
#   https://github.com/capistrano/rails
#   https://github.com/capistrano/passenger
#
# require "capistrano/rvm"
# require "capistrano/rbenv"
# require "capistrano/chruby"
# require "capistrano/bundler"
# require "capistrano/rails/assets"
# require "capistrano/rails/migrations"
# require "capistrano/passenger"

require 'capistrano/nvm'
require 'capistrano/yarn'
require "capistrano/rbenv"
require "capistrano/rails"
require "capistrano/passenger"

set :rbenv_type, :user
set :rbenv_ruby, '3.0.2'
# set :rbenv_prefix, '/usr/bin/rbenv exec'
set :rbenv_prefix, -> { "RBENV_ROOT=#{fetch(:rbenv_path)} RBENV_VERSION=#{fetch(:rbenv_ruby)} #{fetch(:nvm_prefix)} /usr/bin/rbenv exec" }
                       # RBENV_ROOT=$HOME/.rbenv RBENV_VERSION=3.0.2 /tmp/rails_mina_hello/nvm-exec.sh $HOME/.rbenv/bin/rbenv exec

set :rbenv_map_bins, %w{rake gem bundle ruby rails}

set :nvm_type, :user # or :system, depends on your nvm setup
set :nvm_node, 'v16.9.1'
set :nvm_map_bins, %w{node npm yarn}

# set :yarn_target_path, '/home/udin/.nvm/versions/node/v16.9.1/bin'

# Load custom tasks from `lib/capistrano/tasks` if you have any defined
Dir.glob("lib/capistrano/tasks/*.rake").each { |r| import r }
