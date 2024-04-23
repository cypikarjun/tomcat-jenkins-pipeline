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
                slackSend channel: 'arjun', message: 'job started'
                echo "========always========"
            }
        }
        stage("Build"){
                steps{
                    // mvn package
                    sh "mvn package"
                    echo "========always========"
            }
        }
        stage("Deploy on test"){
                steps{
                    // deploy on container -> piugin
                    deploy adapters: [tomcat9(credentialsId: 'ram', path: '', url: 'http://20.121.64.144:8080')], contextPath: '/app', war: '**/*.war'
                    echo "========always========"
            }
        }
        stage("ADeploy on prod"){

                  input {
                        message "Should we continue?"
                        ok "Yes we Should"
                    }

                steps{
                    // deploy on container -> plugin
                    deploy adapters: [tomcat9(credentialsId: 'ram', path: '', url: 'http://20.121.65.139:8080')], contextPath: '/app', war: '**/*.war'
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
            slackSend channel: 'arjun', message: 'job success'
        }
        failure{
            echo "========pipeline execution failed========"
            slackSend channel: 'arjun', message: 'job failed'
        }
    }
}