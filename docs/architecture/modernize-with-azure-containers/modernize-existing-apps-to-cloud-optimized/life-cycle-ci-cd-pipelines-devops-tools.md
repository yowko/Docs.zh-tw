---
title: 在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式的生命週期現代化
ms.date: 04/30/2018
ms.openlocfilehash: d1aa2e156e87cafe99fb994233786f67bf7a81a1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396212"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化

現今的企業需要以快速的步調創新，以在 marketplace 中獲得競爭優勢。 提供高品質的現代化應用程式需要 DevOps 的工具和流程，這是實現這項不斷創新週期的關鍵。 開發人員可以使用適當的 DevOps 工具，簡化持續部署，並更快速地將創新的應用程式交給使用者。

雖然已妥善建立持續整合和部署作法，但容器的引進會引進新的考慮，特別是當您使用多容器應用程式時。

Azure DevOps Services 透過官方 Azure DevOps Services 部署工作，支援多容器應用程式的持續整合和部署到各種環境：

- [部署至 Azure 用於容器的 Web App](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [部署至 Azure Kubernetes Service](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

但是您也可以使用 Azure DevOps Services 腳本工作，部署到[Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)或 DC/OS。

為了繼續加速部署的靈活性，這些工具為容器工作負載提供了絕佳的開發與測試對生產部署體驗，並可選擇開發和 CI/CD 解決方案。

圖4-12 顯示會在 Azure Container Service 中部署至 Kubernetes 叢集的持續部署管線。

![Azure DevOps Services 部署至 Kubernetes 叢集的螢幕擷取畫面。](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**圖4-12。** Azure DevOps Services 持續部署管線，部署至 Kubernetes 叢集

>[!div class="step-by-step"]
>[上一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
>[下一頁](migrate-to-hybrid-cloud-scenarios.md)
