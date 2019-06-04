node {
   stage('init') {
      checkout scm
   }
   // mvn -version
   // mvn clean package
   stage('build') {
      sh '''
         cd complete
         cp src/main/resources/web.config web.config
         cp target/gs-spring-boot-0.1.0.jar app.jar 
         zip todo.zip app.jar web.config
      '''
   }
   stage('deploy') {
      azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
      resourceGroup: env.RES_GROUP, appName: env.WEB_APP, filePath: "**/todo.zip"
   }
}
