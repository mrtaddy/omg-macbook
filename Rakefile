namespace :xcode do
  task :lisence do
    sh 'which xcodebuild' do |ok, _status|
      break unless ok
      sh 'sudo xcodebuild -license'
    end
  end

  task :install do
    sh 'which xcode-select' do |ok, _status|
      break unless ok
      sh 'xcode-select --install'
    end
  end
end

namespace :brew do
  task :install do
    sh 'which brew' do |ok, _status|
      break if ok
      sh '/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"'
    end
  end

  task ansible: :install do
    sh 'which ansible' do |ok, _status|
      break if ok
      sh 'brew install ansible'
    end
  end
end

namespace :ansible do
  def roles
    require 'yaml'
    @roles ||= YAML.load_file('localhost.yml').first['roles'].map do |role|
      if role.instance_of?(Hash)
        role['role']
      else
        role
      end
    end
  end

  def installed_roles
    @installed_roles ||= YAML.load(`ansible-galaxy list -p roles`).map do |line|
      line.split(',').first
    end
  end

  task :galaxy do
    sh 'which ansible-galaxy' do |ok, _status|
      break unless ok
      (roles - installed_roles).each do |role|
        sh "ansible-galaxy install --roles-path=roles #{role}"
      end
    end
  end

  task playbook: :galaxy do
    sh 'which ansible-playbook' do |ok, _status|
      break unless ok
      sh 'ansible-playbook -i hosts -vv localhost.yml'
    end
  end
end

desc 'setup ansible'
task :setup => "brew:ansible"

desc 'ansible-playbook -i hosts -vv localhost.yml'
task :playbook => "ansible:playbook"
