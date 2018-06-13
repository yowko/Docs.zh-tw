---
title: 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b483214e7bd039a71ae642aa26e69d63222af8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580123"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="531bc-103">針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="531bc-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="531bc-104">有兩個支援的實作，可使用 .NET 來建置伺服器端容器化 Docker 應用程式：[.NET Framework](https://www.microsoft.com/net/download/framework) 及 [.NET Core](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="531bc-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="531bc-105">這兩者共用許多 .NET Standard 元件，而您可以在這兩者間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="531bc-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="531bc-106">不過，兩者間有一些基本差異，而您使用的實作取決於您想要完成的目標。</span><span class="sxs-lookup"><span data-stu-id="531bc-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="531bc-107">本節提供每個實作選擇時機的指引。</span><span class="sxs-lookup"><span data-stu-id="531bc-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="531bc-108">[上一個] (../container-docker-introduction/docker-containers-images-registries.md) [下一個] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="531bc-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
