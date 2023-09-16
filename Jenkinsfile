pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment {
        SNAP_REPO= 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'Karanghale41o*'
        RELEASE_REPO = 'vprofile-release'
	    CENTRAL_REPO = 'maven-central'
        NEXUSIP = '172.31.93.77'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vprofile-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }
    stages {
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        
        stage ('Test'){
            steps {
                sh 'mvn test'
            }
            
        }

        stage ('Checkstyle Analysis'){
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }



        }
    }
}