pipeline{
    agent any
    tools {
        maven 'Maven'
    }

    stages{
        stage("Test"){
            steps{
                sh "mvn test"
                echo "========executing A========"
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========test executed successfully========"
                }
                failure{
                    echo "========test execution failed========"
                }
            }
        }
        stage("Build"){
            steps{
                sh "mvn package"
                echo "========executing Build========"
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========Build executed successfully========"
                }
                failure{
                    echo "========Build execution failed========"
                }
            }
        }
        stage("Deploy on Test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'test_serverdetails1', path: '', url: 'http://13.230.51.131:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing Deploy on test========"
            }
           
        }
        stage("Deploy on prod"){
            steps{
                echo "deployment"
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
