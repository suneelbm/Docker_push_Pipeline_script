pipeline {
    agent { label "slave_ProjectA" }
    stages {
        stage('Gitclone') {
            steps {
                git 'https://github.com/VinCloud1/hello-world-master.git'
                echo 'cloning the project...'
                // commands to build the project
            }
        }
        stage('Build') {
            steps {
                sh 'yum install maven -y'
                sh 'mvn -Dmaven.test.failure.ignore=true install'
                echo 'Build the project...'
                // commands to run tests
            }
        }        
        stage('dockerstop') {
            steps {
                sh 'docker stop myweb1_container || true'
                echo 'dockerstop...'
                // commands to build the project
            }
        }
        stage('dockerremove') {
            steps {
                sh 'docker rm -f myweb1_container || true'
                echo 'dockerremove...'
                // commands to run tests
            }
        }
        stage('dockerimage') {
            steps {
                sh 'docker image  rm -f vnom1985/myweb1 || true'
                echo 'dockerimage creation...'
            }
        }
        stage('dockerbuild') {
            steps {
                sh 'docker build -t myweb1 .'
                echo 'dockerbuild...'
                // commands to monitor the production environment
            }
        }
        stage('dockertag') {
            steps {
                sh 'docker tag myweb1 vnom1985/myweb1'
                echo 'dockertag...'
                // commands to monitor the production environment
            }
        }
        stage('dockerlogin') {
            steps {
                sh 'docker login -u vnom1985 -p abc@12345'
                echo 'dockerlogin ...'
                // commands to monitor the production environment
            }
        }
        stage('dockerpush') {
            steps {
                sh 'docker push vnom1985/myweb1'
                echo 'dockerpush ...'
                // commands to monitor the production environment
            }
        }         
    }
}
