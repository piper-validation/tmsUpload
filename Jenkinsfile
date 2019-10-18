@Library('piper-lib-os@master') _

node() {
    stage('INIT') {
        setupCommonPipelineEnvironment script: this
    }
    stage('TMS_UPLOAD') {
        tmsUpload script: this,
                  mtaPath: 'dummy.mtar',
                  nodeName: '__piperIntegrationTest',
                  credentialsId: 'tmsUpload',
                  verbose: true
    }
    stage('VALIDATION') {
        sh '''#!/bin/bash
              curl --header \
                   --fail \
                   https://transport-service-app-backend.tshotfix.cfapps.eu10.hana.ondemand.com/nodes/1/transportRequests?status=in
           '''
    }
}
