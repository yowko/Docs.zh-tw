---
title: 決策資料表。 用於 Docker 的 .NET Frameworks
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 決策資料表，用於 Docker 的 .NET Frameworks
ms.date: 01/13/2021
ms.openlocfilehash: 35f101b3f4030e081068677b3754363bf6cd8210
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188656"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>決策資料表：用於 Docker 的 .NET Frameworks

下列決策表摘要說明是否要使用 .NET Framework 或 .NET 5。 請記住，Linux 容器需要以 Linux 為架構的 Docker 主機 (VM 或伺服器)，而 Windows 容器需要以 Windows Server 為架構的 Docker 主機 (VM 或伺服器)。

> [!IMPORTANT]
> 您的開發電腦會執行一部 Docker 主機，Linux 或 Windows。 您想要在一個解決方案中執行並測試的相關微服務，都需要在相同的容器平台上執行。

| 架構/應用程式類型 | Linux 容器 | Windows 容器 |
|-------------------------|------------------|--------------------|
| 容器上的微服務 | .NET 5 | .NET 5 |
| 整合型應用程式 | .NET 5 | .NET Framework <br/> .NET 5 |
| 同級最佳效能和延展性 | .NET 5 | .NET 5 |
| Windows Server 舊版應用程式 (「棕地」) 移轉至容器 | -- | .NET Framework |
| 新的容器型開發 (「綠燈區」) | .NET 5 | .NET 5 |
| ASP.NET Core | .NET 5 | .NET 5 (建議的)  <br/> .NET Framework |
| ASP.NET 4 (MVC 5、Web API 2 和 Web Form) | -- | .NET Framework |
| SignalR 服務 | .NET Core 2.1 或更新版本 | .NET Framework <br/> .NET Core 2.1 或更新版本 |
| WCF、WF 和其他舊版架構 | .NET Core 中的 WCF 只 (用戶端程式庫)  | .NET Framework <br/> .NET 5 中的 WCF 只 (用戶端程式庫)  |
| Azure 服務的使用量 | .NET 5 <br/>  (最後，大部分的 Azure 服務都會提供適用于 .NET 5 的用戶端 Sdk)  | .NET Framework <br/> .NET 5 <br/>  (最後，大部分的 Azure 服務都會提供適用于 .NET 5 的用戶端 Sdk)  |

>[!div class="step-by-step"]
>[上一個](net-framework-container-scenarios.md) 
>[下一步](net-container-os-targets.md)
