pipeline{
    agent{
        label "ansible"
    }
        stages{
        
        stage(" Git Checkout"){
            
            steps{
                git branch: 'main', url: 'https://github.com/viswar4/demo-counter-app.git'
            }
            
            }

        stage(" Maven Build"){
            
            steps{
                sh 'mvn clean install'
            }
            
            }

        stage("Build Docker File"){

                steps 
                {
                  script{
                    sh "docker image build -t ${JOB_NAME}:v1.$BUILD_ID ."
                    sh "docker image tag ${JOB_NAME}:v1.$BUILD_ID viswar4/${JOB_NAME}:v1.$BUILD_ID"
                    sh "docker image tag ${JOB_NAME}:v1.$BUILD_ID viswar4/$JOB_NAME:latest"
                }
            }        
            }
        
        stage("Ansible playbook")
            steps{
                sh "ansiblePlaybook becomeUser: null, disableHostKeyChecking: true, extras: 'BUILD_NUMBER=${BUILD_NUMBER}', inventory: '/home/ec2-user/hosts', playbook: '/home/ec2-user/playbook.yaml"
            }
}
}
