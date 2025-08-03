pipeline {
    agent any

    tools {
        // Install the Maven version configured as "maven" and add it to the path.
        maven 'maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Venkatesh-Veduri/onlinebookstore.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            // post {
            //     // If Maven was able to run the tests, even if some of the test
            //     // failed, record the test results and archive the jar file.
            //     success {
            //         junit '**/target/surefire-reports/TEST-*.xml'
            //         archiveArtifacts 'target/*.jar'
            //     }
            // }
        }
        stage('Build') {
            steps {
                sh 'mvn -v'
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the Code..........'
                sh 'mvn test'
            }
        }
        stage('Compile') {
            steps {
                echo 'Compiling the Project..........'
                sh 'mvn compile'
            }
        }
        stage('Package') {
            steps {
                echo 'Package the Project..........'
                sh 'mvn package'
            }
        }
        // stage('Deploy') {
        //     steps{
        //         echo "Deploying the Project.........."
        //         /* sh "cp /var/lib/jenkins/workspace/maven-pipeline-1/target/*.war /opt/tomcat/webapps/" */
        //         ansiblePlaybook credentialsId: 'edf29c56-6626-4ce1-a40e-4d6a98e6afea', disableHostKeyChecking: true, installation: 'ansible', inventory: 'dev.inv', playbook: 'play.yml', sudoUser: null
        //     }
        // }
    }
}
