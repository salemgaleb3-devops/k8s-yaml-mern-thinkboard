pipeline {
    agent any

    parameters {
        string(name: 'DOCKERTAG', description: 'Docker image tag (e.g. BUILD_NUMBER)')
    }

    environment {
        GIT_REPO   = "https://github.com/salemgaleb3-devops/k8s-yaml-mern-thinkboard.git"
        GIT_BRANCH = "main"
        GIT_CREDS  = "github-creds"
    }

    stages {

        stage('Validate Parameters') {
            steps {
                script {
                    if (!params.DOCKERTAG?.trim()) {
                        error "DOCKERTAG is required and cannot be empty ❌"
                    }
                }
            }
        }

        stage('Clone Manifest Repository') {
            steps {
                git branch: "${GIT_BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Update Deployments Manifest') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: "${GIT_CREDS}",
                        usernameVariable: 'GIT_USERNAME',
                        passwordVariable: 'GIT_PASSWORD'
                    )
                ]) {
                    sh """
                        set -e
                        git config user.email "jenkins@local"
                        git config user.name "jenkins"

                        echo "backend image Before update"
                        grep image 03-backend-deployment.yaml

                        sed -i 's|\\(image: salemghaleb/mern-backend:\\).*|\\1${params.DOCKERTAG}|' 03-backend-deployment.yaml

                        echo "After update:"
                        grep image 03-backend-deployment.yaml

                        echo "frontend image Before update"
                        grep image 04-frontend-deployment.yaml

                        sed -i 's|\\(image: salemghaleb/mern-frontend:\\).*|\\1${params.DOCKERTAG}|' 04-frontend-deployment.yaml

                        echo "After update:"
                        grep image 04-frontend-deployment.yaml


                        git add .
                        git commit -m "Update image tag to ${params.DOCKERTAG}"
                        git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/salemgaleb3-devops/k8s-yaml-mern-thinkboard.git HEAD:${GIT_BRANCH}
                    """
                }
            }
        }
    }
}

