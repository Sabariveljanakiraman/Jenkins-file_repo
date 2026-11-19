# InvoiceBill Jenkins pipelines

Five separate pipeline scripts: master, v1, v2, v3 and v4.

## Jenkins job configuration
Pipeline script from SCM:
- SCM: Git
- Repository URL: https://github.com/Sabariveljanakiraman/Jenkins-file_repo.git
- Branch specifier: */main
- Credentials ID: github-credentials

Script Paths (files are at repository root):
- InvoiceBill-Master: Jenkinsfile-master
- InvoiceBill-V1: Jenkinsfile-v1
- InvoiceBill-V2: Jenkinsfile-v2
- InvoiceBill-V3: Jenkinsfile-v3
- InvoiceBill-V4: Jenkinsfile-v4

If files are inside an `invoice` folder, prefix each Script Path with `invoice/`.

Each pipeline checks out its matching branch from:
https://github.com/Meganartech/InvoiceBill.git

Required Jenkins tool names:
- JDK: JDK17
- Maven: Maven3
- NodeJS: NodeJS22

Required plugins: Pipeline, Git, NodeJS, Email Extension.
The credential ID `github-credentials` must have read access to both private repositories.

Each branch deploys into its own folder under D:\DevOps-Testing-Buildfiles so parallel builds do not overwrite one another.
The cron expression requests 12:00 PM Asia/Kolkata daily. Confirm your Jenkins version supports the TZ cron directive; alternatively set the Jenkins controller timezone to Asia/Kolkata and use `0 12 * * *`.
