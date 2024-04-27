# Implementation of ArgoCD for Canary Deployment ASSIGNMENT

## Introduction
This documentation outlines the implementation of ArgoCD for a canary deployment strategy. It covers the steps I took ,challenges encountered during the process, how they were resolved, and includes additional information such as cleanup steps and screenshots for visual representation.

# Steps Taken to Complete the Assignment

## Step 1: Setting Up ArgoCD Server

1. Installed ArgoCD on Kubernetes cluster following official documentation.
2. Configured ArgoCD server and accessed the UI to manage applications.

## Step 2: Defining Application Deployment

1. Created deployment manifests for my-app using Kubernetes YAML files.
2. Defined the desired state of the application, including replicas, labels, and container specifications.

## Step 3: Canary Deployment Strategy

1. Implemented a canary deployment strategy using Argo Rollouts for my-app.
2. Specified canary steps in the rollout definition for gradual rollout and testing.
3. Monitored the canary release progress to ensure successful completion.

## Step 4: Updating Docker Image and Rollout Definition

1. Built and pushed a new Docker image for my-app with updated features (new2).
2. Updated the rollout definition (rollout.yaml) to use the new Docker image (cappybara12/assignment-ai-planet:new2).

## Step 5: Monitoring Deployment and Rollout

1. Used kubectl commands to monitor rollout progress and pod statuses.
2. Leveraged Argo Rollouts UI to visualize the deployment pipeline and canary steps.

## Step 6: Documentation and Clean-Up

1. Created comprehensive documentation detailing the assignment process, challenges faced, and solutions implemented.
2. Added relevant screenshots to the documentation for visual clarity.
3. Wrote a "Clean Up" section in README.md to provide instructions for removing all resources created during the assignment from the Kubernetes cluster.

---

## Relevant Screenshots

Include relevant screenshots in the documentation to enhance visual understanding and showcase the implementation process.

- **Screenshot 1:** ArgoCD UI showing the deployment pipeline for the my-app-rollout.
  ![Screenshot 2024-04-28 010924](https://github.com/gbaeke/demo-clu-flux/assets/122734275/a29bb8f7-d2d0-411c-b9b4-7afe281a9c72)
  - **Screenshot 2:** Issue I ran into when doing the canary.
![Screenshot 2024-04-27 194328](https://github.com/gbaeke/demo-clu-flux/assets/122734275/edcd4b33-eef2-488d-bbf5-22bd3b6b6b7a)

- **Screenshot 3:** Successful Canary Deployment being shown in the image below ,Implementing a Canary Release with Argo Rollouts.
The output shows that the rollout named my-app-rollout is in a Healthy state, and the canary deployment strategy has completed all 7 steps, with the final step SetWeight: 100 and ActualWeight: 100, indicating that the new version (cappybara12/assignment-ai-planet:new-tag2) is now receiving 100% of the traffic.
![Screenshot 2024-04-28 003653](https://github.com/gbaeke/demo-clu-flux/assets/122734275/9c308d24-ec9a-4bc2-9d0a-24995080526c)



- **Screenshot 4:** Terminal output of the `kubectl get pods` command displaying pod statuses.
- ![Screenshot 2024-04-27 192123](https://github.com/gbaeke/demo-clu-flux/assets/122734275/4aad9505-15ae-44c0-96fe-a1ab663160b7)
- **Screenshot 5:** ArgoCD server running on localhost and accessible via port-forwarding.
- ![Screenshot 2024-04-26 171013](https://github.com/gbaeke/demo-clu-flux/assets/122734275/0f7372ee-e762-4b3b-98c3-d4d9d511d97b)


---


---
## Challenges Faced
### 1.Setup ArgoCD Server
The initial setup of the ArgoCD server involved following official documentation and online tutorials. Post-restart issues were encountered but resolved by switching back to the correct Kubernetes context.

**Resolution:** Troubleshooting skills were utilized to identify and resolve configuration issues, ensuring the successful setup of the ArgoCD server.

---

## 2.Rollout Definition with Canary Strategy
Creating a rollout definition with a canary strategy presented challenges related to invalid specifications and rollout failures.

**Resolution:** Through trial and error, the rollout.yaml file was corrected, and each step was configured according to ArgoCD's requirements. This experience enhanced understanding of canary deployments and YAML configurations.

---

## 3.Docker Image Update and Deployment
Updating Docker images and deploying them via ArgoCD posed challenges regarding image version inconsistencies and rollout states.

**Resolution:** In-depth review and correction of rollout.yaml and deployment.yaml files led to successful image updates and rollout deployments, ensuring application stability.

---

---
## Cleanup

   To cleanly remove all resources created during this assignment from the Kubernetes cluster , I follwed these steps:

   1. **To Delete the Deployed Application**:
      ```
      kubectl delete rollout my-app-rollout
      ```

   2. **To sdlete Argo CD Installation**:
      ```
      kubectl delete -n argocd --all
      ```
      to remove the `argocd` namespace as well
      ```
      kubectl delete namespace argocd
      ```

   3. **To delete Argo Rollouts Installation**:
      ```
      kubectl delete -n argocd --all
      ```
      

   4. **Remove Any Additional Resources**:
      
      
      ```
      kubectl delete namespace arogocd
      ```

   5. **Verify Cluster Clean-up**:
      After executing all the deletion commands, I neeeded to verify that the resoruces are dleted which I by this command:
      ```
      kubectl get all --all-namespaces
      ```



## What I Learned

During this assignment, I delved into several key areas of DevOps and deployment strategies. Here are some abstract insights and learnings:

- Embracing Canary Deployments: Understanding the nuances of canary deployments, including the gradual rollout and monitoring strategies, deepened my grasp of continuous delivery practices.
- Leveraging DevOps Tools: Working with ArgoCD and Argo Rollouts showcased the power of declarative deployment tools in managing complex application lifecycles efficiently.
- Troubleshooting and Problem Solving: Dealing with challenges such as YAML configuration errors and rollout failures honed my troubleshooting skills and taught me valuable lessons in resilience and persistence.

This documentation not only captures the technical steps but also reflects on the learning journey and growth as a DevOps practitioner throughout the assignment.
