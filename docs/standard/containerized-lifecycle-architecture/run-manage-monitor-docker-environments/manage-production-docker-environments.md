---
title: 管理生產 Docker 環境
description: 了解管理容器為基礎的生產環境的關鍵要點。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 54e2b999f744600d3b6853442bb9ccca004f4e76
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219486"
---
# <a name="manage-production-docker-environments"></a>管理生產 Docker 環境

叢集管理和協調流程會控制一群主控件程序。 這可以包括新增和移除叢集，以取得資訊的目前狀態的主機和容器，以及啟動和停止處理程序中的主機。 叢集管理和協調流程與排程的排程器必須存取每一部主機叢集中以排程服務因為緊密相關。 基於這個理由，通常用於這兩種用途的相同的工具。

## <a name="container-service-and-management-tools"></a>容器服務和管理工具

Container Service 提供快速部署常用的開放原始碼容器叢集和協調流程解決方案。 若要確保您的應用程式容器具有完整可攜性，它就會使用 Docker 映像。 使用 Container Service，您可以部署 （由 Mesosphere 和 Apache Mesos） 的 DC/OS 和 Docker Swarm 叢集的 Azure Resource Manager 範本或 Azure 入口網站，以確保您可以調整這些應用程式至數千個，甚至是幾萬個 — 的容器。

使用 Azure 虛擬機器擴展集，部署這些叢集和叢集會利用 Azure 網路和儲存體供應項目。 若要存取 Container Service，您需要 Azure 訂用帳戶。 使用容器服務時，您可以充分利用 Azure 的企業級功能，同時仍可保有應用程式可攜性，包括協調流程層。

表 6-1 會列出其協調器、 排程器和叢集平台相關的一般管理工具。

表 6-1:Docker 管理工具


| 管理工具      | 描述           | 相關的協調器 |
|-----------------------|-----------------------|-----------------------|
| Container Service\(UI 管理 Azure 入口網站中的) | [Container Service](https://azure.microsoft.com/services/container-service/)提供能夠輕鬆地啟動辦法[部署在 Azure 中的容器叢集](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)根據受歡迎的協調器，例如 Mesosphere DC/OS、 Kubernetes 和 Docker Swarm。 <br /><br /> Container Service 最佳化這些平台的設定。 您只需要選取大小、 主機數量及選擇的協調工具，Container Service 會處理所有其他項目。 | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Docker 通用控制平面\(內部部署或雲端) | [Docker 通用控制平面](https://docs.docker.com/v1.11/ucp/overview/)是企業級的叢集管理解決方案，從 Docker。 它可協助您從單一位置管理整個叢集。 <br /><br /> Docker 通用控制平面是名為提供 Docker Swarm、 Docker 通用控制平面與 Docker Trusted Registry 的 Docker Datacenter 商業產品的一部分。 <br /><br /> Docker Datacenter 可安裝在內部，或從類似 Azure 的公用雲端佈建。 | Docker Swarm\(Container Service 所支援) |
| Docker Cloud\(也稱為 Tutum; 雲端 SaaS) | [Docker 雲端](https://docs.docker.com/docker-cloud/)是裝載的管理服務 (SaaS) 提供協調流程功能和的 Docker 登錄，建置和測試 docker 化應用程式映像，可協助您設定和管理您的主機基礎結構，工具功能可協助您自動化您的映像部署到您具體的基礎結構的部署功能。 您可以連接您的 SaaS Docker 雲端帳戶在 Container Service 中執行的 Docker Swarm 叢集基礎結構。 | Docker Swarm\(Container Service 所支援) |
| Mesosphere Marathon\(內部部署或雲端) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) Mesosphere 的 DC/OS 和 Apache Mesos 是生產等級容器協調流程與排程器平台。 <br /><br /> 它使用 Mesos （DC/OS 根據 Apache Mesos） 來控制長時間執行服務，並提供[程序和容器管理 web UI](https://mesosphere.github.io/marathon/docs/marathon-ui.html)。 它可提供 web UI 管理工具 | Mesosphere DC/OS\(根據 Apache Mesos，Container Service 所支援) |
| Google Kubernetes | [Kubernetes](https://kubernetes.io/docs/user-guide/ui/#dashboard-access)跨越協調、 排程和叢集基礎結構。 它是開放原始碼平台，到叢集中的主機，提供以容器為中心的基礎結構自動化部署、 調整及應用程式容器的作業。 | Google Kubernetes\(Container Service 所支援) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

叢集中部署和管理的另一個選擇是 Azure Service Fabric。 [Service Fabric](https://azure.microsoft.com/services/service-fabric/) Microsoft 的微服務平台，其中包含容器協調流程，以及開發人員的程式設計模型，以建置可靈活調整的微服務應用程式。 Service Fabric 支援在目前的 Linux 預覽版本中，Docker，如同[在 Linux 上的 Service Fabric 預覽](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)，和適用於 Windows 容器[中的下一個版本](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

以下是 Service Fabric 管理工具：

-   [適用於 Service Fabric 的 azure 入口網站](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)叢集相關的作業 （建立/更新/刪除） 的叢集，或設定其基礎結構 (Vm、 負載平衡器、 網路功能等。)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster)是特製化的 web UI 工具，提供深入解析和某些從節點 /vm 觀點來看，並從應用程式和服務的觀點來看，在 Service Fabric 叢集上的作業。

>[!div class="step-by-step"]
>[上一頁](run-microservices-based-applications-in-production.md)
>[下一頁](monitor-containerized-application-services.md)