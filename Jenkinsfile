pipeline {
  agent {
    docker {
      image 'lilinj2000/dev:centos7.gcc'
    }
  }

  environment {
    home_3rd = '/var/jenkins_home/dist_pkg/3rd/centos7'
    home_libs = '/var/jenkins_home/dist_pkg/libs/centos7'
    home_app = '/var/jenkins_home/dist_pkg/app/centos7'
  }

  stages {
    stage('build') {
      steps {
        sh '''
	./bootstrap.sh --prefix=${home_3rd}/boost
	./b2 cxxflags="-std=c++11"
	'''
      }
    }
    stage('install') {
      steps {
        sh './b2 install'
      }
    }
  }
	
post { 
   always { 
     cleanWs()
     }
  }
}
