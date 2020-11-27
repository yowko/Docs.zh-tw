---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032431"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="e8101-101">Spa： SpaServices 和 NodeServices 已標示為過時</span><span class="sxs-lookup"><span data-stu-id="e8101-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="e8101-102">從 ASP.NET Core 2.1 開始，下列 NuGet 套件的內容都是不必要的。</span><span class="sxs-lookup"><span data-stu-id="e8101-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="e8101-103">因此，下列封裝會標示為已淘汰：</span><span class="sxs-lookup"><span data-stu-id="e8101-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="e8101-104">AspNetCore. SpaServices</span><span class="sxs-lookup"><span data-stu-id="e8101-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="e8101-105">AspNetCore. NodeServices</span><span class="sxs-lookup"><span data-stu-id="e8101-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="e8101-106">基於相同的原因，下列 npm 模組會標示為已淘汰：</span><span class="sxs-lookup"><span data-stu-id="e8101-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="e8101-107">aspnet-角度</span><span class="sxs-lookup"><span data-stu-id="e8101-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="e8101-108">aspnet-預先呈現</span><span class="sxs-lookup"><span data-stu-id="e8101-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="e8101-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="e8101-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="e8101-110">aspnet-webpack-回應</span><span class="sxs-lookup"><span data-stu-id="e8101-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="e8101-111">網域-工作</span><span class="sxs-lookup"><span data-stu-id="e8101-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="e8101-112">上述封裝和 npm 模組稍後會在 .NET 5 中移除。</span><span class="sxs-lookup"><span data-stu-id="e8101-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e8101-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e8101-113">Version introduced</span></span>

<span data-ttu-id="e8101-114">3.0</span><span class="sxs-lookup"><span data-stu-id="e8101-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e8101-115">舊的行為</span><span class="sxs-lookup"><span data-stu-id="e8101-115">Old behavior</span></span>

<span data-ttu-id="e8101-116">已淘汰的封裝和 npm 模組旨在將 ASP.NET Core 與各種 Single-Page 應用程式 (SPA) 架構整合。</span><span class="sxs-lookup"><span data-stu-id="e8101-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="e8101-117">這類架構包含了 Redux 的角度、反應和反應。</span><span class="sxs-lookup"><span data-stu-id="e8101-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e8101-118">新的行為</span><span class="sxs-lookup"><span data-stu-id="e8101-118">New behavior</span></span>

<span data-ttu-id="e8101-119">新的整合機制存在於 [AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="e8101-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="e8101-120">從 ASP.NET Core 2.1 開始，此套件仍是角度和反應專案範本的基礎。</span><span class="sxs-lookup"><span data-stu-id="e8101-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e8101-121">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e8101-121">Reason for change</span></span>

<span data-ttu-id="e8101-122">ASP.NET Core 支援與各種 Single-Page 應用程式 (SPA) 架構的整合，包括 Redux 的角度、反應和反應。</span><span class="sxs-lookup"><span data-stu-id="e8101-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="e8101-123">一開始，與這些架構的整合是透過處理案例的 ASP.NET Core 特定元件來完成，例如伺服器端預先呈現和與 Webpack 的整合。</span><span class="sxs-lookup"><span data-stu-id="e8101-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="e8101-124">隨著時間的進展，產業標準也有所改變。</span><span class="sxs-lookup"><span data-stu-id="e8101-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="e8101-125">每個 SPA 架構都會發行自己的標準命令列介面。</span><span class="sxs-lookup"><span data-stu-id="e8101-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="e8101-126">例如，「角度」 CLI 和「建立-回應」應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8101-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="e8101-127">當 ASP.NET Core 2.1 在5月2018日發行時，小組會回應標準的變更。</span><span class="sxs-lookup"><span data-stu-id="e8101-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="e8101-128">提供更簡單且更簡單的方法來與 SPA 架構本身的工具鏈整合。</span><span class="sxs-lookup"><span data-stu-id="e8101-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="e8101-129">新的整合機制存在於封裝中 `Microsoft.AspNetCore.SpaServices.Extensions` ，並會在 ASP.NET Core 2.1 之後，保持角度和回應專案範本的基礎。</span><span class="sxs-lookup"><span data-stu-id="e8101-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="e8101-130">為了說明舊版 ASP.NET Core 特定的元件是不相關的，而且不建議使用：</span><span class="sxs-lookup"><span data-stu-id="e8101-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="e8101-131">2.1 之前的整合機制會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="e8101-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="e8101-132">支援的 npm 套件會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="e8101-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e8101-133">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e8101-133">Recommended action</span></span>

<span data-ttu-id="e8101-134">如果您要使用這些套件，請更新您的應用程式以使用此功能：</span><span class="sxs-lookup"><span data-stu-id="e8101-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="e8101-135">在 `Microsoft.AspNetCore.SpaServices.Extensions` 封裝中。</span><span class="sxs-lookup"><span data-stu-id="e8101-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="e8101-136">由您所使用的 SPA 架構提供</span><span class="sxs-lookup"><span data-stu-id="e8101-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="e8101-137">若要啟用伺服器端預先呈現和熱模組重載等功能，請參閱對應 SPA 架構的檔。</span><span class="sxs-lookup"><span data-stu-id="e8101-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="e8101-138">中的功能 `Microsoft.AspNetCore.SpaServices.Extensions` *尚未* 淘汰，而且會繼續受到支援。</span><span class="sxs-lookup"><span data-stu-id="e8101-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="e8101-139">類別</span><span class="sxs-lookup"><span data-stu-id="e8101-139">Category</span></span>

<span data-ttu-id="e8101-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e8101-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e8101-141">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e8101-141">Affected APIs</span></span>

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
