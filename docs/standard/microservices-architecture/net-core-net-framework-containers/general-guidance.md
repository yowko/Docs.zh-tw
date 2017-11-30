---
title: "一般指導方針"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |一般指導方針"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a>一般指導方針

本節提供何時選擇.NET Core 或.NET Framework 的摘要。 我們提供更多詳細以下各節中的這些選項。

您應該使用.NET Core Linux 或 Windows 容器 Docker 伺服器應用程式容器化時：

-   您有跨平台需求。 例如，您要使用 Linux 和 Windows 容器。

-   您的應用程式的架構根據 microservices。

-   您需要快速啟動容器，而且想以降低成本的每個容器，以達到更佳的密度或更多的容器，每個硬體單位佔空間很小。

簡單地說，當您建立新容器化的.NET 應用程式，您應該考慮.NET Core 以預設選項。 它有許多優點，並最符合的原理容器和工作樣式。

使用.NET Core 的另一個優點是，您可以執行並存的同一部電腦中的應用程式的.NET 版本。 這項優點是更重要的伺服器或不使用容器，容器的 Vm，因為容器隔離的應用程式所需的.NET 版本。 （只要它們是與基礎作業系統相容。）

您應該使用.NET Framework 中，使用 Windows 容器 Docker 伺服器應用程式容器化時：

-   目前應用程式會使用.NET Framework 和 Windows 具有強式的相依性。

-   您需要使用.NET 核心不支援的 Windows Api。

-   您要使用協力廠商.NET 程式庫或不適用於.NET Core 的 NuGet 封裝。

在 Docker 中使用.NET Framework 可以改善您的部署經驗部署問題降至最低。 這[ *「 提起和 shift 」 案例*](https://aka.ms/liftandshiftwithcontainersebook)是很重要的 containerizing 原本是開發與傳統.NET Framework 中，像 ASP.NET WebForms、 MVC web 應用程式或 WCF （的舊版應用程式Windows Communication Foundation) 服務。

### <a name="additional-resources"></a>其他資源

-   **電子書： 現代化現有的.NET Framework 應用程式使用 Azure 和 Windows 容器**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **範例應用程式： 現代化的舊版 ASP.NET web 應用程式，藉由使用 Windows 容器**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[上一個](index.md) [下一步] (net-核心-容器-scenarios.md)
