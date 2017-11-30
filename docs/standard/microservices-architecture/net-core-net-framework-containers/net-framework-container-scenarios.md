---
title: "選擇.NET Framework 的 Docker 容器的時機"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |選擇.NET Framework 的 Docker 容器的時機"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="28a58-104">選擇.NET Framework 的 Docker 容器的時機</span><span class="sxs-lookup"><span data-stu-id="28a58-104">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="28a58-105">.NET Core 提供重要的優點，新的應用程式和應用程式模式，而.NET Framework 仍將是不錯的選擇，許多現有的案例。</span><span class="sxs-lookup"><span data-stu-id="28a58-105">While .NET Core offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="28a58-106">將現有的應用程式移轉到 Windows Server 容器的直接</span><span class="sxs-lookup"><span data-stu-id="28a58-106">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="28a58-107">您可能想要使用 Docker 容器只是為了簡化部署，，即使您沒有建立 microservices。</span><span class="sxs-lookup"><span data-stu-id="28a58-107">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="28a58-108">例如，可能是您想要改善您的 DevOps 工作流程使用 Docker，容器可讓您更好的隔離的測試環境和也可免除部署移至生產環境時，遺失的相依性所造成的問題。</span><span class="sxs-lookup"><span data-stu-id="28a58-108">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="28a58-109">在這些情況下，即使您要部署整合的應用程式，它使用合理 Docker 與 Windows 容器目前的.NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="28a58-109">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="28a58-110">在大部分情況下，此案例中，您不需要移轉到.NET Core; 現有應用程式您可以使用包含傳統的.NET Framework 的 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="28a58-110">In most cases for this scenario, you will not need to migrate your existing applications to .NET Core; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="28a58-111">不過，建議的方法是使用.NET Core，當您擴充現有的應用程式，例如 ASP.NET Core 中撰寫新的服務。</span><span class="sxs-lookup"><span data-stu-id="28a58-111">However, a recommended approach is to use .NET Core as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a><span data-ttu-id="28a58-112">使用適用於.NET Core 的第三方.NET 程式庫或無法使用的 NuGet 封裝</span><span class="sxs-lookup"><span data-stu-id="28a58-112">Using third-party .NET libraries or NuGet packages not available for .NET Core</span></span>

<span data-ttu-id="28a58-113">協力廠商程式庫會快速採用[.NET 標準](https://docs.microsoft.com/dotnet/standard/net-standard)，可讓在所有的.NET 版本，包括.NET Core 之間共用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="28a58-113">Third-party libraries are quickly embracing the [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard), which enables code sharing across all .NET flavors, including .NET Core.</span></span> <span data-ttu-id="28a58-114">以.NET 標準程式庫 2.0 版或超過 API 介面跨不同架構的相容性變得更大，而.NET Core 2.0 應用程式也可以直接參考現有的.NET Framework 程式庫 (請參閱[相容填充碼](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work))。</span><span class="sxs-lookup"><span data-stu-id="28a58-114">With the .NET Standard Library 2.0 and beyond the API surface compatibility across different frameworks has become significantly larger and in .NET Core 2.0 applications can also directly reference existing .NET Framework libraries (see [compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).</span></span>

<span data-ttu-id="28a58-115">不過，即使是使用.NET 標準 2.0 和.NET 核心 2.0 自該例外狀況的進展，可能有某些 NuGet 封裝需要執行的 Windows，而且可能不支援.NET Core。</span><span class="sxs-lookup"><span data-stu-id="28a58-115">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.0, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core.</span></span> <span data-ttu-id="28a58-116">如果這些封裝您的應用程式的關鍵，您將需要使用.NET Framework 上 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="28a58-116">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="usingnet-technologies-not-available-for-net-core"></a><span data-ttu-id="28a58-117">沒有適用於.NET Core 的 Using.NET 技術</span><span class="sxs-lookup"><span data-stu-id="28a58-117">Using.NET technologies not available for .NET Core</span></span> 

<span data-ttu-id="28a58-118">某些.NET Framework 技術不適用於目前版本的.NET Core （2.0 版撰寫本文時）。</span><span class="sxs-lookup"><span data-stu-id="28a58-118">Some .NET Framework technologies are not available in the current version of .NET Core (version 2.0 as of this writing).</span></span> <span data-ttu-id="28a58-119">其中部分可在更新的.NET Core 版本 (.NET Core 2.x)，但其他人不會套用到新的應用程式模式.NET Core 的目標，而且可能永遠不會使用。</span><span class="sxs-lookup"><span data-stu-id="28a58-119">Some of them will be available in later .NET Core releases (.NET Core 2.x), but others do not apply to the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="28a58-120">下列清單顯示大部分的.NET Core 2.0 中未提供的技術：</span><span class="sxs-lookup"><span data-stu-id="28a58-120">The following list shows most of the technologies that are not available in .NET Core 2.0:</span></span>

-   <span data-ttu-id="28a58-121">ASP.NET Web Form。</span><span class="sxs-lookup"><span data-stu-id="28a58-121">ASP.NET Web Forms.</span></span> <span data-ttu-id="28a58-122">只有在.NET Framework 上使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="28a58-122">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="28a58-123">目前並未規劃將 ASP.NET Web Form 帶入 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="28a58-123">Currently there are no plans to bring ASP.NET Web Forms to .NET Core.</span></span>

-   <span data-ttu-id="28a58-124">WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="28a58-124">WCF services.</span></span> <span data-ttu-id="28a58-125">即使[WCF 用戶端程式庫](https://github.com/dotnet/wcf)皆可使用.NET core 的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="28a58-125">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET Core.</span></span> <span data-ttu-id="28a58-126">為準，mid 2017，WCF 伺服器實作才會使用.NET Framework 上。</span><span class="sxs-lookup"><span data-stu-id="28a58-126">as of mid-2017, the WCF server implementation is only available on .NET Framework.</span></span> <span data-ttu-id="28a58-127">這種情況下可能會視為未來版本的.NET Core。</span><span class="sxs-lookup"><span data-stu-id="28a58-127">This scenario might be considered for future releases of .NET Core.</span></span>

-   <span data-ttu-id="28a58-128">工作流程相關的服務。</span><span class="sxs-lookup"><span data-stu-id="28a58-128">Workflow-related services.</span></span> <span data-ttu-id="28a58-129">Windows Workflow Foundation (WF)、 工作流程服務 （WCF + 單一服務中的 WF） 和 WCF 資料服務 （先前稱為 ADO.NET Data Services），只能使用.NET Framework 為基礎。</span><span class="sxs-lookup"><span data-stu-id="28a58-129">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="28a58-130">目前沒有計劃以將它們帶到.NET Core。</span><span class="sxs-lookup"><span data-stu-id="28a58-130">There are currently no plans to bring them to .NET Core.</span></span>

<span data-ttu-id="28a58-131">除了技術之外列入正式[.NET Core 藍圖](https://github.com/aspnet/Home/wiki/Roadmap)，其他功能可能移植到.NET Core。</span><span class="sxs-lookup"><span data-stu-id="28a58-131">In addition to the technologies listed in the official [.NET Core roadmap](https://github.com/aspnet/Home/wiki/Roadmap), other features might be ported to .NET Core.</span></span> <span data-ttu-id="28a58-132">如需完整清單，查看 標記為的項目[連接埠-核心](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)CoreFX GitHub 網站上。</span><span class="sxs-lookup"><span data-stu-id="28a58-132">For a full list, look at the items tagged as [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) on the CoreFX GitHub site.</span></span> <span data-ttu-id="28a58-133">請注意，這份清單不代表 microsoft 承諾會將這些元件帶到.NET Core — 項目只會擷取來自社群的要求。</span><span class="sxs-lookup"><span data-stu-id="28a58-133">Note that this list does not represent a commitment from Microsoft to bring those components to .NET Core—the items simply capture requests from the community.</span></span> <span data-ttu-id="28a58-134">如果您在意任何上列的元件，請考慮參與 GitHub 上的討論，以便可以聽到語音。</span><span class="sxs-lookup"><span data-stu-id="28a58-134">If you care about any of the components listed above, consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="28a58-135">如果您認為缺少了什麼，請[在 CoreFX 儲存機制中提問新的問題](https://github.com/dotnet/corefx/issues/new)。</span><span class="sxs-lookup"><span data-stu-id="28a58-135">And if you think something is missing, please [file a new issue in the CoreFX repository](https://github.com/dotnet/corefx/issues/new).</span></span>

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a><span data-ttu-id="28a58-136">使用平台或應用程式開發介面中不支援.NET Core</span><span class="sxs-lookup"><span data-stu-id="28a58-136">Using a platform or API that does not support .NET Core</span></span>

<span data-ttu-id="28a58-137">某些 Microsoft 或第三方平台不支援.NET Core。</span><span class="sxs-lookup"><span data-stu-id="28a58-137">Some Microsoft or third-party platforms do not support .NET Core.</span></span> <span data-ttu-id="28a58-138">例如，部分 Azure 服務所提供的 SDK，尚無法使用.NET 核心上的耗用量。</span><span class="sxs-lookup"><span data-stu-id="28a58-138">For example, some Azure services provide an SDK that is not yet available for consumption on .NET Core.</span></span> <span data-ttu-id="28a58-139">這是暫時性的，因為所有 Azure 服務最終將會使用.NET 核心。</span><span class="sxs-lookup"><span data-stu-id="28a58-139">This is temporary, because all Azure services will eventually use .NET Core.</span></span> <span data-ttu-id="28a58-140">例如， [Azure DocumentDB SDK for.NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1)已於 2016 年 11 月 16 日預覽發行，但現在是上市 (GA) 做為穩定版本。</span><span class="sxs-lookup"><span data-stu-id="28a58-140">For example, the [Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) was released as a preview on November 16, 2016, but it is now generally available (GA) as a stable version.</span></span>

<span data-ttu-id="28a58-141">在此同時，如果任何平台或服務在 Azure 中的使用其用戶端應用程式開發介面不支援仍然.NET Core，您可以使用對等的 REST API 從 Azure 服務或用戶端 SDK.NET Framework 為基礎。</span><span class="sxs-lookup"><span data-stu-id="28a58-141">In the meantime, if any platform or service in Azure still doesn’t support .NET Core with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="28a58-142">其他資源</span><span class="sxs-lookup"><span data-stu-id="28a58-142">Additional resources</span></span>

-   <span data-ttu-id="28a58-143">**.NET core 指南**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)</span><span class="sxs-lookup"><span data-stu-id="28a58-143">**.NET Core Guide**
[*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)</span></span>

-   <span data-ttu-id="28a58-144">**從.NET Framework 移植到.NET Core**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)</span><span class="sxs-lookup"><span data-stu-id="28a58-144">**Porting from .NET Framework to .NET Core**
[*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)</span></span>

-   <span data-ttu-id="28a58-145">**.NET framework 上 Docker 指南**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)</span><span class="sxs-lookup"><span data-stu-id="28a58-145">**.NET Framework on Docker Guide**
[*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)</span></span>

-   <span data-ttu-id="28a58-146">**.NET 元件概觀**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)</span><span class="sxs-lookup"><span data-stu-id="28a58-146">**.NET Components Overview**
[*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="28a58-147">[上一個](net-核心-容器-scenarios.md) [下一步] (容器-架構-選擇-factors.md)</span><span class="sxs-lookup"><span data-stu-id="28a58-147">[Previous] (net-core-container-scenarios.md) [Next] (container-framework-choice-factors.md)</span></span>
