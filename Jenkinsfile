//@Library('piper-library-os') _  --> will be set by the testing framework

node() {
    stage('INIT') {
        echo "HALLO MARCUS"
        deleteDir()
        def scmInfo = checkout scm
        echo "SCM_INFO: ${scmInfo}"
        def sha = sh returnStdout: true,
                     script: "git rev-parse HEAD"
        setupCommonPipelineEnvironment script: this
        echo "GIT_COMMIT: ${sha}"
        commonPipelineEnvironment.setGitCommitId(sha)
        echo "CPE-GIT_COMMIT-1: ${commonPipelineEnvironment.gitCommitId}"
    }
    stage('TMS_UPLOAD') {
        echo "CPE-GIT_COMMIT-1: ${this.commonPipelineEnvironment.gitCommitId}"
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
