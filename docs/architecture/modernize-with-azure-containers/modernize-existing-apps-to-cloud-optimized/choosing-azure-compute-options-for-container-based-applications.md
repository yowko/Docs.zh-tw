---
title: 選擇容器應用程式的 Azure 計算平台
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |選擇適用于容器型應用程式的 Azure 計算平臺
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578341"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>選擇容器應用程式的 Azure 計算平台

如您在閱讀前幾節所注意, Azure 是一個開放雲端, 可提供多個選擇。 您可以使用最適合您的需求, 不過, 它也會呈現您應該針對容器化應用程式使用之產品/技術的相關問題。

根據*預設*的建議, 下列是本指南中建議的主要準則:

- **單一整合型應用程式:** 選擇 Azure App Service
- **多層式應用程式:** 如果您有單一或少數後端服務, 請選擇協調器, 例如 Azure Kubernetes Service (AKS) 或 App Service
- **微服務**選擇適用于容器的 AKS 或 Azure Web Apps
- **無伺服器函數 & 事件處理常式:** 選擇 Azure Functions
- **大規模批次:** 選擇 Azure Batch

不過, 這項建議應以一種 salt 來進行, 因為產品的選擇將取決於您的特定應用程式的需求和特性。 並非所有的應用程式都相同, 即使一開始可能看起來像這樣的類型也一樣。

在更深入分析應用程式的需求之後, 所選取的產品可能會不同。 但是做為起點, 您可以根據特定優先順序開始評估和測試的初始指引。

在下一個圖中, 您可以看到不同類型的應用程式及其理想 Azure 裝載案例的細目。

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一頁](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
