pipeline {
    agent any

    environment {
        SONAR_HOST_URL    = "http://172.31.35.75:9000"
        SONAR_PROJECT_KEY = "flask-app"
    }

    stages {
        stage('SonarQube Scan') {
            steps {
                withCredentials([string(credentialsId: 'sonarqube-token-id', variable: 'SONAR_TOKEN')]) {
                    sh """
                        docker run --rm \
                        -e SONAR_HOST_URL="${SONAR_HOST_URL}" \
                        -e SONAR_TOKEN="${SONAR_TOKEN}" \
                        -v "${WORKSPACE}:/usr/src" \
                        sonarsource/sonar-scanner-cli \
                        -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                        -Dsonar.sources=. \
                        -Dsonar.exclusions="**/venv/**,**/tests/**,**/*.log,docker-compose.yml"
                    """
                }
            }
        }

        stage('Quality Gate Input') {
            steps {
                input message: "Did the SonarQube quality gate pass? Verify at: ${SONAR_HOST_URL}", ok: "Proceed"
            }
        }
    }
}

/*

parameters{ booleanParam(
    name: 'USE_SLIM_IMAGE'
    default: false
    description: ""
    )}

environemnt{
    dockerhub = credentials('dockerhub')
    image_tag = "${BUILD_NUMBER}"
    original_image = "flask-app:${BUILD_NUMBER}-original"
    slim_image = "flask-app:${BUILD_NUMBER}-slim"
    nginx_image = "mynginx:${BUILD_NUMBER}"
    dockerhub_repo = chrisreeves1/flask-app
    sonar_host_url = "http://172.31.35.75:9000"
    SONAR_PROJECT_KEY = "flask-app"
}

fs scan
 - trivy 

clean up/prep
- remove containers + networks

unit test

sonarqube Scan (gated):


build original images

build slim image:
    when { expression { return params.USE_SLIM_IMAGE } }

select slim/original:
    script:
        if..param.USE_SLIM_IMAGE
            then..
        else ..

collect metaData:
    inspect
    image ls
    history 
        post always archive

image_size_gate
    200 + == unstable()

image security scan

generate SBOM

quality gate

run containers (if needed)

smoke test
    if fail print all logs

login tag and push to dockerhub
    example:
    env {DOCKERHUB_CREDENTIALS = credentials('dockerhub_creds')}

    echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u "$DOCKERHUB_CREDENTIALS_USR" --password-stdin

pipeline post actions:
    echo? 



*/