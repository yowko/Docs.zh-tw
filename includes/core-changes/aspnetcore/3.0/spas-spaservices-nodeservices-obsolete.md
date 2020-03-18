---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393910"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="89380-101">Spa 服務：標記為過時的 Spa 服務和節點服務</span><span class="sxs-lookup"><span data-stu-id="89380-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="89380-102">自 ASP.NET Core 2.1 以來，以下 NuGet 包的內容都是不必要的。</span><span class="sxs-lookup"><span data-stu-id="89380-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="89380-103">因此，以下包被標記為過時：</span><span class="sxs-lookup"><span data-stu-id="89380-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="89380-104">微軟.AspNetCore.Spa服務</span><span class="sxs-lookup"><span data-stu-id="89380-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="89380-105">微軟.AspNetCore.節點服務</span><span class="sxs-lookup"><span data-stu-id="89380-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="89380-106">出於同樣的原因，以下 npm 模組被標記為棄用：</span><span class="sxs-lookup"><span data-stu-id="89380-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="89380-107">阿斯普內角</span><span class="sxs-lookup"><span data-stu-id="89380-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="89380-108">阿斯普內特預渲染</span><span class="sxs-lookup"><span data-stu-id="89380-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="89380-109">阿斯普內特網包</span><span class="sxs-lookup"><span data-stu-id="89380-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="89380-110">阿斯普內特-網路包-反應</span><span class="sxs-lookup"><span data-stu-id="89380-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="89380-111">域任務</span><span class="sxs-lookup"><span data-stu-id="89380-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="89380-112">前面的包和 npm 模組稍後將在 .NET 5 中刪除。</span><span class="sxs-lookup"><span data-stu-id="89380-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="89380-113">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="89380-113">Version introduced</span></span>

<span data-ttu-id="89380-114">3.0</span><span class="sxs-lookup"><span data-stu-id="89380-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="89380-115">舊的行為</span><span class="sxs-lookup"><span data-stu-id="89380-115">Old behavior</span></span>

<span data-ttu-id="89380-116">棄用的套裝軟體和 npm 模組旨在將 ASP.NET 核心與各種單頁應用 （SPA） 框架組成。</span><span class="sxs-lookup"><span data-stu-id="89380-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="89380-117">此類框架包括角、回應和與 Redux 的回應。</span><span class="sxs-lookup"><span data-stu-id="89380-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="89380-118">新的行為</span><span class="sxs-lookup"><span data-stu-id="89380-118">New behavior</span></span>

<span data-ttu-id="89380-119">[Microsoft.AspNetCore.SpaServices.擴展](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/)NuGet 包中存在一種新的集成機制。</span><span class="sxs-lookup"><span data-stu-id="89380-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="89380-120">該包仍然是自ASP.NET Core 2.1 以來的"角"和"反應"專案範本的基礎。</span><span class="sxs-lookup"><span data-stu-id="89380-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="89380-121">更改原因</span><span class="sxs-lookup"><span data-stu-id="89380-121">Reason for change</span></span>

<span data-ttu-id="89380-122">ASP.NET核心支援與各種單頁應用 （SPA） 框架組成，包括角、回應和與 Redux 的回應。</span><span class="sxs-lookup"><span data-stu-id="89380-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="89380-123">最初，與這些框架的集成是通過ASP.NET核心特定的元件完成的，這些元件處理了伺服器端預呈現和與 Webpack 集成等方案。</span><span class="sxs-lookup"><span data-stu-id="89380-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="89380-124">隨著時間的流逝，行業標準也發生了變化。</span><span class="sxs-lookup"><span data-stu-id="89380-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="89380-125">每個 SPA 框架都發佈了自己的標準命令列介面。</span><span class="sxs-lookup"><span data-stu-id="89380-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="89380-126">例如，角 CLI 和創建-回應應用。</span><span class="sxs-lookup"><span data-stu-id="89380-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="89380-127">當 ASP.NET Core 2.1 于 2018 年 5 月發佈時，團隊對標準的變化做出了回應。</span><span class="sxs-lookup"><span data-stu-id="89380-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="89380-128">提供了一種更新和更簡單的與 SPA 框架自己的工具鏈集成的方法。</span><span class="sxs-lookup"><span data-stu-id="89380-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="89380-129">新的集成機制存在於包`Microsoft.AspNetCore.SpaServices.Extensions`中，並且自ASP.NET Core 2.1 以來，它仍然是角和反應專案範本的基礎。</span><span class="sxs-lookup"><span data-stu-id="89380-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="89380-130">要澄清舊ASP.NET核心特定元件不相關，不建議：</span><span class="sxs-lookup"><span data-stu-id="89380-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="89380-131">2.1 前集成機制標記為過時。</span><span class="sxs-lookup"><span data-stu-id="89380-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="89380-132">支援的 npm 包被標記為已棄用。</span><span class="sxs-lookup"><span data-stu-id="89380-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="89380-133">建議的動作</span><span class="sxs-lookup"><span data-stu-id="89380-133">Recommended action</span></span>

<span data-ttu-id="89380-134">如果您正在使用這些包，請更新應用以使用以下功能：</span><span class="sxs-lookup"><span data-stu-id="89380-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="89380-135">在包`Microsoft.AspNetCore.SpaServices.Extensions`中。</span><span class="sxs-lookup"><span data-stu-id="89380-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="89380-136">由您使用的 SPA 框架提供</span><span class="sxs-lookup"><span data-stu-id="89380-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="89380-137">要啟用伺服器端預渲染和熱模組重新載入等功能，請參閱相應 SPA 框架的文檔。</span><span class="sxs-lookup"><span data-stu-id="89380-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="89380-138">中的`Microsoft.AspNetCore.SpaServices.Extensions`功能*未*過時，將繼續受支援。</span><span class="sxs-lookup"><span data-stu-id="89380-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="89380-139">類別</span><span class="sxs-lookup"><span data-stu-id="89380-139">Category</span></span>

<span data-ttu-id="89380-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89380-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="89380-141">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="89380-141">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
