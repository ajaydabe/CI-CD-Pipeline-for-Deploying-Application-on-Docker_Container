pipeline{
    agent{
        label 'docker'
    }
    stages{
        stage("Cloning Git Repo"){
            steps{
                echo "Cloning Git Repository to Local"
                git url: 'https://github.com/ajaydabe/CI-CD-Pipeline-for-Deploying-Application-on-Docker_Container.git', branch: 'docker-compose'
            }
        }
        stage("Create Deployment Service"){
            steps{
                echo "Using Docker Stack, create Deployment Service"
                sh "docker stack deploy –c docker-compose.yml mydeployment"
            }
        }
    }
}
