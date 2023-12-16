node {
  checkout scm
  env.PATH = "${tool 'maven-3.6.3'}/bin:${env.PATH}"
  stage('Package') {
    dir('.') {
      sh 'mvn clean package -DskipTests'
    }
  }

  stage('Run Tests') {
    try {
      dir('.') {
       sh "mvn test"
      }
    } catch (error) {

    } finally {
      junit '**/target/surefire-reports/*.xml'
    }
  }
}
