withEnv([
  'AZURE_SUBSCRIPTION_ID=<your_subscription_id>',
  'AZURE_TENANT_ID=<your_tenant_id>'
]) {
  
  def resourceGroup = 'jenkins-get-started-rg'
  def webAppName   = '<yourappname>'

  withCredentials([usernamePassword(
    credentialsId: 'AzureServicePrincipal',
    usernameVariable: 'AZURE_CLIENT_ID',
    passwordVariable: 'AZURE_CLIENT_SECRET'
  )]) {

    sh """
      az webapp deploy \
        --resource-group ${resourceGroup} \
        --name ${webAppName} \
        --src-path target/calculator-1.0.war \
        --type war
    """
  }
}
