---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393910"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="ad6db-101">Spa：已標記為過時的 SpaServices 和 NodeServices</span><span class="sxs-lookup"><span data-stu-id="ad6db-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="ad6db-102">下列 NuGet 套件的內容在 ASP.NET Core 2.1 之後都是不必要的。</span><span class="sxs-lookup"><span data-stu-id="ad6db-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="ad6db-103">因此，下列套件會標示為已淘汰：</span><span class="sxs-lookup"><span data-stu-id="ad6db-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="ad6db-104">AspNetCore. SpaServices</span><span class="sxs-lookup"><span data-stu-id="ad6db-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="ad6db-105">AspNetCore. NodeServices</span><span class="sxs-lookup"><span data-stu-id="ad6db-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="ad6db-106">基於相同原因，下列 npm 模組會標示為已淘汰：</span><span class="sxs-lookup"><span data-stu-id="ad6db-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="ad6db-107">aspnet-角度</span><span class="sxs-lookup"><span data-stu-id="ad6db-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="ad6db-108">aspnet-預先呈現</span><span class="sxs-lookup"><span data-stu-id="ad6db-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="ad6db-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="ad6db-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="ad6db-110">aspnet-webpack-回應</span><span class="sxs-lookup"><span data-stu-id="ad6db-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="ad6db-111">網域-工作</span><span class="sxs-lookup"><span data-stu-id="ad6db-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="ad6db-112">先前的套件和 npm 模組稍後會在 .NET 5 中移除。</span><span class="sxs-lookup"><span data-stu-id="ad6db-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ad6db-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ad6db-113">Version introduced</span></span>

<span data-ttu-id="ad6db-114">3.0</span><span class="sxs-lookup"><span data-stu-id="ad6db-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ad6db-115">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ad6db-115">Old behavior</span></span>

<span data-ttu-id="ad6db-116">已淘汰的封裝和 npm 模組主要是用來整合 ASP.NET Core 與各種單頁應用程式（SPA）架構。</span><span class="sxs-lookup"><span data-stu-id="ad6db-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="ad6db-117">這類架構包含 Redux 的角度、反應和回應。</span><span class="sxs-lookup"><span data-stu-id="ad6db-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ad6db-118">新的行為</span><span class="sxs-lookup"><span data-stu-id="ad6db-118">New behavior</span></span>

<span data-ttu-id="ad6db-119">新的整合機制存在於[AspNetCore. SpaServices （擴充](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/)功能） NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="ad6db-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="ad6db-120">從 ASP.NET Core 2.1 開始，套件仍然是「角度」和「回應」專案範本的基礎。</span><span class="sxs-lookup"><span data-stu-id="ad6db-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ad6db-121">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ad6db-121">Reason for change</span></span>

<span data-ttu-id="ad6db-122">ASP.NET Core 支援與各種單頁應用程式（SPA）架構整合，包括 Redux 的角度、反應和回應。</span><span class="sxs-lookup"><span data-stu-id="ad6db-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="ad6db-123">一開始，與這些架構的整合是透過 ASP.NET Core 特定元件來完成，這些元件會處理案例，例如伺服器端預先呈現和與 Webpack 的整合。</span><span class="sxs-lookup"><span data-stu-id="ad6db-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="ad6db-124">隨著時間進展，產業標準也有所改變。</span><span class="sxs-lookup"><span data-stu-id="ad6db-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="ad6db-125">每個 SPA 架構都會發行自己的標準命令列介面。</span><span class="sxs-lookup"><span data-stu-id="ad6db-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="ad6db-126">例如，「角度」 CLI 和「建立-回應」應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad6db-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="ad6db-127">當 ASP.NET Core 2.1 于5月2018日發行時，小組會回應標準的變更。</span><span class="sxs-lookup"><span data-stu-id="ad6db-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="ad6db-128">提供較新且更簡單的方式來與 SPA 架構本身的工具鏈整合。</span><span class="sxs-lookup"><span data-stu-id="ad6db-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="ad6db-129">新的整合機制存在於套件中 `Microsoft.AspNetCore.SpaServices.Extensions`，而且從 ASP.NET Core 2.1 開始，仍然是「角度」和「回應」專案範本的基礎。</span><span class="sxs-lookup"><span data-stu-id="ad6db-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="ad6db-130">若要闡明舊版 ASP.NET Core 特定的元件是不相關的，而且不建議使用：</span><span class="sxs-lookup"><span data-stu-id="ad6db-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="ad6db-131">2\.1 前的整合機制會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="ad6db-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="ad6db-132">支援的 npm 封裝會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="ad6db-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ad6db-133">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ad6db-133">Recommended action</span></span>

<span data-ttu-id="ad6db-134">如果您要使用這些套件，請更新您的應用程式以使用功能：</span><span class="sxs-lookup"><span data-stu-id="ad6db-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="ad6db-135">在 `Microsoft.AspNetCore.SpaServices.Extensions` 封裝中。</span><span class="sxs-lookup"><span data-stu-id="ad6db-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="ad6db-136">由您所使用的 SPA 架構提供</span><span class="sxs-lookup"><span data-stu-id="ad6db-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="ad6db-137">若要啟用伺服器端預先呈現和經常性模組重載之類的功能，請參閱對應 SPA 架構的檔。</span><span class="sxs-lookup"><span data-stu-id="ad6db-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="ad6db-138">@No__t-0 中的功能*並未*淘汰，而且會繼續受到支援。</span><span class="sxs-lookup"><span data-stu-id="ad6db-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="ad6db-139">分類</span><span class="sxs-lookup"><span data-stu-id="ad6db-139">Category</span></span>

<span data-ttu-id="ad6db-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ad6db-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad6db-141">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ad6db-141">Affected APIs</span></span>

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
