# ppeffjenkins 

### Artifacts and Fingerprint
```
stage('Build'){
  steps{
    sh 'mvn clean package'
    junit '**/target/surfire-reports/TEST-*.xml'
    archiveArtifacts artifact 'target/*.jar', fingerprint:true
  }
}
```

### Deloying Our Java Web Project
```
stage('Deploy'){
  steps {
    input 'Do you want to start'
    sh 'scp target/*.jar jenkins@192.168.5.1:/opt/p/'
    sh 'ssh jenkins@192.168.5.1 "nohup java -jar /opt/p/spring-p-1.jar &"'
  }
}
```
