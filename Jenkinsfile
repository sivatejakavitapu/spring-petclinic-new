pipeline
{
    agent {label 'NODE_2'}
    stages
    {
        stage ('download'){
            steps
            {
                git branch: 'main', url: 'https://github.com/sivatejakavitapu/spring-petclinic-new.git'
            }
           }
        stage ('Artifactory configuration')
        {
            steps {
                
                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "JFROG_1",
                    releaseRepo: 'libs-release',
                    snapshotRepo: 'libs-snapshot'
                )
            }
        }
          stage('Build the Code') {
            steps {
               sh 'mvn package'
                }
            }
            
            stage ('Exec Maven') {
              steps {
                rtMavenRun (
                    tool: 'maven', // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'package',
                    deployerId: "MAVEN_DEPLOYER"
                )
               }
            }
            stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "JFROG_1"
                )
              }
           }
            
            
            
            
        }
    
            

        
       
        
    }
    

    

