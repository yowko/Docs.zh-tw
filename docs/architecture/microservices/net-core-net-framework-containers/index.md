---
title: 針對 Docker 容器在 .NET 5 和 .NET Framework 之間進行選擇
description: 容器化 .NET 應用程式的 .NET 微服務架構 |針對 Docker 容器在 .NET 5 和 .NET Framework 之間進行選擇
ms.date: 01/13/2021
ms.openlocfilehash: 5c7ea1be02722fce7c5784afa89c18defbe4eeaf
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188643"
---
# <a name="choosing-between-net-and-net-framework-for-docker-containers"></a><span data-ttu-id="28f82-103">在 Docker 容器的 .NET 和 .NET Framework 之間進行選擇</span><span class="sxs-lookup"><span data-stu-id="28f82-103">Choosing Between .NET and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="28f82-104">使用 .NET 建立伺服器端容器化 Docker 應用程式有兩種支援的架構： [.NET Framework 和 .net 5](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="28f82-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="28f82-105">這兩者共用許多 .NET 平台元件，而您可以在這兩者間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="28f82-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="28f82-106">不過，兩者間有一些基本差異，而您可以依據想要完成的目標決定要使用的架構。</span><span class="sxs-lookup"><span data-stu-id="28f82-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="28f82-107">本節提供每個架構選擇時機的指引。</span><span class="sxs-lookup"><span data-stu-id="28f82-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="28f82-108">[上一個](../container-docker-introduction/docker-containers-images-registries.md) 
>[下一步](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="28f82-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
