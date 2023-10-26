# commands to configure IAM OIDC provider 

```
export cluster_name=demo-cluster
```

```
oidc_id=$(aws eks describe-cluster --name $cluster_name --query "cluster.identity.oidc.issuer" --output text | cut -d '/' -f 5) 
```

## Check if there is an IAM OIDC provider configured already

- aws iam list-open-id-connect-providers | grep $oidc_id | cut -d "/" -f4\n 

If not, run the below command

```
eksctl utils associate-iam-oidc-provider --cluster $cluster_name --approve
```


FYI
IAM OIDC is a powerful tool for integrating AWS with your organization's identity and authentication systems, providing a seamless experience for users and simplifying identity management in AWS environments. It can be especially useful for organizations that already use OIDC IdPs for other applications and want to extend this authentication mechanism to AWS resources.
