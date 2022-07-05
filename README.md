# Cloud DevSecOps reusable actions repository
Welcome to the DevSecOps reusable actions repository containing sample reusable composite actions to help you get up and running quickly using M&S standards and best practices.

![Public repository attention](https://img.icons8.com/ios/32/000000/error--v1.png)
**Please note** this repository is **Public** and as such no sensitive data should be stored. 


## Reusable actions
The following reusable actions are available for a variety of tech stacks, please see the [Workflows folder](https://github.com/DigitalInnovation/cloud-devsecops-pipelineactions/tree/main/workflows).
- CI
  - Build
  - Artifact publishing 
  - Image publishing
  - Code Quality 
- AppSec
  - Dependency Vulnerability scanning
  - SAST (Static Application Security testing)
  - Container Vulnerability Scanning 
- Artifact and Image Publishing (If required separately from CI)
- Code Quality (If required separately from CI)
- Deployment 
  - AKS Helm Deployment
- Observability 
  - New Relic Deployment Marker
## Insights 
The insights workflow sends the pipeline run metrics to New Relic events db based on the New Relic Account ID and API Key provided as secrets.
  
  **How to Consume**
  
  1. Below is the sample reusable workflow trigger, which should be part of the 'main' branch of the repository. It gets triggered, everytime when there is a workflow run completion. By default the workflow trigger file will be part of the repositories which are created from Brightcloud. 
  If the repository is not created from Brightcloud, please follow the below step.
     
     - Copy the workflow file to the **_.github/workflows_** directory in _**main**_ branch.
     
     https://github.com/DigitalInnovation/Cloud-DevSecOps-Reusable-Templates/blob/main/.github/workflows/pipeline-insights-reusable-template.yaml
     
  2. Pipeline Metrics data is being sent to the below event tables in New Relic.
    * **pipelinemetricsdb** -> Contains the details about the workflow
    * **pipelinejobmetricsdb** -> Contains the details about the Jobs in each workflow
      
   - You an duplicate the below Demo Dashbaord to view the metrics.
    https://onenr.io/0bRK984bEQE

- Or you can use the below sample queries to view in New Relic Dashboard (Custom queries can be created based on the data) 
     - * _FROM pipelinemetricsdb SELECT latest(Repository_Name) as 'Repository Name' Facet Repo_ID SINCE 7 days ago_
     - * _FROM pipelinemetricsdb SELECT latest(Total_Duration) FACET Workflow_ID SINCE 7 days ago TIMESERIES 30 minutes LIMIT MAX_
     - * _FROM pipelinejobmetricsdb SELECT latest(Job_Duration) FACET Workflow_ID,Job_Name SINCE 7 days ago TIMESERIES 30 minutes  LIMIT MAX_ 

## Want to contribute?
We openly welcome contributors to enhance and grow our resuable actions to improve M&S engineering experience. Please feel free to raise a pull request against this repo with your suggestions / additions and one of the Cloud DevSecOps team will review. 

## Consumer Registry
Refer cloud-devsecops-pipelineactions [wiki](https://github.com/DigitalInnovation/cloud-devsecops-pipelineactions/wiki) page.
- [Product Teams repositort list](https://github.com/DigitalInnovation/cloud-devsecops-pipelineactions/wiki/Product_Team_Repository_List)

## Documentation
- [Semantic versioning](docs/semantic_versioning.md)

## Feedback or Support
Please contact the Cloud DevSecOps teams: itplatformscloudtechnologydevsecops@marks-and-spencer.com


   

