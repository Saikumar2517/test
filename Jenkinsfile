pipeline {
    agent any
    environment {
        DOCKER_REGISTRY = ' saidocker999/test'
    }
      tools {
        dockerTool 'docker'
    }


    stages {
        stage('Docker Build') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-password') {
                            def customImage = docker.build("saidocker999/test:${env.BUILD_ID}")

                            /* Push the container to the custom Registry */
                            customImage.push()
                    }
                }
            }
        }
        // stage('test'){
        //     steps{
        //         script{
        //             def scannerHome = tool 'sonar';
        //             withSonarQubeEnv(credentialsId: 'sonar-pass') {
        //                 sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=bmi" 

        //             }
        //         }
        //     }
        // }
        // stage('Deploy') {
        //     steps {
        //         script {
        //             sshPublisher(publishers: [sshPublisherDesc(configName: 'server-aws', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: "docker pull  saidocker999/bmi-react:${env.BUILD_ID} && docker container rm -f bmi-react && docker run --name bmi-react -p 3004:80 -d  saidocker999/bmi-react:${env.BUILD_ID}", execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        //         }
        //     }
        // }

    }
}
