---
title: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 簡介
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: 57c2a598e48f855dd540b96c7ebdb522b4197b91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580259"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式

![封面影像](./media/cover.jpg)


.NET Core 和 ASP.NET Core 提供許多優於傳統.NET 開發的優點。 如果下列部分或所有項目對應用程式成功而言十分重要，則您應該將 .NET Core 用於伺服器應用程式：

-   跨平台支援

-   使用微服務

-   使用 Docker 容器

-   高效能和延展性需求

-   相同伺服器上應用程式之 .NET 版本的並存版本控制

傳統 .NET 應用程式可以並確實支援這些需求，但 ASP.NET Core 和 .NET Core 已最佳化可提供針對上述案例的改善支援。

越來越多的組織會選擇使用 Microsoft Azure 這類服務，以在雲端中裝載其 Web 應用程式。 如果下列對您的應用程式或組織十分重要，則您應該考慮將應用程式裝載在雲端中：

-   降低對資料中心成本的投資 (硬體、軟體、空間、公用程式等等)

-   彈性價格 (根據使用付費，而閒置容量不需付費)

-   極高可靠性

-   改善的應用程式行動性；輕鬆地變更您應用程式的部署位置和方式

-   彈性容量；根據實際需求相應增加或減少

使用 ASP.NET Core 建置 Web 應用程式 (且其裝載於 Microsoft Azure) 提供許多優於傳統替代項目的具競爭性優點。 ASP.NET Core 已針對現代化 Web 應用程式開發做法和雲端裝載案例最佳化。 在本指南中，您將學習如何架構 ASP.NET Core 應用程式以善加利用這些功能。

## <a name="purpose"></a>用途

本指南會提供使用 ASP.NET Core 和 Azure 建置整合型 Web 應用程式的端對端指引。

本指南可補充「使用 .NET 架構和開發容器化和以微服務為基礎的應用程式」，其較著重 Docker、微服務以及裝載企業應用程式的容器的部署。

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>在 .NET 中架構和開發以容器化微服務為基礎的應用程式
> - **電子書**  
> <http://aka.ms/MicroservicesEbook>
> - **範例應用程式**  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南的對象主要是開發人員、開發負責人和架構設計人員，而他們對使用 Microsoft 技術和服務在雲端中建置現代化 Web 應用程式感興趣。

次要對象是技術決策者，其已熟悉 ASP.NET 和 (或) Azure，並尋找是否可以升級為新或現有專案之 ASP.NET Core 的相關資訊。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

本指南已壓縮成相當小的文件，著重於使用現代化 .NET 技術和 Windows Azure 來建置 Web 應用程式。 因此，可以完整讀取它，以提供對這類應用程式和其技術考量的基礎了解。 本指南與其範例應用程式也可以作為起點或參考。 使用相關聯的範例應用程式作為您專屬應用程式的範本，或查看如何組織應用程式的元件組件。 請回頭參考指南的原則、架構和技術選項的涵蓋範圍，以及權衡這些針對您專屬應用程式之選擇的決策考量。

請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。 讓所有人都使用一組共用術語和基礎原則，將有助於確保套用一致的架構模式和做法。

## <a name="references"></a>參考
- **針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**  
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
[下一個] (modern-web-applications-characteristics.md)
