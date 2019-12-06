pipeline {
    agent any
    
    environment {
        PATH = "${PATH}:${getTerraformPath()}"
    }
    
    stages {
        stage ('terra-init'){
            steps {
                withCredentials([azureServicePrincipal(credentialsId: 'Terraform-Azure',
                                    subscriptionIdVariable: 'SUBS_ID',
                                    clientIdVariable: 'CLIENT_ID',
                                    clientSecretVariable: 'CLIENT_SECRET',
                                    tenantIdVariable: 'TENANT_ID')]) {
                                         bat 'az login --service-principal -u %CLIENT_ID% -p %CLIENT_SECRET% -t %TENANT_ID%'
                }
                
                /*bat '''
                    az login --service-principal -u "56734769-eb5d-4ef2-9f3e-63be21d88528" -p "rYqBPiW8Fo:O/?dA.nciejC8JC8J51X4" -t "1c65a708-c899-485d-ad68-d53560fa74ba"
                    "C:\\Program Files\\Terraform\\terraform" init 
                    
                '''
                //bat "\"${getTerraformPath()}\\terraform\" init"
                bat "\"${getTerraformPath()}\\terraform\" plan"
                bat "\"${getTerraformPath()}\\terraform\" apply -auto-approve" */
            }
        }    
    }
}

def getTerraformPath () {
    def HomeDir = tool name: 'Terraform-12', type: 'org.jenkinsci.plugins.terraform.TerraformInstallation'
    return HomeDir
}
