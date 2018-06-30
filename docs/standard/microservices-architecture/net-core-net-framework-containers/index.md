---
title: 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 0f6689468eda1dd1b12c24927e650b2b01381274
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104438"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="b4401-103">針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="b4401-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="b4401-104">有兩個支援的實作，可使用 .NET 來建置伺服器端容器化 Docker 應用程式：[.NET Framework](https://www.microsoft.com/net/download/framework) 及 [.NET Core](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="b4401-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="b4401-105">這兩者共用許多 .NET Standard 元件，而您可以在這兩者間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4401-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="b4401-106">不過，兩者間有一些基本差異，而您使用的實作取決於您想要完成的目標。</span><span class="sxs-lookup"><span data-stu-id="b4401-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="b4401-107">本節提供每個實作選擇時機的指引。</span><span class="sxs-lookup"><span data-stu-id="b4401-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b4401-108">[上一頁](../container-docker-introduction/docker-containers-images-registries.md)
[下一頁](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="b4401-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
