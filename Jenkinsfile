pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }
    
     }

     //Stage 3 deploy to Nexus

       // Stage3 : Publish the artifacts to Nexus
        stage ('Publish to Nexus'){
            steps {
                script {

                def NexusRepo = Version.endsWith("SNAPSHOT") ? "DamonsDevOpsLab-SNAPSHOT" : "DamonsDevOpsLab-RELEASE"

                nexusArtifactUploader artifacts: [[artifactId: 'DamonsDevOpsLab', classifier: '', file: 'target/DamonsDevOpsLab-0.0.5-SNAPSHOT.war', type: 'war']], credentialsId: '4c81d5eb-dd74-43b7-8c18-c1582b5a25ac', groupId: 'com.damonsdevopslab', nexusUrl: '172.30.10.245:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'NexusMaven-SNAPSHOT', version: '0.0.5-SNAPSHOT'
             }
            }
        }

} 
