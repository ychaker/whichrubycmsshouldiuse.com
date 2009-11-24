desc "deploy site to whichrubycmsshouldiuse.com"
task :deploy do
  require 'rubygems'
  require 'highline/import'
  require 'net/ssh'

  branch = "master"

  username = ask("Username:  ") { |q| q.echo = true }
  password = ask("Password:  ") { |q| q.echo = "*" }

  Net::SSH.start('74.50.57.225', username, :port => 22, :password => password) do |ssh|
    commands = <<EOF
cd /var/www/whichrubycmsshouldiuse.com
git pull origin #{branch}
rm -R _site/
jekyll --no-auto
EOF
    commands = commands.gsub(/\n/, "; ")
    ssh.exec commands
  end
end
