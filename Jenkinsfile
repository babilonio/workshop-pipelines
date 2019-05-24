#!groovy

pipeline {
    agent {
        docker {
            image 'adoptopenjdk/openjdk11:jdk-11.0.3_7'
            args '--network ci'
        }
    }

    environment {
        ORG_NAME = "babilonio"
        APP_NAME = "sboatella-pipelines"
        APP_CONTEXT_ROOT = "/"
        APP_LISTENING_PORT = "8080"
        TEST_CONTAINER_NAME = "ci-${APP_NAME}-${BUILD_NUMBER}"
        DOCKER_HUB = credentials("${ORG_NAME}-docker-hub")
    }
    agent {
        docker {
            image 'adoptopenjdk/openjdk11:jdk-11.0.3_7'
            args '--network ci --mount type=volume,source=ci-maven-home,target=/root/.m2'
        }
    }
}
