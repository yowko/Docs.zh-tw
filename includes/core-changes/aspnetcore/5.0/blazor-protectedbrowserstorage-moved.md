---
ms.openlocfilehash: a9545c66d3873b5114fe66e13c77ddc28e20020e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077601"
---
### <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="45e56-101">Blazor： ProtectedBrowserStorage 功能已移至共用架構</span><span class="sxs-lookup"><span data-stu-id="45e56-101">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="45e56-102">在 ASP.NET Core 5.0 RC2 版中，此功能已 `ProtectedBrowserStorage` 移至 ASP.NET Core 的共用架構。</span><span class="sxs-lookup"><span data-stu-id="45e56-102">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45e56-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="45e56-103">Version introduced</span></span>

<span data-ttu-id="45e56-104">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="45e56-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="45e56-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="45e56-105">Old behavior</span></span>

<span data-ttu-id="45e56-106">在 ASP.NET Core 5.0 Preview 8 中，此功能可作為 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) 套件的一部分，但是只能在 Blazor WebAssembly 中使用。</span><span class="sxs-lookup"><span data-stu-id="45e56-106">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="45e56-107">在 ASP.NET Core 5.0 RC1 中，此功能是 [AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) 的一部分，可參考 `Microsoft.AspNetCore.App` 共用架構。</span><span class="sxs-lookup"><span data-stu-id="45e56-107">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="45e56-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="45e56-108">New behavior</span></span>

<span data-ttu-id="45e56-109">在 ASP.NET Core 5.0 RC2 中，不再需要 NuGet 套件參考，也無法使用此功能。</span><span class="sxs-lookup"><span data-stu-id="45e56-109">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="45e56-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="45e56-110">Reason for change</span></span>

<span data-ttu-id="45e56-111">移至共用架構更適合客戶所預期的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="45e56-111">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45e56-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="45e56-112">Recommended action</span></span>

<span data-ttu-id="45e56-113">如果從 ASP.NET Core 5.0 RC1 升級，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="45e56-113">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="45e56-114">`Microsoft.AspNetCore.Components.ProtectedBrowserStorage`從專案移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="45e56-114">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="45e56-115">將 `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` 取代為 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。</span><span class="sxs-lookup"><span data-stu-id="45e56-115">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="45e56-116">從您的類別中移除對的呼叫 `AddProtectedBrowserStorage` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="45e56-116">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="45e56-117">如果從 ASP.NET Core 5.0 Preview 8 升級，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="45e56-117">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="45e56-118">`Microsoft.AspNetCore.Components.Web.Extensions`從專案移除套件參考。</span><span class="sxs-lookup"><span data-stu-id="45e56-118">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="45e56-119">將 `using Microsoft.AspNetCore.Components.Web.Extensions;` 取代為 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。</span><span class="sxs-lookup"><span data-stu-id="45e56-119">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="45e56-120">從您的類別中移除對的呼叫 `AddProtectedBrowserStorage` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="45e56-120">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

#### <a name="category"></a><span data-ttu-id="45e56-121">類別</span><span class="sxs-lookup"><span data-stu-id="45e56-121">Category</span></span>

<span data-ttu-id="45e56-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="45e56-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45e56-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="45e56-123">Affected APIs</span></span>

<span data-ttu-id="45e56-124">無</span><span class="sxs-lookup"><span data-stu-id="45e56-124">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
