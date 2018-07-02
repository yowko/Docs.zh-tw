---
title: 針對 Docker 容器選擇 .NET Framework 的時機
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器選擇 .NET Framework 的時機
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/07/2018
ms.openlocfilehash: 2fdf0c24999891e48e1867e8fa7b4ba0f5302850
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106706"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="cb14f-103">針對 Docker 容器選擇 .NET Framework 的時機</span><span class="sxs-lookup"><span data-stu-id="cb14f-103">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="cb14f-104">儘管 .NET Core 可為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍然是許多現有案例的首選。</span><span class="sxs-lookup"><span data-stu-id="cb14f-104">While .NET Core offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="cb14f-105">將現有應用程式直接移轉至 Windows Server 容器</span><span class="sxs-lookup"><span data-stu-id="cb14f-105">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="cb14f-106">您可能只想要使用 Docker 容器來簡化部署，即使未建立微服務也是一樣。</span><span class="sxs-lookup"><span data-stu-id="cb14f-106">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="cb14f-107">例如，您可能想要使用 Docker 來改善 DevOps 工作流程；容器可讓您更適當地隔離測試環境，也可以去除移至生產環境時遺失相依性所造成的部署問題。</span><span class="sxs-lookup"><span data-stu-id="cb14f-107">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="cb14f-108">如果是這些情況，則即使您要部署整合型應用程式，還是可以將 Docker 和 Windows 容器合理地用於目前 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb14f-108">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="cb14f-109">在大部分情況下，於此案例中，您不需要將現有應用程式移轉至 .NET Core；您可以使用包含傳統 .NET Framework 的 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="cb14f-109">In most cases for this scenario, you will not need to migrate your existing applications to .NET Core; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="cb14f-110">不過，建議您在擴充現有應用程式時使用 .NET Core，例如，在 ASP.NET Core 中寫入新的服務。</span><span class="sxs-lookup"><span data-stu-id="cb14f-110">However, a recommended approach is to use .NET Core as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a><span data-ttu-id="cb14f-111">使用不適用於 .NET Core 的協力廠商 .NET 程式庫或 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="cb14f-111">Using third-party .NET libraries or NuGet packages not available for .NET Core</span></span>

<span data-ttu-id="cb14f-112">協力廠商程式庫會快速採行 [.NET Standard](../../net-standard.md)，以跨所有 .NET 類別 (包含 .NET Core) 共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="cb14f-112">Third-party libraries are quickly embracing the [.NET Standard](../../net-standard.md), which enables code sharing across all .NET flavors, including .NET Core.</span></span> <span data-ttu-id="cb14f-113">使用 .NET Standard 程式庫 2.0 和以上版本，跨不同架構的 API 介面相容性已明顯變好，而且在 .NET Core 2.x 中，應用程式也可以直接參考現有 .NET Framework 程式庫 (請參閱[相容性修正](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work) \(英文\))。</span><span class="sxs-lookup"><span data-stu-id="cb14f-113">With the .NET Standard Library 2.0 and beyond, the API surface compatibility across different frameworks has become significantly larger and in .NET Core 2.x applications can also directly reference existing .NET Framework libraries (see [compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).</span></span>

<span data-ttu-id="cb14f-114">不過，即使自 .NET Standard 2.0 和 .NET Core 2.0 開始有該例外進展，仍然可能有特定 NuGet 套件需要執行 Windows 而且可能不支援 .NET Core 的情況。</span><span class="sxs-lookup"><span data-stu-id="cb14f-114">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.0, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core.</span></span> <span data-ttu-id="cb14f-115">如果這些套件對您的應用程式十分重要，則需要在 Windows 容器上使用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="cb14f-115">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="using-net-technologies-not-available-for-net-core"></a><span data-ttu-id="cb14f-116">使用不適用於 .NET Core 的 .NET 技術</span><span class="sxs-lookup"><span data-stu-id="cb14f-116">Using .NET technologies not available for .NET Core</span></span> 

<span data-ttu-id="cb14f-117">部分 .NET Framework 技術在最新版本的 .NET Core (撰寫本文時為 2.1 版) 中未提供。</span><span class="sxs-lookup"><span data-stu-id="cb14f-117">Some .NET Framework technologies are not available in the current version of .NET Core (version 2.1 as of this writing).</span></span> <span data-ttu-id="cb14f-118">這其中有一些可在更新的 .NET Core 版本 (.NET Core 2.x) 中使用，但其他則不適用於 .NET Core 設為目標的新應用程式模式，而且可能永遠無法使用。</span><span class="sxs-lookup"><span data-stu-id="cb14f-118">Some of them will be available in later .NET Core releases (.NET Core 2.x), but others do not apply to the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="cb14f-119">下列清單顯示 .NET Core 2.1 中未提供的大部分技術：</span><span class="sxs-lookup"><span data-stu-id="cb14f-119">The following list shows most of the technologies that are not available in .NET Core 2.1:</span></span>

-   <span data-ttu-id="cb14f-120">ASP.NET Web Form。</span><span class="sxs-lookup"><span data-stu-id="cb14f-120">ASP.NET Web Forms.</span></span> <span data-ttu-id="cb14f-121">只有在 .NET Framework 上才能使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="cb14f-121">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="cb14f-122">目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cb14f-122">Currently there are no plans to bring ASP.NET Web Forms to .NET Core.</span></span>

-   <span data-ttu-id="cb14f-123">WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="cb14f-123">WCF services.</span></span> <span data-ttu-id="cb14f-124">即使 [WCF-Client 程式庫](https://github.com/dotnet/wcf)可從 .NET Core 使用 WCF 服務時也是一樣。</span><span class="sxs-lookup"><span data-stu-id="cb14f-124">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET Core.</span></span> <span data-ttu-id="cb14f-125">自 2017 年年中開始，才能在 .NET Framework 上使用 WCF 伺服器實作。</span><span class="sxs-lookup"><span data-stu-id="cb14f-125">as of mid-2017, the WCF server implementation is only available on .NET Framework.</span></span> <span data-ttu-id="cb14f-126">.NET Core 的未來版本可能會考慮這項案例。</span><span class="sxs-lookup"><span data-stu-id="cb14f-126">This scenario might be considered for future releases of .NET Core.</span></span>

-   <span data-ttu-id="cb14f-127">工作流程相關服務。</span><span class="sxs-lookup"><span data-stu-id="cb14f-127">Workflow-related services.</span></span> <span data-ttu-id="cb14f-128">Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 ADO.NET Data Services) 僅適用於 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="cb14f-128">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="cb14f-129">目前未計劃將它們帶到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cb14f-129">There are currently no plans to bring them to .NET Core.</span></span>

<span data-ttu-id="cb14f-130">除了正式 [.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)中所列的技術之外，也可能會將其他功能移植至 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cb14f-130">In addition to the technologies listed in the official [.NET Core roadmap](https://github.com/aspnet/Home/wiki/Roadmap), other features might be ported to .NET Core.</span></span> <span data-ttu-id="cb14f-131">如需完整清單，請查看 CoreFX GitHub 網站上標記為 [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) 的項目。</span><span class="sxs-lookup"><span data-stu-id="cb14f-131">For a full list, look at the items tagged as [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) on the CoreFX GitHub site.</span></span> <span data-ttu-id="cb14f-132">請注意，這份清單並不代表 Microsoft 承諾要將這些元件帶入 .NET Core - 這些項目只是擷取社群的要求。</span><span class="sxs-lookup"><span data-stu-id="cb14f-132">Note that this list does not represent a commitment from Microsoft to bring those components to .NET Core — the items simply capture requests from the community.</span></span> <span data-ttu-id="cb14f-133">如果您關心上方所列的任何元件，請考慮參與 GitHub 上的討論，讓我們可以聽到您的心聲。</span><span class="sxs-lookup"><span data-stu-id="cb14f-133">If you care about any of the components listed above, consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="cb14f-134">如果您認為缺少了什麼，請[在 CoreFX 儲存機制中提問新的問題](https://github.com/dotnet/corefx/issues/new)。</span><span class="sxs-lookup"><span data-stu-id="cb14f-134">And if you think something is missing, please [file a new issue in the CoreFX repository](https://github.com/dotnet/corefx/issues/new).</span></span>

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a><span data-ttu-id="cb14f-135">使用不支援 .NET Core 的平台或 API</span><span class="sxs-lookup"><span data-stu-id="cb14f-135">Using a platform or API that does not support .NET Core</span></span>

<span data-ttu-id="cb14f-136">某些 Microsoft 或協力廠商平台不支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cb14f-136">Some Microsoft or third-party platforms do not support .NET Core.</span></span> <span data-ttu-id="cb14f-137">例如，部分 Azure 服務提供尚無法在 .NET Core 上使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="cb14f-137">For example, some Azure services provide an SDK that is not yet available for consumption on .NET Core.</span></span> <span data-ttu-id="cb14f-138">這是暫時性的，因為所有 Azure 服務最終都會使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cb14f-138">This is temporary, because all Azure services will eventually use .NET Core.</span></span> <span data-ttu-id="cb14f-139">例如，[Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 已在 2016 年 11 月 16 日發行為預覽版，但現在已公開上市 (GA) 為穩定版本。</span><span class="sxs-lookup"><span data-stu-id="cb14f-139">For example, the [Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) was released as a preview on November 16, 2016, but it is now generally available (GA) as a stable version.</span></span>

<span data-ttu-id="cb14f-140">同時，如果 Azure 中的任何平台或服務仍然不支援 .NET Core 與其用戶端 API，則您可以在 .NET Framework 上使用 Azure 服務或用戶端 SDK 中的對等 REST API。</span><span class="sxs-lookup"><span data-stu-id="cb14f-140">In the meantime, if any platform or service in Azure still doesn’t support .NET Core with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cb14f-141">其他資源</span><span class="sxs-lookup"><span data-stu-id="cb14f-141">Additional resources</span></span>

-   <span data-ttu-id="cb14f-142">**.NET Core 指南**
    [*https://docs.microsoft.com/dotnet/core/index*](../../../core/index.md)</span><span class="sxs-lookup"><span data-stu-id="cb14f-142">**.NET Core Guide**
[*https://docs.microsoft.com/dotnet/core/index*](../../../core/index.md)</span></span>

-   <span data-ttu-id="cb14f-143">**從 .NET Framework 移植到 .NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](../../../core/porting/index.md)</span><span class="sxs-lookup"><span data-stu-id="cb14f-143">**Porting from .NET Framework to .NET Core**
[*https://docs.microsoft.com/dotnet/core/porting/index*](../../../core/porting/index.md)</span></span>

-   <span data-ttu-id="cb14f-144">**Docker 上的 .NET Framework 指南**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](../../../framework/docker/index.md)</span><span class="sxs-lookup"><span data-stu-id="cb14f-144">**.NET Framework on Docker Guide**
[*https://docs.microsoft.com/dotnet/framework/docker/*](../../../framework/docker/index.md)</span></span>

-   <span data-ttu-id="cb14f-145">**.NET 元件概觀**
    [*https://docs.microsoft.com/dotnet/standard/components*](../../components.md)</span><span class="sxs-lookup"><span data-stu-id="cb14f-145">**.NET Components Overview**
[*https://docs.microsoft.com/dotnet/standard/components*](../../components.md)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="cb14f-146">[上一頁](net-core-container-scenarios.md)
[下一頁](container-framework-choice-factors.md)</span><span class="sxs-lookup"><span data-stu-id="cb14f-146">[Previous](net-core-container-scenarios.md)
[Next](container-framework-choice-factors.md)</span></span>
