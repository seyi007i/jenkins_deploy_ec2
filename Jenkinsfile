pipeline {
    agent any
    stages {
        stage('fetch code') {
            steps {
                script {
                    echo "Pull source code from Git"
                    git branch: 'jenkins', url: 'https://github.com/seyi007i/jenkins_deploy_ec2.git'
                }
            }
        }
        stage('deploy_to_ec2') {
            steps {
                script {
                    def cp_html = 'sudo apt update && sudo apt install apache2 -y'
                    /*'sudo cp -r /home/ubuntu/* /var/www/html/'  */
                    sshagent(['ubuntu']) {
                        sh "ssh -o StrictHostKeyChecking=no ubuntu@13.48.25.25 ${cp_html}"
                        sh "scp -o StrictHostKeyChecking=no -r 2137_barista_cafe/* ubuntu@13.48.25.25:/home/ubuntu/"
                    }
                }
            }
        }
    }
}