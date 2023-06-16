pipeline{
    agent any
    tools {
        mavan 'Mavan'
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh 'mvn test'
                echo "========executing A========"
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh 'mvn package'
                echo "========executing A========"
            }
        }
        stage("Deploy on Test"){
            steps{
                // Deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'jenkinsnodedetails', path: '', url: 'http://192.168.0.103:8080/app')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
        stage("Deploy on Prod"){
            steps{
                // Deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'jenkinsnodedetails', path: '', url: 'http://192.168.0.102:8080/app')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
