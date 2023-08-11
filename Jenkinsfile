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
}
}
