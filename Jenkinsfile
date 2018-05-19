node {
    stage ('scm checkout') {
    checkout([$class: 'GitSCM',
    branches: [[name: '*/master']],
    doGenerateSubmoduleConfigurations: false,
    extensions: [], submoduleCfg: [],
    userRemoteConfigs: [[url: 'https://github.com/Kiranp295/Devops.git']]])
    } 

    stage ('Appbuild') { 
    sh 'mvn -f pom.xml clean package'
    }
    
    stage ('deployment') {
    sh '''cp target/*.war /opt/tomcat/webapps/
    sh /opt/tomcat/bin/shutdown.sh
    sh /opt/tomcat/bin/startup.sh'''
    }
    stage ('archive Artifacts') {
    archiveArtifacts 'target/*.war'
    }
}
