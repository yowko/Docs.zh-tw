---
title: "管理 Docker 的生產環境"
description: "Microsoft 平台和工具與 Docker 容器化應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 5686dcb0932d4a8580fd5ad3daf9e3f5cf52fff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="manage-production-docker-environments"></a>管理 Docker 的生產環境

叢集管理和協調流程是控制一群主控件程序。 這可能涉及到中新增和移除主機叢集，以取得資訊的目前狀態的主機和容器，以及啟動和停止處理程序。 叢集管理和協調流程緊密相關排程，因為排程器必須有叢集中每個主機的存取權才能排程服務。 基於這個理由，相同的工具通常會用於這兩種用途。

## <a name="container-service-and-management-tools"></a>容器服務與管理工具

容器服務提供熱門的開放原始碼容器叢集和協調流程解決方案的快速的部署。 它會使用 Docker images 確保您的應用程式容器可完整移植。 藉由使用容器服務，您可以將 DC/OS （由 Mesosphere 和 Apache Mesos） 部署和 Azure 資源管理員範本或 Azure 入口網站，以確保您可以調整這些應用程式以千分位 Docker Swarm 叢集 — 即使數以萬計的 — 的容器。

使用 Azure 虛擬機器擴展集，部署這些叢集和叢集充分利用 Azure 網路和儲存體供應項目。 若要存取容器服務，您需要 Azure 訂用帳戶。 容器服務時，您可以利用 Azure 的企業級功能仍然維持應用程式可攜性，包括協調流程層級。

表 6-1 會列出其 orchestrators、 排程器和群集的平台相關的常用管理工具。

表 6-1: Docker 管理工具


| 管理工具      | 說明           | 相關的 orchestrators |
|-----------------------|-----------------------|-----------------------|
| 容器服務\(UI 管理 Azure 入口網站中的) | [容器服務](https://azure.microsoft.com/en-us/services/container-service/)提供可以讓啟動方式[部署在 Azure 中的容器叢集](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)根據常用 orchestrators Mesosphere DC/OS、 Kubernetes 和 Docker Swarm 等。 <br /><br /> 容器服務進行最佳化平台所的設定。 您只需要選取大小、 主機、 數目和選擇的 orchestrator 工具，且容器服務會處理所有其他項目。 | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker 群集 |
| Docker 通用控制項的平面\(在內部部署或雲端) | [Docker 通用控制項的平面](https://docs.docker.com/v1.11/ucp/overview/)是企業級叢集管理解決方案，從 Docker。 它可協助您從單一位置管理整個叢集。 <br /><br /> Docker 通用控制項的平面是名為 Docker 資料中心提供 Docker Swarm、 通用控制項平面 Docker 和 Docker Trusted Registry 商業產品的一部分。 <br /><br /> Docker 資料中心可以安裝在內部部署，或如 Azure 公用雲端佈建。 | Docker Swarm\(容器服務支援) |
| Docker 雲端\(也稱為 Tutum; 雲端 SaaS) | [Docker 雲端](https://docs.docker.com/docker-cloud/)是裝載的管理服務 (SaaS) 提供協調流程的功能和 Docker 登錄與建置和測試設備 Dockerized 應用程式映像，可協助您設定和管理您的主機基礎結構，工具和部署功能，可協助您自動化您的映像部署到您具體的基礎結構。 您可以將 SaaS Docker 雲端帳戶連接到您在執行 Docker Swarm 叢集的容器服務中的基礎結構。 | Docker Swarm\(容器服務支援) |
| Mesosphere 馬拉松\(在內部部署或雲端) | [馬拉松](https://mesosphere.github.io/marathon/docs/marathon-ui.html)Mesosphere 的 DC/OS 和 Apache Mesos 是實際執行等級容器協調流程和排程器平台。 <br /><br /> 它使用 Mesos （DC/OS 根據 Apache Mesos） 來控制長時間執行服務，並提供[web UI 的程序和容器管理](https://mesosphere.github.io/marathon/docs/marathon-ui.html)。 它提供的 web UI 管理工具 | Mesosphere DC/OS\(根據 Apache Mesos; 支援的容器服務) |
| Google Kubernetes | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access)跨越協調、 排程及叢集基礎結構。 它是開放原始碼平台自動化部署、 調整及應用程式容器的作業在叢集中的主機，提供容器中心基礎結構。 | Google Kubernetes\(容器服務支援) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

為叢集中部署和管理的另一個選擇是 Azure Service Fabric。 [Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/)包含容器協調流程，以及開發人員的 Microsoft microservices 平台程式設計模型，以建置可高度擴充 microservices 應用程式。 Service Fabric 支援在目前的 Linux 預覽版本中，為在 Docker [Linux 上的 Service Fabric 預覽](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)，以及 Windows 容器[的下一個版本](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

以下是服務網狀架構管理工具：

-   [Azure 入口網站，適用於 Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)叢集相關作業 （建立/更新/刪除） 的叢集或設定其基礎結構 (Vm，負載平衡器、 網路等。)

-   [Azure Service Fabric 總管](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster)是提供深入資訊和從 Vm 節點/觀點來看，並從應用程式及服務觀點來看，Service Fabric 叢集上的特定作業的特殊的 web UI 工具。


>[!div class="step-by-step"]
[上一個](run-microservices-based-applications-in-production.md) [下一步] (監視-容器化的應用程式-services.md)
