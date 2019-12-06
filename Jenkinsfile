pipeline {
    agent any
    
    environment {
        ARM_CLIENT_ID="56734769-eb5d-4ef2-9f3e-63be21d88528"
        ARM_CLIENT_SECRET=credentials('Terraform-Azure-Cient-Secret')
        ARM_SUBSCRIPTION_ID="98e03152-0027-41fa-a4af-1b6b1100e212"
        ARM_TENANT_ID="1c65a708-c899-485d-ad68-d53560fa74ba"
    }
    
    stages {
        stage ('terra-init'){
            steps {
                 bat "\"${getTerraformPath()}\\terraform\" init"               
            }
        }
        stage ('terra-plan') {
            steps {
                bat "\"${getTerraformPath()}\\terraform\" plan"
            }
        }  
        stage ('terra-apply') {
            steps {
                bat "\"${getTerraformPath()}\\terraform\" apply -auto-approve" 
            }
        } 
    }
}

def getTerraformPath () {
    def HomeDir = tool name: 'Terraform-12', type: 'org.jenkinsci.plugins.terraform.TerraformInstallation'
    return HomeDir
}
