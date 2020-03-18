---
title: 選擇容器應用程式的 Azure 計算平台
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |為基於容器的應用程式選擇 Azure 計算平臺
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503870"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>選擇容器應用程式的 Azure 計算平台

正如您在閱讀前幾節後注意到的那樣，Azure 是一個開放雲，提供多種選擇。 您可以使用最適合您的需求，但是，它也引發了有關在容器化應用程式中應該使用哪些產品/技術的問題。

作為*預設*建議，本指南建議的主要標準如下：

- **單片式應用程式：** 選擇 Azure 應用服務
- **N-Tier 應用：** 如果您有單個或幾個後端服務，請選擇協調器，如 Azure 庫伯奈服務 （AKS） 或應用服務
- **微服務：** 為容器選擇 AKS 或 Azure Web 應用
- **無伺服器函數&事件處理常式：** 選擇 Azure 函數
- **大型批次：** 選擇 Azure 批次處理

但是，此建議應該帶有一點鹽，因為產品的選擇將取決於您的特定應用的需求和特性。 並非所有應用程式都相同，即使最初它們看起來可能相似。

對應用程式的需求進行更深入的分析後，所選產品可能有所不同。 但是，作為起點，最好從何處獲得初始指導，以便根據某些優先順序開始評估和測試。

在下表中，您可以看到不同類型的應用及其可能和推薦的 Azure 託管方案的細目。

| 應用程式架構 | VM - Azure 虛擬機器 | ACI - Azure 容器實例 | Azure 應用服務（ww/o 容器） | AKS - Azure 庫伯奈斯服務 | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Web 應用（單體）**         | ![使用 VM 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![與 ACI 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![建議使用應用服務](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **N 層應用（服務）**        | ![使用 VM 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![與 ACI 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![建議使用應用服務](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![使用 Azure 引信可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **雲原生（微服務）**  | | ![與 ACI 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![建議使用 AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> （Linux&nbsp;容器）| ![建議使用 Azure 函數](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> （事件&#x2011;驅動） | |
| **批次處理/作業（背景工作）** | ![使用 VM 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![與 ACI 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![可能使用應用服務](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![AKS 可能](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![建議使用 Azure 函數](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> （後臺&nbsp;任務） | ![隨 Azure 批次處理一起推薦](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> （大&#x2011;規模） |

**傳說**

![推薦圖示](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) 推薦 |
![可能的圖示](media/choosing-azure-compute-options-for-container-based-applications/possible.png) 可能

> [!div class="step-by-step"]
> [上一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [下一個](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
