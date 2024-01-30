pipeline
 {
     agent any
     stages
      {
     stage('Continious Download')
      {
      steps
         {
          git 'https://github.com/intelliqittrainings/maven.git'
         }
       }  
        stage('Continious Build')
          {
            steps
            {
              sh 'mvn package'
             }
           }
           stage('Continious Deployment')
           {
               steps
             {
                 deploy adapters: [tomcat9(credentialsId: '9ef5a70e-062f-4dfe-9774-22fa3b65b0dc', path: '', url: 'http://172.31.34.184:8080')], contextPath: 'test1', war: '**/*.war'    
             }
           }
           stage('Continious Testing')
           {
               steps
               {
                 git 'https://github.com/intelliqittrainings/FunctionalTesting.git'  
                 sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
               }
           }
           stage('Continious Delivery')
           {
               steps
               {
                  deploy adapters: [tomcat9(credentialsId: '9ef5a70e-062f-4dfe-9774-22fa3b65b0dc', path: '', url: 'http://172.31.45.158:8080')], contextPath: 'prodapp1', war: '**/*.war' 
               }
           }
    }
}     
