---
title: 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇
ms.date: 09/11/2018
ms.openlocfilehash: 771d23cf4610e5778f0a144386754ce10d6ae144
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296516"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="f7184-103">針對 Docker 容器在 .NET Core 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="f7184-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="f7184-104">有兩個支援的架構，可使用 .NET 來建置伺服器端容器化 Docker 應用程式：[.NET Framework 及 .NET Core](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="f7184-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="f7184-105">這兩者共用許多 .NET 平台元件，而您可以在這兩者間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7184-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="f7184-106">不過，兩者間有一些基本差異，而您可以依據想要完成的目標決定要使用的架構。</span><span class="sxs-lookup"><span data-stu-id="f7184-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="f7184-107">本節提供每個架構選擇時機的指引。</span><span class="sxs-lookup"><span data-stu-id="f7184-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f7184-108">[上一頁](../container-docker-introduction/docker-containers-images-registries.md)
>[下一頁](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="f7184-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
