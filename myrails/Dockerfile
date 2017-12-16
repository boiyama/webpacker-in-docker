FROM fedora

RUN dnf -y update && \
    dnf -y group install "C Development Tools and Libraries" && \
    curl --silent --location https://rpm.nodesource.com/setup_8.x | bash - && \
    curl --silent https://dl.yarnpkg.com/rpm/yarn.repo -o /etc/yum.repos.d/yarn.repo && \
    dnf -y install \
    redhat-rpm-config \
    wget \
    zlib-devel \
    sqlite-devel \
    mysql-devel \
    postgresql-devel \
    ruby-devel \
    ruby \
    rubygem-json \
    nodejs \
    yarn && \
    dnf clean all && \
    gem install bundler rails

WORKDIR /workdir
EXPOSE 3000
