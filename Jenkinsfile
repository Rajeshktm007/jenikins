pipeline
{
  agent any
 
  stages
  {
    stage('BUILD')
    {
      steps
      
      {
        sh 'docker build -t rajeshktm007/summa:latest .'
      }
    }
    stage('PUSH to DOCKERHUB')
    {
      steps
      {
        withCredentials([string(credentialsId: 'DOCKERHUBPASSWD', variable: 'DOCKERHUBPASSWD')]) {
        sh 'docker login -u rajeshktm007 -p ${DOCKERHUBPASSWD}'
        }
        
        sh 'docker push rajeshktm007/summa'
      }
    }
      stage('DEPLOYMENT')
      {
        steps{
          sh 'docker run -d -p 569:80 --name firstd rajeshktm007/summa'
        }
        
    }
  }
}
