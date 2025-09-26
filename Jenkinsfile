// Jenkins Pipeline Draft
pipeline{
    agent{
        label 'slave'
    }
    stages{
        stage("Cloning Git Repo"){
            steps{
                echo "Cloning Git Repository to Local"
                git url: 'https://github.com/ajaydabe/CI-CD-Pipeline-for-Deploying-Application-on-Docker_Container.git', branch: 'main'
            }
        }
        stage("Build Image & Run Container"){
            steps{
                echo "Build Docker Image using Dockerfile"
                sh 'docker build -t ajaydabe/helloworld'
                echo "Running Container using Image"
                sh 'docker run -itd -p 80:80 ajaydabe/helloworld'
		echo "Container is now running on the Port 80."
            }
        }
        stage("Push Image"){
            steps{
                echo "Push Docker Image to DockerHub"
                withCredentials([usernamePassword(credentialsId: 'DockerHub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                    sh 'docker login -u $(env.USERNAME) -p(env.PASSWORD)'
                    sh 'docker push ajaydabe/helloworld'
                }
            }
        }
    }
}
