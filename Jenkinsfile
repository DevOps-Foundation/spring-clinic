node {
  
  env.SONAR_TOKEN = 'e262b3fc59321227af8535c03f2763c65401b652'
  
  stage('Clone'){
    println 'Se Clona el Repositorio en Espacio de Trbaajo'
    checkout scm
  }
  
  stage('Build'){
    checkout scm
    sh "chmod 777 gradlew"
     sh "./gradlew build"
  }
  
  stage('Test'){
  sh "./gradlew clean test"
  }
  
  stage('Code Review'){
    
    println 'Comienza proceso Sonar.-'
     sh "set +x; ./gradlew sonarqube -Dsonar.login=${SONAR_TOKEN} -Dsonar.branch.name=feature-ChristopherGarrido-interfaz"
  }
  
  stage('Build') { 
            steps { 
                script{
                 app = docker.build("underwater")
                }
            }
        }
}
