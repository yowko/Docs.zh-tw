---
title: 決策資料表。 用於 Docker 的 .NET Frameworks
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 決策資料表，用於 Docker 的 .NET Frameworks
ms.date: 09/11/2018
ms.openlocfilehash: 0087d80c2d949daf14e1edd773dd310f47c508a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039671"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>決策資料表：用於 Docker 的 .NET Frameworks

以下決策資料表摘述要使用 .NET Framework 或 .NET Core。 請記住，Linux 容器需要以 Linux 為架構的 Docker 主機 (VM 或伺服器)，而 Windows 容器需要以 Windows Server 為架構的 Docker 主機 (VM 或伺服器)。

> [!IMPORTANT]
> 您的開發電腦會執行一部 Docker 主機，Linux 或 Windows。 您想要在一個解決方案中執行並測試的相關微服務，都需要在相同的容器平台上執行。

| 架構/應用程式類型 | Linux 容器 | Windows 容器 |
|-------------------------|------------------|--------------------|
| 容器上的微服務 | .NET Core | .NET Core |
| 整合型應用程式 | .NET Core | .NET Framework <br/> .NET Core |
| 同級最佳效能和延展性 | .NET Core | .NET Core |
| Windows Server 舊版應用程式 (「棕地」) 移轉至容器 | -- | .NET Framework |
| 新的容器型開發 (「綠燈區」) | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (建議) <br/> .NET Framework |
| ASP.NET 4 (MVC 5、Web API 2 和 Web Form) | -- | .NET Framework |
| SignalR 服務 | .NET Core 2.1 或更新版本 | .NET Framework <br/> .NET Core 2.1 或更新版本 |
| WCF、WF 和其他舊版架構 | .NET Core 中的 WCF （僅限用戶端程式庫） | .NET Framework <br/> .NET Core 中的 WCF （僅限用戶端程式庫） |
| Azure 服務的使用量 | .NET Core <br/> (最終所有 Azure 服務都會提供適用於 .NET Core 的用戶端 SDK) | .NET Framework <br/> .NET Core <br/> (最終所有 Azure 服務都會提供適用於 .NET Core 的用戶端 SDK) |

>[!div class="step-by-step"]
>[上一頁](net-framework-container-scenarios.md)
>[下一頁](net-container-os-targets.md)
