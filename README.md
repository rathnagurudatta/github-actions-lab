# github-actions-lab
AWS - INFRA

```text
Developer (You)
   |
   | git push
   v
GitHub Repository
   |
   v
GitHub Actions Runner
   |
   | assumes IAM role
   v
AWS CloudFormation
   |
   v
Creates / Updates S3 Bucket (Prod)

*****************************************

Create  cloudformation/s3.yaml
Create  environments/prod.json
Create IAM Role (One time) - GitHubActionsCloudFormationRole [IAM → Roles → GitHubActionsCloudFormationRole → Trust relationships]
Create Github Actions workflow - .github/workflows/deploy-s3.yml


AWS:
Create Trust-policy s3-deploy-policy.yaml (Ensure only my repo can deploy)
Create IAM Permission policy (Attach to role)

IAM Role
├── Trust Policy   (WHO can assume the role - ex: GitHub Actions (OIDC))
|         [AWS Location: IAM → Roles → GitHubActionsCloudFormationRole → Trust relationships]
└── Permissions    (WHAT can the role do & can be inline policy or managed policy)
        [AWS Location: IAM → Roles → GitHubActionsCloudFormationRole → Permissions
        AWS Location: IAM → Policies → Managed Policies]

Github marketplace : https://github.com/marketplace?type=actions



