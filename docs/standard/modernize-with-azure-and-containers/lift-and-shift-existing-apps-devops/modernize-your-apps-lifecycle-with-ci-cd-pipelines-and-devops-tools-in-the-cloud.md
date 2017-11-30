---
title: "現代化雲端中的 DevOps 工具 CI/CD 管線與您的應用程式生命週期"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |現代化雲端中的 DevOps 工具 CI/CD 管線與您的應用程式生命週期"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 2799f203cec2b01d2c9ff1a60ece801dc5939104
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>現代化雲端中的 DevOps 工具 CI/CD 管線與您的應用程式生命週期

現今的企業需要 marketplace 處於競爭腳步創新。 現代應用程式提供高品質，需要 DevOps 工具和實作的創新此常數週期不可或缺的程序。 使用適當的 DevOps 工具，開發人員可以簡化連續部署，並更快取得的使用者在未授權者手的創新應用程式。

雖然全都堅實的連續整合及部署的作法，容器的簡介會引進新的考量，特別是當您正在使用多個容器應用程式。

Visual Studio Team Services 支援連續整合及多容器應用程式部署到各種不同的環境，完成的官方 Team Services 部署工作：

-   [將部署至獨立 Docker 主機 VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) （Linux 或 Windows Server 2016 或更新版本）

-   [部署 Service fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [部署至 Azure 的容器服務 – Kubernetes](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

但您也可以部署到[Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)或 DC/OS 使用 Team Services 指令碼為基礎的工作。

若要繼續促進部署靈活度，這些工具會提供絕佳的開發人員若要為測試-至生產部署發生時針對容器的工作負載，透過選擇的開發和 CI/CD 解決方案。

圖 4-12 顯示部署至 Kubernetes 叢集 Azure 容器服務中的連續部署管線。

![Visual Studio Team Services 連續部署管線，將部署至 Kubernetes 叢集](./media/image12.png)

> **圖 4-12。** Visual Studio Team Services 連續部署管線，將部署至 Kubernetes 叢集

>[!div class="step-by-step"]
[上一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
[下一頁](migrate-to-hybrid-cloud-scenarios.md)
