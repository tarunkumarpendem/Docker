pipeline{
    agent{
        label 'node-2'
    }
    stages{
        stage(clone){
            steps{
                git url: 'https://github.com/tarunkumarpendem/Docker.git',
                    branch: 'main'
            }
        }
        stage(docker_stage){
            steps{
                sh 'docker info'
                sh 'docker image build -t jenkins:1.0 .'
                sh 'docker container rm -f $(docker container ls -a -q)'
                sh 'docker container run -d -P --name Jenkins jenkins:1.0'
                sh 'docker container ls -a'
                sh 'cat /var/jenkins_home/secrets/initialAdminPassword'
            }
        }
    }
}