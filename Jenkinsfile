pipeline 
{
  agent { label 'Deploy_Server'}
  
  environment 
  {
    DOCKERHUB_CREDENTIALS = credentials('DockerHub')
  }
  stages 
  {
    stage('Build') 
    {
      steps 
      {
        dir('/var/lib/docker/volumes/tomcat/_data/')
        {
          sh 'docker build -t sumitsscet/simple-webapp:latest .'
        }
      }
    }
    stage('Login') 
    {
      steps 
      {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') 
    {
      steps 
      {
        sh 'docker push sumitsscet/simple-webapp:latest'
      }
    }
  }

}