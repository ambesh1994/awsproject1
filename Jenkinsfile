pipeline
{
  agent 
  {
    label 'awsnode'
  } 
   stages 
  {
    stage ("Install docker")
    {
      steps
      {
        sh '''
        yum install docker -y
        '''
      }  
    }
   
  
    stage ("build image")
    {
      steps
      {
        sh '''
        build -t aws -f aws.dockerfile .
        '''
      }  
    }
    stage ("run image")
    {
      steps
      {
        sh '''
        docker rm -f aws | exit 0
        docker run -d -p 80:80 --name aws aws
        '''
      }  
    }  
    
  }  
}
