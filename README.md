# AWS Programming and Tools Workshop (ArgoCD Workshop) 

## Instructions for workshop setup:

1. Sign into your AWS account 
2. Click https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/quickcreate?templateUrl=https://ws-assets-prod-iad-r-sin-694a125e41645312.s3.ap-southeast-1.amazonaws.com/39146514-f6d5-41cb-86ef-359f9d2f7265/eks-workshop-vscode-cfn.yaml&stackName=eks-workshop-ide&param_RepositoryRef=stable


3. Scroll to the bottom of the screen and click "I acknowledge that AWS CloudFormation might create IAM resources with customised names." Click "create stack" button.
<img width="1476" alt="image" src="https://github.com/user-attachments/assets/2c25e869-c33a-4083-95d1-aa3378bea145" />

4. Wait 5 minutes until the lab has been launched. The cloudformation status of the workshop (eks-workshop-ide) should be "CREATE_COMPLETE" once done.
<img width="1724" alt="image" src="https://github.com/user-attachments/assets/b69bcfe5-015d-408a-9992-d9aedde2c651" />



5. Click on the workshop name and select "Outputs" from the tab
<img width="1724" alt="image" src="https://github.com/user-attachments/assets/91321779-47ab-4753-9491-d3cf2ad3120f" />



6. Click the link next to "IdePasswordSecret"
<img width="1724" alt="image" src="https://github.com/user-attachments/assets/698c3de8-bb7f-450e-9d21-18bd018d431d" />



7. You will be taken to this secrets page. Click "Retrieve secret value"
<img width="1724" alt="image" src="https://github.com/user-attachments/assets/70aa1da6-f38a-42fc-bfd5-c16c9b232458" />



8. Copy the value for the password secret. Paste it in a notepad or word document as you will need it later.
<img width="1724" alt="image" src="https://github.com/user-attachments/assets/b3a1608c-4899-44b1-95a0-8bb040969942" />



9. Hit the back button to go back to the Outputs page you were on before. Once there, click the link next to "IdeUrl"
<img width="1724" alt="image" src="https://github.com/user-attachments/assets/a51e9aab-2fc6-4921-9028-beb766267608" />



10. You will be taken to the page below. Paste the password value you copied earlier (in step 9). Click the submit button.
    <img width="1724" alt="image" src="https://github.com/user-attachments/assets/32419e16-0d0d-408a-9caa-8882bdb1778b" />



11. Run the following code:

```
export EKS_CLUSTER_NAME=eks-workshop
curl -fsSL https://raw.githubusercontent.com/aws-samples/eks-workshop-v2/stable/cluster/eksctl/cluster.yaml | \
envsubst | eksctl create cluster -f -
```

<img width="1724" alt="image" src="https://github.com/user-attachments/assets/b1a4dd08-afd2-44d3-96a9-38a0f0b200e3" />

12. Wait 15 minutes for the workshop to finish setting up.
    
14. Once finished, run the following command:

```
prepare-environment automation/gitops/argocd
```

<img width="1402" alt="image" src="https://github.com/user-attachments/assets/f423c2b4-aea5-46d3-9c06-7b18750c6821" />


15: Access the workshop at:

https://www.eksworkshop.com/docs/automation/gitops/argocd/codecommit

## Instructions for workshop cleanup:

1. Run the following command in your environment to delete your cluster:

```
delete-environment
eksctl delete cluster $EKS_CLUSTER_NAME --wait
```

2. In your cloudshell run the following command to delete your stack:

```
aws cloudformation delete-stack --stack-name eks-workshop-ide
```

