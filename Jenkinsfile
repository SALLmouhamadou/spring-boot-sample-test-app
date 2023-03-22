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
            bat 'mvnw -Dtest=com.example.testingweb.functional.** test'
            echo 'fin de test funtional'
          }
        }

        stage('smoke test') {
          steps {
            echo 'debut smoke test'
            bat 'mvnw -Dtest=com.example.testingweb.functional.** test'
            echo 'fin test smoke'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        echo 'stage deploy'
        bat 'java -jar target/testing-web-complete.jar'
        echo 'fin stage deploy'
      }
    }

  }
  tools {
    maven 'maven 3.9'
    jdk 'java 11'
  }
}