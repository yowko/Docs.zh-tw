---
title: 選擇容器應用程式的 Azure 計算平台
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |選擇容器型應用程式的 Azure 計算平台
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833847"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>選擇容器應用程式的 Azure 計算平台

閱讀前幾節之後，您已經注意到，則 Azure 會是開放式的雲端，可提供多個選項。 您可以使用最適合您的需求，不過，它也會呈現有關容器化應用程式，您應該使用哪些產品/技術問題。

作為*預設為*建議，以下是主要的準則，建議您在本指南中：

- **單一的單體式應用程式：** 選擇 Azure App Service
- **多層式架構應用程式：** 如果您有單一或少數的後端服務，請選擇協調器，例如 Azure Kubernetes Service (AKS) 或 App Service
- **微服務：** 選擇 AKS or Azure Web Apps for Containers
- **無伺服器函式 （&) 事件處理常式：** 選擇 Azure 函式
- **大規模的批次：** 選擇 Azure 批次

不過，這項建議應該隨著一小段 salt，如產品的選擇取決於特定應用程式的需求和特性。 一開始它們看起來類似的型別時，即使並非所有應用程式都是相同的。

在應用程式的需求的更深入的分析之後, 所選擇的產品可能不同。 不過，做為起點，最好能夠從何處開始評估的初始指導方針，並且測試根據特定優先權。

在下一個圖中，您可以看到各種不同的應用程式和其理想的 Azure 裝載案例的細目。

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
