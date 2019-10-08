---
title: 管理生產 Docker 環境
description: 了解管理容器型生產環境的關鍵點。
ms.date: 02/15/2019
ms.openlocfilehash: 26e7a3319afe593d75e2384d023c901a389245dc
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834511"
---
# <a name="manage-production-docker-environments"></a>管理生產 Docker 環境

叢集管理和協調流程是控制一群主機的處理序。 這可能包括新增和移除叢集中的主機、取得主機和容器目前狀態的相關資訊，以及啟動與停止。 叢集管理和協調流程與排程緊密相關，因為排程器必須擁有叢集中每一部主機的存取權，才能對服務進行排程。 因此，同一個工具通常同時用於這兩種用途。

## <a name="container-service-and-management-tools"></a>容器服務與管理工具

容器服務支援快速部署常用的開放原始碼容器叢集和協調流程解決方案。 它會使用 Docker 映像，以確保您的應用程式容器具有完整可攜性。 透過使用容器服務，您可以使用 Azure Resource Manager 範本或 Azure 入口網站部署 DC/OS (由 Mesosphere 和 Apache Mesos 提供技術支援) 和 Docker Swarm 叢集，以確保您能夠將這些應用程式擴展到數千個，甚至是數萬個容器。

您會使用 Azure 虛擬機器擴展集來部署這些叢集，而叢集會利用 Azure 網路和儲存體供應專案。 若要存取容器服務，您需要有 Azure 訂用帳戶。 藉由使用容器服務，您可以充分利用 Azure 的企業級功能，同時仍可保有應用程式的可攜性，包括協調流程層級。

表 6-1 列出與其協調器、排程器及叢集平台相關的一般管理工具。

**表 6-1**. Docker 管理工具

| 管理工具 | 描述 | 相關協調器 |
|------------------|-------------|-----------------------|
| [適用於容器的 Azure 監視器](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Azure 專用的 Kubernetes 管理工具 | Azure Kubernetes Services (AKS) |
| [Kubernetes Web UI (儀表板)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Kubernetes 管理工具，可以監視及管理本機的 Kubernetes 叢集 | Azure Kubernetes Service (AKS)<br/>本機 Kubernetes |
| [適用於 Service Fabric 的 Azure 入口網站](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Azure、內部部署、本機開發及其他雲端中用來管理 Service Fabric 叢集的線上和桌面版本 | Azure Service Fabric |
| [容器監視 (Azure 監視器)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | 一般的容器管理與監視解決方案。 可以透過[適用於容器的 Azure 監視器](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview)管理 Kubernetes 叢集。 | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS 及其他項目。 |

## <a name="azure-service-fabric"></a>Azure Service Fabric

叢集部署和管理的另一個選擇是 Azure Service Fabric。 [Service Fabric](https://azure.microsoft.com/services/service-fabric/) 是　Microsoft 微服務平台，其中包含容器協調流程以及開發人員程式設計模型，用來建置可高度擴充的微服務應用程式。 Service Fabric 支援 Linux 和 Windows 容器中的 Docker，且可以在 Windows 和 Linux 伺服器中執行。

以下是 Service Fabric 管理工具：

- [適用於 Service Fabric 的 Azure 入口網站](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)可對叢集進行叢集相關作業 (建立/更新/刪除)，或設定其基礎結構 (VM、負載平衡器、網路功能等)。

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) 是一種特製化的 Web UI 和桌面多平台工具，可從節點/VM 觀點以及從應用程式和服務觀點，提供對 Service Fabric 叢集的見解及作業。

>[!div class="step-by-step"]
>[上一頁](run-microservices-based-applications-in-production.md)
>[下一頁](monitor-containerized-application-services.md)
