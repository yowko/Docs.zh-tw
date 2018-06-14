---
title: 選擇容器應用程式的 Azure 運算平台
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |選擇容器應用程式的 Azure 運算平台
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958008"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>選擇容器應用程式的 Azure 運算平台

您已注意到閱讀上一節之後，Azure 會是提供了多個選項在開啟的雲端。 您可以使用最適合您的需求，不過，它也會提供諸如您容器化應用程式應該使用哪些產品/技術有關的問題。

做為*依預設*建議中，以下是建議您在本指南中的主要標準：

  - **單一龐大的應用程式：** 選擇 Azure App Service
  - **多層式架構應用程式：** 選擇 orchestrators，例如 Azure Kubernetes 服務 (AKS)、 服務網狀架構 (SF) 或應用程式服務，如果您有一部或幾個後端服務
  - **Linux microservices:** 選擇 AKS/Kubernetes
  - **Windows microservices:** 選擇 Service Fabric
  - **無伺服器函式 （& s) 事件處理常式：** 選擇 Azure 函式
  - **大型批次：** 選擇 Azure 批次

不過，這項建議應採取的 salt 捏合與產品的選取項目會取決於特定應用程式的需求和特性。 一開始它們看起來類似的類型時，即使並非所有應用程式都是相同的。

應用程式的需求更深入分析後, 所選擇的產品可能會不同。 但是，做為起點，最好能夠從何處開始評估初始的指導方針，而且測試會依據特定的優先順序。

在下一個圖中，您可以分析更通用時詳細的決策表。

![](./media/image8.5.png)

請注意如何基礎作業系統 （Windows 與。Linux) 也可以決策因數某些 orchestrators 更成熟 Linux 容器上與其他 Windows 容器上也不一樣。 比方說，Linux 容器是非常成熟 Kubernetes (在 Azure 中 AKS) 中但較不成熟服務網狀架構上。 相反地，Windows 容器是成熟 Service Fabric （2017 年發行） 中，較不成熟 AKS 中。

不過，OS 成熟度的這些差異會在未來淡出多個平台會比較 OS 成熟度，以及擁有決策會配置更詳細的喜好設定，根據您的應用程式可能需要或根據每個平台生態系統的特定功能原因。


>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
