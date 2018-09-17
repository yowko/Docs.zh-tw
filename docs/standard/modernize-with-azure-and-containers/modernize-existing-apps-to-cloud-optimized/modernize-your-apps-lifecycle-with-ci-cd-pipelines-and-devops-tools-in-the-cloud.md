---
title: 現代化您的應用程式生命週期 CI/CD 管線與雲端中的 DevOps 工具
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |現代化您的應用程式生命週期 CI/CD 管線與雲端中的 DevOps 工具
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c4d3eaa50f6c7645c954ca65bf42c6c1eab3a68d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742869"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>現代化您的應用程式生命週期 CI/CD 管線與雲端中的 DevOps 工具

現今的企業需要速度很快即可具競爭力的市場中發揮創意。 交付高品質、 現代化應用程式需要 DevOps 工具和程序會實作這個持續的循環的創新的關鍵。 使用適當的 DevOps 工具，開發人員可以簡化持續部署，並更快速創新的應用程式傳遞給的使用者。

雖然持續整合和部署作法全都堅實的建立，容器的簡介會介紹新的考量，特別是當您正在使用多容器應用程式。

Azure 的 DevOps 服務支援持續整合和多容器應用程式部署到各種不同的環境，透過的官方 Azure DevOps 服務部署工作：

-   [部署為獨立部署 Docker 主機 VM](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) （Linux 或 Windows Server 2016 或更新版本）

-   [部署到 Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [部署至 Azure Container Service-Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

但是您也可以部署到[Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)或 DC/OS 使用 Azure DevOps 服務指令碼為基礎的工作。

若要繼續加速部署靈活度，這些工具會提供絕佳的開發到測試-至-生產部署容器工作負載，使用您選擇的開發和 CI/CD 解決方案體驗。

圖 4 到 12 個顯示持續部署管線，以部署至 Azure Container Service 中 Kubernetes 叢集。

![Azure 的 DevOps 服務持續部署管線，將部署到 Kubernetes 叢集](./media/image12.png)

> **圖 4 到 12 個。** Azure 的 DevOps 服務持續部署管線，將部署到 Kubernetes 叢集

>[!div class="step-by-step"]
[上一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
[下一頁](migrate-to-hybrid-cloud-scenarios.md)
