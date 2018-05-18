---
title: 決策資料表。 用於 Docker 的 .NET Frameworks
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 決策資料表，用於 Docker 的 .NET Frameworks
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0e384fabca88d8ad6f93ae626140fb3d5dcaf971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>決策資料表：用於 Docker 的 .NET Frameworks

以下摘述要使用 .NET Framework 或 .NET Core，以及 Windows 或 Linux 容器。 請記住，Linux 容器需要以 Linux 為架構的 Docker 主機 (VM 或伺服器)，而 Windows 容器需要以 Windows Server 為架構的 Docker 主機 (VM 或伺服器)。

您的應用程式有幾項功能會影響您的決定。 在做決定時，您應該衡量這些功能的重要性。

> [!IMPORTANT]
> 您的開發電腦會執行一部 Docker 主機，Linux 或 Windows。 您想要在一個解決方案中執行並測試的相關微服務，都需要在相同的容器平台上執行。

* 您的應用程式架構選擇是**容器上的微服務**。
    - 您的 .NET 實作選擇應該是 *.NET Core*。
    - 您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。
* 您的應用程式架構選擇是**整合型應用程式**。
    - 您的 .NET 實作選擇可以是 *.NET Core* 或 *.NET Framework*。
    - 如已選擇 *.NET Core*，則您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。
    - 如已選擇 *.NET Framework*，則您的容器平台選擇必須是「Windows 容器」。
* 您的應用程式是**新的容器型開發 (「綠燈區」)**。
    - 您的 .NET 實作選擇應該是 *.NET Core*。
    - 您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。
* 您的應用程式是 **Windows Server 舊版應用程式 (「棕地」) 移轉至容器**
    - 您的 .NET 實作選擇是以架構相依性為基礎的 *.NET Framework*。
    - 因為 .NET Framework 的相依性，您的容器平台選擇必須是「Windows 容器」。
* 您的應用程式設計目的是**最高等級的效能和延展性**。
    - 您的 .NET 實作選擇應該是 *.NET Core*。
    - 您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。
* 您使用 **ASP.NET Core** 組建應用程式。
    - 您的 .NET 實作選擇應該是 *.NET Core*。
    - 如果您有其他架構相依性，可以使用 *.NET Framework* 實作。
    - 如已選擇 *.NET Core*，則您的容器平台選擇可以是「Linux 容器」或「Windows 容器」。
    - 如已選擇 *.NET Framework*，則您的容器平台選擇必須是「Windows 容器」。
* 您使用 **ASP.NET 4 (MVC 5、Web API 2 和 Web Forms)** 組建應用程式。
    - 您的 .NET 實作選擇是以架構相依性為基礎的 *.NET Framework*。
    - 因為 .NET Framework 的相依性，您的容器平台選擇必須是「Windows 容器」。
* 您的應用程式使用 **SignalR 服務**。
    - 您的 .NET 實作選擇可以是 *.NET Framework* 或 *.NET Core 2.1 (發行後) 或更新版本*。
    - 如果在 .NET Framework 中選擇 SignalR 實作，您的容器平台選擇必須是「Windows 容器」。
    - 如果您在 .NET Core 2.1 或更新版本 (發行後) 中選擇 SignalR 實作，您的容器平台選擇可以是 Linux 容器或 Windows 容器。  
    - 在 *.NET Core* 執行 **SignalR 服務**時，您可以使用「Linux 容器或 Windows 容器」。
* 您的應用程式使用 **WCF、WF 和其他舊版架構**。
    - 您的 .NET 實作選擇是 *.NET Framework* 或 *.NET Core (未來的版本藍圖)*。
    - 因為 .NET Framework 的相依性，您的容器平台選擇必須是「Windows 容器」。
* 您的應用程式牽涉到**取用 Azure 服務**。
    - 您的 .NET 實作選擇是 *.NET Framework* 或 *.NET Core (所有 Azure 服務最終都會提供適用於 .NET Core 的用戶端 SDK)*。
    - 如果使用 .NET Framework 用戶端 API，您的容器平台選擇必須是「Windows 容器」。
    - 如果使用 *.NET Core* 可用的用戶端 API，您也可以選擇「Linux 容器或 Windows 容器」。

>[!div class="step-by-step"]
[上一頁] (net-framework-container-scenarios.md) [下一頁] (net-container-os-targets.md)
