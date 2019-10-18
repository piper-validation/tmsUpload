@Library('piper-lib-os@master') _

node() {
    stage('INIT') {
        setupCommonPipelineEnvironment script: this
    }
    stage('TMS_UPLOAD') {
        echo "Hello TMS"
        sh 'cp $JENKINS_HOME/dummy.mtar dummy.mtar'
        tmsUpload script: this,
                  mtaPath: 'dummy.mtar',
                  nodeName: '__piperIntegrationTest',
                  credentialsId: 'tmsUpload',
                  verbose: true
    }
}
