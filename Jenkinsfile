pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'DÈpuis de l\'Èatpe build'
        bat 'mvnw -DskipTests clean install'
        echo 'Fin de build'
      }
    }

    stage('test') {
      parallel {
        stage('test int√©gration') {
          steps {
            echo 'test d\'int√©gration'
          }
        }

        stage('test fonctionnel') {
          steps {
            echo 'test fonctionnel'
          }
        }

        stage('smoke test') {
          steps {
            echo 'smoke test'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        echo 'stage deploy'
      }
    }

  }
  tools {
    maven 'maven 3.9'
    jdk 'java 11'
  }
}