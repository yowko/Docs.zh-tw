---
title: 針對 Docker 容器選擇 .NET Framework 的時機
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 Docker 容器選擇 .NET Framework 的時機
ms.date: 01/13/2021
ms.openlocfilehash: 476f891a70a220172f84d8168c8492416b8e56bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188111"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="f4a2f-103">針對 Docker 容器選擇 .NET Framework 的時機</span><span class="sxs-lookup"><span data-stu-id="f4a2f-103">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="f4a2f-104">雖然 .NET 5 為新的應用程式和應用程式模式提供顯著的優點，但 .NET Framework 仍是許多現有案例的理想選擇。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-104">While .NET 5 offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="f4a2f-105">將現有應用程式直接移轉至 Windows Server 容器</span><span class="sxs-lookup"><span data-stu-id="f4a2f-105">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="f4a2f-106">您可能只想要使用 Docker 容器來簡化部署，即使未建立微服務也是一樣。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-106">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="f4a2f-107">例如，您可能想要使用 Docker 來改善 DevOps 工作流程；容器可讓您更適當地隔離測試環境，也可以去除移至生產環境時遺失相依性所造成的部署問題。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-107">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="f4a2f-108">如果是這些情況，則即使您要部署整合型應用程式，還是可以將 Docker 和 Windows 容器合理地用於目前 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-108">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="f4a2f-109">在此案例的大部分情況下，您不需要將現有的應用程式遷移到 .NET 5。您可以使用包含傳統 .NET Framework 的 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-109">In most cases for this scenario, you will not need to migrate your existing applications to .NET 5; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="f4a2f-110">不過，建議的方法是在擴充現有的應用程式時使用 .NET 5，例如在 ASP.NET Core 中撰寫新的服務。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-110">However, a recommended approach is to use .NET 5 as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-5"></a><span data-ttu-id="f4a2f-111">使用 .NET 5 無法使用的協力廠商 .NET 程式庫或 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="f4a2f-111">Using third-party .NET libraries or NuGet packages not available for .NET 5</span></span>

<span data-ttu-id="f4a2f-112">協力廠商程式庫會快速採用 [.NET Standard](../../../standard/net-standard.md)，讓您能夠在所有 .net 類別（包括 .net 5）間共用程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-112">Third-party libraries are quickly embracing [.NET Standard](../../../standard/net-standard.md), which enables code sharing across all .NET flavors, including .NET 5.</span></span> <span data-ttu-id="f4a2f-113">使用 .NET Standard 2.0 和更新版本，跨不同架構的 API 介面相容性已變得更大。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-113">With .NET Standard 2.0 and later, the API surface compatibility across different frameworks has become significantly larger.</span></span> <span data-ttu-id="f4a2f-114">更多的是，.NET Core 2.x 和更新版本的應用程式也可以直接參考現有的 .NET Framework 程式庫 (請參閱 [.NET Framework 支援 .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)) 的4.6.1。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-114">Even more, .NET Core 2.x and newer applications can also directly reference existing .NET Framework libraries (see [.NET Framework 4.6.1 supporting .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).</span></span>

<span data-ttu-id="f4a2f-115">此外， [Windows 相容性套件](../../../core/porting/windows-compat-pack.md) 也會擴充 windows 上適用于 .NET Standard 2.0 的 API 介面。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-115">In addition, the [Windows Compatibility Pack](../../../core/porting/windows-compat-pack.md) extends the API surface available for .NET Standard 2.0 on Windows.</span></span> <span data-ttu-id="f4a2f-116">透過此套件，只需要些許修改甚至不需修改，大部分的現有程式碼即可重新編譯為 .NET Standard 2.x，以在 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-116">This pack allows recompiling most existing code to .NET Standard 2.x with little or no modification, to run on Windows.</span></span>

<span data-ttu-id="f4a2f-117">但是，即使在 .NET Standard 2.0 和 .NET Core 2.1 或更新版本之後，也會有特定的 NuGet 套件需要執行 Windows 而且可能不支援 .NET Core 或更新版本的情況。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-117">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.1 or later, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core or later.</span></span> <span data-ttu-id="f4a2f-118">如果這些套件對您的應用程式十分重要，則需要在 Windows 容器上使用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-118">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="using-net-technologies-not-available-for-net-5"></a><span data-ttu-id="f4a2f-119">使用 .net 5 無法使用的 .NET 技術</span><span class="sxs-lookup"><span data-stu-id="f4a2f-119">Using .NET technologies not available for .NET 5</span></span>

<span data-ttu-id="f4a2f-120">從這個撰寫) 的版本中，目前的 .NET (5.0 版無法使用部分 .NET Framework 技術。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-120">Some .NET Framework technologies aren't available in the current version of .NET (version 5.0 as of this writing).</span></span> <span data-ttu-id="f4a2f-121">其中有些可能會在較新版本中提供使用，但其他則不符合 .NET Core 目標的新應用程式模式，且可能永遠無法使用。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-121">Some of them might become available in later releases, but others don't fit the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="f4a2f-122">下列清單顯示 .NET 5 中無法使用的大部分技術：</span><span class="sxs-lookup"><span data-stu-id="f4a2f-122">The following list shows most of the technologies that aren't available in .NET 5:</span></span>

- <span data-ttu-id="f4a2f-123">ASP.NET Web Form。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-123">ASP.NET Web Forms.</span></span> <span data-ttu-id="f4a2f-124">只有在 .NET Framework 上才能使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-124">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="f4a2f-125">目前沒有任何計畫可將 ASP.NET Web Forms 帶入 .NET 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-125">Currently there are no plans to bring ASP.NET Web Forms to .NET  or later.</span></span>

- <span data-ttu-id="f4a2f-126">WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-126">WCF services.</span></span> <span data-ttu-id="f4a2f-127">即使有 [Wcf 用戶端程式庫](https://github.com/dotnet/wcf) 可從 .net 5 取用 wcf 服務，但從2021年1月開始，wcf 伺服器的執行只能在 .NET Framework 上使用。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-127">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET 5, as of Jan-2021, the WCF server implementation is only available on .NET Framework.</span></span>

- <span data-ttu-id="f4a2f-128">工作流程相關服務。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-128">Workflow-related services.</span></span> <span data-ttu-id="f4a2f-129">Windows Workflow Foundation (WF)、工作流程服務 (WCF + 單一服務中的 WF) 和 WCF Data Services (先前稱為 ADO.NET Data Services) 僅適用於 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-129">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="f4a2f-130">目前沒有任何計畫可將它們帶到 .NET 5。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-130">There are currently no plans to bring them to .NET 5.</span></span>

<span data-ttu-id="f4a2f-131">除了在官方 [.net 藍圖](https://github.com/dotnet/core/blob/master/roadmap.md)中列出的技術之外，其他功能也可能移植到新的 [統一 .net 平臺](https://devblogs.microsoft.com/dotnet/introducing-net-5/)。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-131">In addition to the technologies listed in the official [.NET roadmap](https://github.com/dotnet/core/blob/master/roadmap.md), other features might be ported to the new [unified .NET platform](https://devblogs.microsoft.com/dotnet/introducing-net-5/).</span></span> <span data-ttu-id="f4a2f-132">您可以考慮參與 GitHub 上的討論，以便聽取您的心聲。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-132">You might consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="f4a2f-133">如果您認為缺少了什麼，請在 [dotnet/runtime](https://github.com/dotnet/runtime/issues/new) GitHub 存放庫中提出新的問題。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-133">And if you think something is missing, file a new issue in the [dotnet/runtime](https://github.com/dotnet/runtime/issues/new) GitHub repository.</span></span>

## <a name="using-a-platform-or-api-that-doesnt-support-net-5"></a><span data-ttu-id="f4a2f-134">使用不支援 .NET 5 的平臺或 API</span><span class="sxs-lookup"><span data-stu-id="f4a2f-134">Using a platform or API that doesn't support .NET 5</span></span>

<span data-ttu-id="f4a2f-135">有些 Microsoft 和協力廠商平臺不支援 .NET 5。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-135">Some Microsoft and third-party platforms don't support .NET 5.</span></span> <span data-ttu-id="f4a2f-136">例如，有些 Azure 服務提供尚未在 .NET 5 上使用的 SDK。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-136">For example, some Azure services provide an SDK that isn't yet available for consumption on .NET 5.</span></span> <span data-ttu-id="f4a2f-137">大部分的 Azure SDK 最終應該會移植到 .NET 5/Standard，但有些可能並非各種原因。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-137">Most Azure SDK should eventually be ported to .NET 5/Standard but some might not for various reasons.</span></span> <span data-ttu-id="f4a2f-138">您可以在 [AZURE Sdk 最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html) 頁面中查看可用的 azure sdk。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-138">You can see the available Azure SDKs in the [Azure SDK Latest Releases](https://azure.github.io/azure-sdk/releases/latest/index.html) page.</span></span>

<span data-ttu-id="f4a2f-139">同時，如果 Azure 中的任何平臺或服務仍然不支援 .NET 5 及其用戶端 API，您可以在 .NET Framework 上使用 Azure 服務或用戶端 SDK 中的對等 REST API。</span><span class="sxs-lookup"><span data-stu-id="f4a2f-139">In the meantime, if any platform or service in Azure still doesn't support .NET 5 with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4a2f-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="f4a2f-140">Additional resources</span></span>

- <span data-ttu-id="f4a2f-141">**.NET 基礎** </span><span class="sxs-lookup"><span data-stu-id="f4a2f-141">**.NET fundamentals** </span></span>\
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- <span data-ttu-id="f4a2f-142">**將專案移植到 .NET 5** </span><span class="sxs-lookup"><span data-stu-id="f4a2f-142">**Porting Projects to .NET 5** </span></span>\
  [https://channel9.msdn.com/Events/dotnetConf/2020/Porting-Projects-to-NET-5](https://channel9.msdn.com/Events/dotnetConf/2020/Porting-Projects-to-NET-5)

- <span data-ttu-id="f4a2f-143">**Docker 上的 .NET 指南** </span><span class="sxs-lookup"><span data-stu-id="f4a2f-143">**.NET on Docker Guide** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- <span data-ttu-id="f4a2f-144">**.NET 元件總覽** </span><span class="sxs-lookup"><span data-stu-id="f4a2f-144">**.NET Components Overview** </span></span>\
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
><span data-ttu-id="f4a2f-145">[上一個](net-core-container-scenarios.md) 
>[下一步](container-framework-choice-factors.md)</span><span class="sxs-lookup"><span data-stu-id="f4a2f-145">[Previous](net-core-container-scenarios.md)
[Next](container-framework-choice-factors.md)</span></span>
