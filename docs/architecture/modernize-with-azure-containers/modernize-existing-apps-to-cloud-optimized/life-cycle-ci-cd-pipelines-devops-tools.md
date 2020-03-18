---
title: 在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |借助雲中的 CI/CD 管道和 DevOps 工具實現應用生命週期的現代化
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503844"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>在雲端中使用 CI/CD 管線和 DevOps 工具將應用程式生命週期現代化

當今的企業需要快速創新，才能在市場上具有競爭力。 交付高品質、現代的應用程式需要 DevOps 工具和流程，這對於實現這種持續的創新週期至關重要。 借助正確的 DevOps 工具，開發人員可以簡化持續部署，並更快地將創新應用程式送到使用者手中。

儘管持續集成和部署實踐已經確立，但引入容器會帶來新的注意事項，尤其是在使用多容器應用程式時。

Azure DevOps 服務支援通過正式的 Azure DevOps 服務部署任務持續集成多容器應用程式並部署到各種環境：

- [部署到容器的 Azure Web 應用](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [部署到 Azure 庫伯奈斯服務](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

但是，您也可以通過使用基於 Azure DevOps 服務腳本的任務部署到[Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html)或 DC/OS。

為了繼續提高部署敏捷性，這些工具為容器工作負載提供了出色的從開發到測試到生產的部署體驗，並可以選擇開發和 CI/CD 解決方案。

圖 4-12 顯示了一個連續部署管道，該管道部署到 Azure 容器服務中的 Kubernetes 群集。

![部署到庫伯奈斯群集的 Azure DevOps 服務的螢幕截圖。](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**圖 4-12。** Azure DevOps 服務連續部署管道，部署到庫伯內斯群集

>[!div class="step-by-step"]
>[上一個](modernize-your-apps-with-monitoring-and-telemetry.md)
>[下一個](migrate-to-hybrid-cloud-scenarios.md)
