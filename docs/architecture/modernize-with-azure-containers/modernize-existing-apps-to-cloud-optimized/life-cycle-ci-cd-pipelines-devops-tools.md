---
title: 在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |使用雲端中的 CI/CD 管線和 DevOps 工具將應用程式的生命週期現代化
ms.date: 12/21/2020
ms.openlocfilehash: f8517ebe8570b8d2be7b49c3cb9e1bc436076af2
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235335"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化

現今的企業需要以快速的步調創新，才能在 marketplace 中具競爭力。 提供高品質的新式應用程式需要 DevOps 的工具和程式，以實現此不斷創新的迴圈。 使用適當的 DevOps 工具，開發人員可以簡化持續的部署，並更快速地將創新的應用程式提供給使用者。

雖然已妥善建立持續整合和部署實務，但導入容器也引進了新的考慮，特別是當您使用多容器應用程式時。

Azure DevOps Services 透過官方 Azure DevOps Services 部署工作，支援多容器應用程式的持續整合和部署到各種環境：

- [部署到 Azure 用於容器的 Web App](/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [部署到 Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

但是您也可以使用 Azure DevOps Services 腳本工作，部署至 [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) 或 DC/OS。

為了持續促進部署的靈活性，這些工具可讓您選擇開發和 CI/CD 解決方案，為容器工作負載提供絕佳的開發/測試對生產部署體驗。

圖4-12 顯示在 Azure Container Service 中部署至 Kubernetes 叢集的持續部署管線。

![Azure DevOps Services 部署至 Kubernetes 叢集的螢幕擷取畫面。](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**圖4-12。** Azure DevOps Services 持續部署管線，部署至 Kubernetes 叢集

>[!div class="step-by-step"]
>[上一個](modernize-your-apps-with-monitoring-and-telemetry.md) 
>[下一步](migrate-to-hybrid-cloud-scenarios.md)
