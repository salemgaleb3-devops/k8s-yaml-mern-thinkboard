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

        stage('Clone Manifest Repository') {
            steps {
                git branch: "${GIT_BRANCH}",
                    url: "${GIT_REPO}"
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
                      git config user.email "jenkins@local"
                      git config user.name "jenkins"

                      echo "Before update:"
                      cat 03-backend-deployment.yaml

                      sed -i 's|image: salemghaleb/mern-backend:.*|image: salemghaleb/mern-backend:${DOCKERTAG}|' 03-backend-deployment.yaml

                      echo "After update:"
                      cat 03-backend-deployment.yaml

                      echo "Before update:"
                      cat 04-frontend-deployment.yaml

                      sed -i 's|image: salemghaleb/mern-frontend:.*|image: salemghaleb/mern-frontend:${DOCKERTAG}|' 04-frontend-deployment.yaml

                      echo "After update:"
                      cat 04-frontend-deployment.yaml


                      git add deployment.yaml
                      git commit -m "Update image tag to ${DOCKERTAG}" || echo "No changes to commit"
                      git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/salemgaleb3-devops/k8s-yaml-mern-thinkboard.git HEAD:${GIT_BRANCH}
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Manifest updated successfully 🎉"
        }
        failure {
            echo "Failed to update manifest ❌"
        }
    }
}


