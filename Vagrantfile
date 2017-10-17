Vagrant.configure("2") do |config|
  config.vm.box = 'ubuntu/trusty64'

  # Setup Python 2.7.13
  config.vm.provision "shell", :inline => <<-SHELL
    # apt-add-repository depends on this
    apt-get install -y python-software-properties
    # get common python build tools:
    # https://github.com/pyenv/pyenv/wiki/Common-build-problems
    apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
    libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
    xz-utils tk-dev
    # install python v2.7.13
    wget https://www.python.org/ftp/python/2.7.13/Python-2.7.13.tgz
    tar xzf Python-2.7.13.tgz
    cd Python-2.7.13
    ./configure
    make install
  SHELL

  # Setup Node 6.11.4
  config.vm.provision "shell", :inline => <<-SHELL
    # install 6.x version of node for the system (instead of v0.6.x)
    # https://nodesource.com/blog/installing-node-js-tutorial-ubuntu/
    curl -sL https://deb.nodesource.com/setup_6.x | bash -
    apt-get update
    apt-get install -y nodejs

    # update npm with newer version of node
    npm install npm --global
  SHELL

end
