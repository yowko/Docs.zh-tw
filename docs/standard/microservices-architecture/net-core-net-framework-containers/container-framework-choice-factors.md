---
title: "決策表。 要用於 Docker 的.NET framework"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |決定資料表中，用於 Docker 的.NET framework"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>決定資料表： 用於 Docker 的.NET framework

以下摘述是否要使用.NET Framework 或.NET Core 和 Windows 或 Linux 容器。 請記住，對於 Linux 容器，您需要以 Linux 為基礎的 Docker 主機 （Vm 或伺服器），Windows 容器您需要 Windows Server 為基礎的 Docker 主機 （Vm 或伺服器）。

有數個會影響您的決定應用程式的功能。 在做決定時，您應該衡量這些功能的重要性。

> [!IMPORTANT]
> 您的開發電腦將會執行一部 Docker 主機，Linux 或 Windows。 您想要執行和一起測試在單一解決方案中的相關的 microservices 所有必須在相同的容器平台上執行。

* 您的應用程式架構的選擇是**容器 Microservices**。
    - 您的.NET 實作選擇應該是*.NET Core*。
    - 容器的平台選擇可以是*Linux 容器*或*Windows 容器*。
* 您的應用程式架構的選擇是**整合型應用程式**。
    - 您的.NET 實作選擇可以是*.NET Core*或*.NET Framework*。
    - 如果您已選擇*.NET Core*，容器平台的選擇可以是*Linux 容器*或*Windows 容器*。
    - 如果您已選擇*.NET Framework*，必須是容器的平台選擇*Windows 容器*。
* 您的應用程式**新容器為基礎的開發工作 （「 綠色欄位 」）**。
    - 您的.NET 實作選擇應該是*.NET Core*。
    - 容器的平台選擇可以是*Linux 容器*或*Windows 容器*。
* 您的應用程式**Windows Server 容器的舊版應用程式 ("brown-field") 移轉**
    - 在.NET 實作選擇時*.NET Framework*基礎架構相依性。
    - 必須是容器的平台選擇*Windows 容器*因為.NET Framework 相依性。
* 您的應用程式的設計目的是**最高等級效能和延展性**。
    - 您的.NET 實作選擇應該是*.NET Core*。
    - 容器的平台選擇可以是*Linux 容器*或*Windows 容器*。
* 您建立應用程式使用**ASP.NET Core**。
    - 您的.NET 實作選擇應該是*.NET Core*。
    - 您可以使用*.NET Framework*實作中，如果您有其他架構相依性。
    - 如果您已選擇*.NET Core*，容器平台的選擇可以是*Linux 容器*或*Windows 容器*。
    - 如果您已選擇*.NET Framework*，必須是容器的平台選擇*Windows 容器*。
* 您建立應用程式使用**（MVC 5、 Web API 2 和 Web Form） 的 ASP.NET 4**。
    - 在.NET 實作選擇時*.NET Framework*基礎架構相依性。
    - 必須是容器的平台選擇*Windows 容器*因為.NET Framework 相依性。
* 您的應用程式會使用**SignalR 服務**。
    - .NET 的實作做出選擇可能很*.NET Framework*，或*（發行時），.NET Core 2.1 或更新版本*。
    - 必須是容器的平台選擇*Windows 容器*如果您選擇.NET Framework 中的 SignalR 實作。
    - 如果您選擇的 SignalR 實作.NET Core 2.1 或更新版本 （發行時），Linux 容器或 Windows 容器可以是容器平台的選擇。  
    - 當**SignalR 服務**上執行*.NET Core*，您可以使用*Linux 容器或 Windows 容器*。
* 您的應用程式會使用**WCF、 WF、 和其他舊版架構**。
    - 在.NET 實作選擇時*.NET Framework*，或*.NET Core （在未來的版本藍圖）*。
    - 必須是容器的平台選擇*Windows 容器*因為.NET Framework 相依性。
* 您的應用程式牽涉到**耗用量的 Azure 服務**。
    - 在.NET 實作選擇時*.NET Framework*，或*（最終所有 Azure 服務會提供用戶端 Sdk 適用於.NET Core） 的.NET Core*。
    - 必須是容器的平台選擇*Windows 容器*如果您使用.NET Framework 用戶端應用程式開發介面。
    - 如果您使用用戶端應用程式開發介面可供*.NET Core*，您也可以選擇*Linux 容器和 Windows 容器*。

>[!div class="step-by-step"]
[上一個](net-framework 的容器-scenarios.md) [下一步] (net-容器-os-targets.md)
