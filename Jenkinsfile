//@Library('piper-library-os') _  --> will be set by the testing framework

node() {
    stage('INIT') {
        echo "HALLO MARCUS"
        def scmInfo = checkout scm
        setupCommonPipelineEnvironment script: this
        echo "SCM_INFO: ${scmInfo}"
        echo "GIT_COMMIT: ${scmInfo.GIT_COMMIT}"
        commonPipelineEnvironment.setGitCommitId(scmInfo.GIT_COMMIT)
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
