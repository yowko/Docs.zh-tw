---
title: 選擇容器應用程式的 Azure 計算平台
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |選擇容器型應用程式的 Azure 計算平台
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: f251aecfeaf2421a5cecf218577369963bc736fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811747"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>選擇容器應用程式的 Azure 計算平台

閱讀前幾節之後，您已經注意到，則 Azure 會是開放式的雲端，可提供多個選項。 您可以使用最適合您的需求，不過，它也會呈現有關容器化應用程式，您應該使用哪些產品/技術問題。

作為*預設為*建議，以下是主要的準則，建議您在本指南中：

- **單一的單體式應用程式：** 選擇 Azure App Service
- **多層式架構應用程式：** 如果您有單一或少數的後端服務，請選擇協調器，例如 Azure Kubernetes Service (AKS)、 Service Fabric (SF) 或 App Service
- **Linux 的微服務：** 選擇 AKS/Kubernetes
- **Windows 的微服務：** 選擇 Service Fabric
- **無伺服器函式 （&) 事件處理常式：** 選擇 Azure 函式
- **大規模的批次：** 選擇 Azure 批次

不過，這項建議應該隨著一小段 salt，如產品的選擇取決於特定應用程式的需求和特性。 一開始它們看起來類似的型別時，即使並非所有應用程式都是相同的。

在應用程式的需求的更深入的分析之後, 所選擇的產品可能不同。 不過，做為起點，最好能夠從何處開始評估的初始指導方針，並且測試根據特定優先權。

在下一個圖中，您可以分析詳細的決策表時更全域項目。

![](./media/image8.5.png)

請注意如何基礎作業系統 （Windows 與。因為某些 orchestrator 更成熟 Linux 容器和 Windows 容器上其他 Linux) 也可以是決策因素。 比方說，Linux 容器是在 Kubernetes 中 (在 Azure 中的 AKS) 但較不成熟，Service Fabric 上非常成熟。 相反地，Windows 容器是較為成熟 （2017 年發行） 的 Service Fabric 中和在 AKS 中較不成熟。

不過，OS 成熟度的這些差異會在未來淡出多個平台會有類似的 OS 成熟度並決定將提供詳細說明根據您的應用程式可能需要或根據每個平台生態系統的特定功能的喜好設定原因。

> [!div class="step-by-step"]
> [上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
