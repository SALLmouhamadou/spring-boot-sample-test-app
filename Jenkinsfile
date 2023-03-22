pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Dépuis de l\'éatpe build'
        bat 'mvnw -DskipTests clean install'
        echo 'Fin de build'
      }
    }

    stage('test') {
      parallel {
        stage('test intÃ©gration') {
          steps {
            echo 'debut test integration'
            bat 'mvnw -Dtest=com.example.testingweb.integration.** test'
            echo 'fin test integration'
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