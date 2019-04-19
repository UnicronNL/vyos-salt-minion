pipeline {
  agent {
    node {
      label 'jessie-amd64'
    }

  }
  stages {
    stage('build-package') {
      steps {
        sh '''#!/bin/bash
rm -f ../*.deb
sudo mk-build-deps -i -r -t \'apt-get --no-install-recommends -yq\' debian/control

dpkg-buildpackage -b -us -uc -tc
'''
      }
    }
    stage('Deploy package') {
      steps {
        sh '''#!/bin/bash
/var/lib/vyos-build/pkg-build.sh'''
      }
    }
  }
}