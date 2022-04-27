pipeline {
agent any

  environment {
    TF_WORKSPACEN = "${params.servername}_WS" /// Sets the Terraform Workspace
    TF_IN_AUTOMATION = 'true'
    TF_LOG = 'TRACE'
    TF_LOG_PATH = '/tmp/TF.log'
    SERVER_NAME = "${params.servername}"
  }

  parameters {
        string(name: 'servername', defaultValue: '', description: 'Input the Virtual Machine Name.')
        string(name: 'path', defaultValue: '', description: "The path of the 'tfvars' file where the changes has been made.")
    }

  stages {
    stage('New-Check-Out') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Honishmiran/Azure-final.git']]])
            sh '''
            pwd
            ll
            '''
         }
    }
    // stage('Terraform Init') {
    //   steps {
    //             echo 'Initiating workspace creation!!'
    //     // sh '''
    //     // cd ${SERVER_NAME}_Dir
    //     // ls -lart
    //     // terraform init -input=true -reconfigure -backend-config "key=global/newec2/${SERVER_NAME}.tfstate"
    //     //         /usr/bin/terraform workspace new ${TF_WORKSPACEN} || true
    //     // /usr/bin/terraform workspace list
    //     // '''
    //             echo 'Workspace creation successful!!'
    //   }
    // }
    // stage('Terraform Plan') {
    //  when {
    //    expression { params.action == 'plan' } 
    //    }
    //   steps {
    //     sh '''
    //     cd ${SERVER_NAME}_Dir
    //     /usr/bin/terraform plan -input=false -out=tfplan --var-file ${SERVER_NAME}.tfvars
    //     /usr/bin/terraform show -no-color tfplan > tfplan.txt
    //     '''
    //   }
    // }
    //  stage('Approval') {
    //      when {
    //             not {
    //                 equals expected: true, actual: params.autoApprove
    //           }
    //         }
    //         steps {
    //             script {
    //                sh "cd ${SERVER_NAME}_Dir"
    //                 def plan = readFile "${SERVER_NAME}_Dir/tfplan.txt"
    //                 input message: "Do you want to apply the plan?",
    //                     parameters: [text(name: 'Plan', description: 'Please review the plan', defaultValue: plan)]
    //             }
    //         }
    //     }
    // stage('Terraform Apply') {
    //  when {
    //    expression { params.action == 'apply' } 
    //    }
    //   steps {
    //     input 'Apply Plan'
    //     sh '''
    //     cd ${SERVER_NAME}_Dir
    //     /usr/bin/terraform apply -input=false tfplan
    //     '''
    //   }
    // }
    // stage('Terraform Destroy') {
    //  when {
    //    expression { params.action == 'destroy' } 
    //    }
    //   steps {
    //     input 'Destroy Plan'
    //     sh '''
    //     cd ${SERVER_NAME}_Dir
    //     /usr/bin/terraform destroy -auto-approve --var-file ${SERVER_NAME}.tfvars
    //     '''
    //   }
    // }
////
  }
  //   post {
  //       always {
  //           archiveArtifacts artifacts: "${SERVER_NAME}_Dir/tfplan.txt"
  //       }
  // }
}
