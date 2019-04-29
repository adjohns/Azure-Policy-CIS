# Deny creation of custom subscription owner roles

### Description: 
Subscription ownership should not include permission to create custom owner roles. The principle of least privilege should be followed and only necessary privileges should be assigned instead of allowing full administrative access. 
### Rationale: 
Classic subscription admin roles offer basic access management and include Account Administrator, Service Administrator, and Co-Administrators. It is recommended the least necessary permissions be given initially. Permissions can be added as needed by the account holder. This ensures the account holder cannot perform actions which were not intended. 

## Try on Portal

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmrajess%2FAzure-Policy-CIS%2Fmaster%2Fpolicies%2F1_identity_and_access-management%2F1.23%2FDeny%2Fazurepolicy.json)

## Try with PowerShell

````powershell
$definition = New-AzPolicyDefinition -Name "CIS-1.23" -DisplayName "Ensure that no custom subscription owner roles are created. CIS control 1.23." -description "Subscription ownership should not include permission to create custom owner roles. The principle of least privilege should be followed and only necessary privileges should be assigned instead of allowing full administrative access." -Policy 'https://raw.githubusercontent.com/mrajess/Azure-Policy-CIS/master/policies/1_identity_and_access-management/1.23/Deny/azurepolicy.rules.json' -Parameter 'https://raw.githubusercontent.com/mrajess/Azure-Policy-CIS/master/policies/1_identity_and_access-management/1.23/Deny/azurepolicy.parameters.json' -Mode All
$definition
$assignment = New-AzPolicyAssignment -Name <assignmentname> -Scope <scope> -PolicyDefinition $definition
$assignment 
````

## Try with CLI

````cli

az policy definition create --name 'CIS-1.23' --display-name 'Ensure that no custom subscription owner roles are created. CIS control 1.23.' --description 'Subscription ownership should not include permission to create custom owner roles. The principle of least privilege should be followed and only necessary privileges should be assigned instead of allowing full administrative access.' --rules 'https://raw.githubusercontent.com/mrajess/Azure-Policy-CIS/master/policies/1_identity_and_access-management/1.23/Deny/azurepolicy.rules.json' --params 'https://raw.githubusercontent.com/mrajess/Azure-Policy-CIS/master/policies/1_identity_and_access-management/1.23/Deny/azurepolicy.parameters.json' --mode All

az policy assignment create --name <assignmentname> --scope <scope> --policy 'CIS-1.23'

````