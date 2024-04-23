pipeline{
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage("test"){
            steps{
                // mvn test
                sh "mvn test"
                echo "========always========"
            }
        }
        stage("Build"){
                steps{
                    // mvn package
                    echo "========always========"
            }
        }
        stage("Deploy on test"){
                steps{
                    // deploy on container -> piugin
                    echo "========always========"
            }
        }
        stage("ADeploy on prod"){
                steps{
                    // deploy on container -> plugin
                    echo "========always========"
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