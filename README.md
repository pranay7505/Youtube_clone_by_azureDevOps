# React Web App on Azure with CI/CD 🚀
### This project showcases a modern web application deployment workflow, demonstrating practical DevOps and cloud deployment skills. It features a React frontend deployed on Azure Web App using Azure DevOps CI/CD pipelines for a robust, zero-downtime delivery model.

# 🎯 Purpose of the Project
   Portfolio: A hands-on example to showcase end-to-end deployment skills, from code to cloud.

Learning: A practical deep dive into CI/CD pipelines, artifact management, environment variables, and advanced deployment strategies.

Placement Ready: Demonstrates the ability to deploy real-world applications on cloud platforms following industry best practices.

# 🛠️ Tech Stack
Frontend: React (created with Vite or Create React App)

Cloud: Azure Web App, Azure App Service Slots (Test & Production)

CI/CD: Azure DevOps Pipelines (Build & Release)

Version Control: Azure Repos or GitHub

## 🔄 CI/CD Pipeline
The project uses a two-stage pipeline for continuous integration and continuous deployment.

## Continuous Integration (CI)
A build pipeline automatically triggered on git push or pull request to the main branch.

# Steps:

npm install: Installs project dependencies.

npm run build: Compiles the React application for production.

Archive Files: Creates a .zip artifact of the build output.

Publish Artifact: Makes the artifact available for the deployment stage.

## Continuous Deployment (CD)
A release pipeline automates the deployment to Azure with a staged approach.

## Deploy to Test Slot:

The build artifact is deployed to the Test Slot of the Azure App Service.

This environment is for pre-production testing and validation.

## Pre-deployment Approval:

Manual approval gate to ensure the build is validated before promoting to production.

## Swap to Production:

Once approved, the Test Slot and Production Slot are swapped.

This is an instantaneous operation that provides zero-downtime deployment.

## 🌐 Deployment Details
The application is hosted on an Azure App Service Plan, which can be scaled based on performance and cost requirements.

### App Service Plan Options:

B1 Basic: Suitable for small-scale applications with custom domain support.

F1 Free Tier: Ideal for testing and learning; limited resources, but no cost.

Deployment Slots
This project leverages App Service Slots to enable a Blue-Green Deployment strategy.

Test Slot (Green): Used to deploy and validate new application builds without affecting the live environment.

Production Slot (Blue): The live application accessed by end users.

Swap Mechanism: A verified build in the Test Slot is seamlessly and instantly swapped into the Production Slot.

## 📸 Screenshots

### 1. Staging Slot

Staging environment is used to test new builds before they go live.
Example: Testing React frontend functionality and verifying deployment artifacts.
![Staging Environment](./assets/staging.png)

### 2. Production Slot

Production environment is the live application accessed by end users.
Example: Verified and swapped from staging slot for zero-downtime deployment.
![Production Environment](./assets/production.png)

## 📊 Deployment Strategies
This project primarily uses a Blue-Green Deployment model.

## Blue-Green Deployment
Concept: Two identical environments, Blue (Production) and Green (Staging/Test), run in parallel. New code is deployed to the inactive Green environment and fully validated. Once verified, traffic is instantly rerouted from Blue to Green via a slot swap.

## Advantages:

Zero Downtime: No service interruption for users during deployment.

Easy Rollback: In case of issues, you can instantly swap back to the previous Blue version.

Safe Testing: The new version is tested in a production-like environment before going live.

## Considerations:

Extra Cost: Requires running two environments, though one is typically scaled down.

Data Sync: Requires careful management of database changes or shared data.

## Other Possible Strategies
Canary Deployment: A gradual rollout where a new version is released to a small percentage of users, with performance monitored before a wider release.

Rolling Deployment: Updates instances of the application one by one. This is cost-effective but can lead to a brief period of mixed versions.

Feature Flags / Toggles: Deploy code with new features hidden behind flags. This allows for controlled rollouts and A/B testing without redeploying the application.

## 🚀 Getting Started
To replicate this project, you will need:
An Azure account.
An Azure DevOps organization.

A React application (e.g., created with npx create-react-app my-app or npm create vite@latest).

Push your code to an Azure Repo or GitHub.

Example Build Commands:
Bash
  npm install
  npm run build