//@Library('piper-library-os') _  --> will be set by the testing framework

node() {
    stage('INIT') {
        deleteDir()
        def scmInfo = checkout scm
        String sha = sh(returnStdout: true, script: "git rev-parse HEAD").trim()
        setupCommonPipelineEnvironment script: this
        echo "GIT_COMMIT: ${sha}"
        commonPipelineEnvironment.setGitCommitId(sha)
    }
    stage('TMS_UPLOAD') {
        tmsUpload script: this,
                  mtaPath: 'dummy.mtar',
                  nodeName: '__piperIntegrationTest',
                  credentialsId: 'tmsUpload',
                  verbose: true
    }
//    stage('VALIDATION') {
//        sh '''#!/bin/bash
//              curl --header \
//                   -vvv \
//                   --fail \
//                   https://transport-service-app-backend.tshotfix.cfapps.eu10.hana.ondemand.com/nodes/1/transportRequests?status=in
//           '''
//    }
}
