---
title: 管理生產 Docker 環境
description: 了解管理容器為基礎的生產環境的關鍵要點。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3f8c51b95f52a655de470ac237c51dd4ee9c13eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922573"
---
# <a name="manage-production-docker-environments"></a>管理生產 Docker 環境

叢集管理和協調流程會控制一群主控件程序。 這可以包括新增和移除叢集，以取得資訊的目前狀態的主機和容器，以及啟動和停止處理程序中的主機。 叢集管理和協調流程與排程的排程器必須存取每一部主機叢集中以排程服務因為緊密相關。 基於這個理由，通常用於這兩種用途的相同的工具。

## <a name="container-service-and-management-tools"></a>容器服務和管理工具

Container Service 提供快速部署常用的開放原始碼容器叢集和協調流程解決方案。 若要確保您的應用程式容器具有完整可攜性，它就會使用 Docker 映像。 使用 Container Service，您可以部署 （由 Mesosphere 和 Apache Mesos） 的 DC/OS 和 Docker Swarm 叢集的 Azure Resource Manager 範本或 Azure 入口網站，以確保您可以調整這些應用程式至數千個，甚至是幾萬個 — 的容器。

使用 Azure 虛擬機器擴展集，部署這些叢集和叢集會利用 Azure 網路和儲存體供應項目。 若要存取 Container Service，您需要 Azure 訂用帳戶。 使用容器服務時，您可以充分利用 Azure 的企業級功能，同時仍可保有應用程式可攜性，包括協調流程層。

表 6-1 會列出其協調器、 排程器和叢集平台相關的一般管理工具。

**表 6-1**。 Docker 管理工具

| 管理工具 | 描述 | 相關的協調器 |
|------------------|-------------|-----------------------|
| [適用於容器的 azure 監視器](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Azure 的專用的 Kubernetes 管理工具 | Azure Kubernetes 服務 (AKS) |
| [Kubernetes Web UI （儀表板）](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Kubernetes 的管理工具，可以監視及管理本機的 Kubernetes 叢集 | Azure Kubernetes Service (AKS)<br/>本機 Kubernetes |
| [適用於 Service Fabric 的 azure 入口網站](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | 如需管理 Service Fabric 叢集，在 Azure 上、 在內部部署、 本機開發，以及其他雲端的線上和桌面版本 | Azure Service Fabric |
| [容器監視 （Azure 監視器）](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | 一般的容器監視解決方案的管理 y。 可以管理 Kubernetes 叢集，透過[適用於容器的 Azure 監視器](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview)。 | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS 和其他項目。 |

## <a name="azure-service-fabric"></a>Azure Service Fabric

叢集中部署和管理的另一個選擇是 Azure Service Fabric。 [Service Fabric](https://azure.microsoft.com/services/service-fabric/) Microsoft 的微服務平台，其中包含容器協調流程，以及開發人員的程式設計模型，以建置可高度擴充的微服務應用程式。 Service Fabric 支援 Linux 和 Windows 容器中的 Docker，並可以在 Windows 和 Linux 伺服器中執行。

以下是 Service Fabric 管理工具：

- [適用於 Service Fabric 的 azure 入口網站](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)叢集相關的作業 （建立/更新/刪除） 的叢集，或設定其基礎結構 (Vm、 負載平衡器、 網路功能等。)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster)是特製化 web UI 和桌面提供深入解析和在 Service Fabric 叢集上，從節點 /vm 觀點來看，並從應用程式和服務的觀點來看的特定作業的多平台工具。

>[!div class="step-by-step"]
>[上一頁](run-microservices-based-applications-in-production.md)
>[下一頁](monitor-containerized-application-services.md)
